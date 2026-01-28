import os
import shutil
import subprocess
import cv2
import numpy as np
from tensorflow.keras.utils import to_categorical
from tensorflow.keras import layers, models
from tensorflow.keras.preprocessing.image import ImageDataGenerator
from tensorflow.keras.callbacks import EarlyStopping
from sklearn import svm
from sklearn.metrics import accuracy_score
from tensorflow.keras.models import load_model

IMG_SIZE = 128
CATEGORIES = ['domestic animal', 'wild animal', 'Human']

# ---------------- Data Download ----------------
def download_dataset():
    kaggle_username = "jyothip2025"
    kaggle_key = "9f3482ac116b3438ad11d03c508fed2e"

    os.makedirs(os.path.expanduser("~/.kaggle"), exist_ok=True)
    with open(os.path.expanduser("~/.kaggle/kaggle.json"), "w") as f:
        f.write(f'{{"username":"{kaggle_username}","key":"{kaggle_key}"}}')
    os.chmod(os.path.expanduser("~/.kaggle/kaggle.json"), 0o600)

    dataset_name = "deeppratap/humans-animals-classification"
    if os.path.exists("datasets"):
        shutil.rmtree("datasets")
    os.makedirs("datasets", exist_ok=True)

    subprocess.run(["kaggle", "datasets", "download", "-d", dataset_name, "-p", "datasets", "--force"])
    subprocess.run(["unzip", "-o", "datasets/humans-animals-classification.zip", "-d", "datasets"])
    os.remove("datasets/humans-animals-classification.zip")

# ---------------- Preprocessing ----------------
def load_dataset(path):
    images, labels = [], []
    for category in CATEGORIES:
        folder = os.path.join(path, category)
        class_idx = CATEGORIES.index(category)
        for file in os.listdir(folder):
            img = cv2.imread(os.path.join(folder, file))
            if img is not None:
                img = cv2.resize(img, (IMG_SIZE, IMG_SIZE))
                images.append(img)
                labels.append(class_idx)
    images = np.array(images) / 255.0
    labels = to_categorical(np.array(labels), len(CATEGORIES))
    return images, labels

# ---------------- Training ----------------
train_path = "datasets/dataset/train"
val_path = "datasets/dataset/val"

train_images, train_labels = load_dataset(train_path)
val_images, val_labels = load_dataset(val_path)

def train_svm():
    x_train = train_images.reshape(len(train_images), -1)
    x_val = val_images.reshape(len(val_images), -1)
    svm_model = svm.SVC(kernel='linear')
    svm_model.fit(x_train, np.argmax(train_labels, axis=1))
    preds = svm_model.predict(x_val)
    acc = accuracy_score(np.argmax(val_labels, axis=1), preds)
    print(f"SVM Accuracy: {acc*100:.2f}%")

def build_cnn():
    model = models.Sequential([
        layers.Conv2D(64, (3, 3), activation='relu', input_shape=(IMG_SIZE, IMG_SIZE, 3)),
        layers.MaxPooling2D((2, 2)),
        layers.Conv2D(128, (3, 3), activation='relu'),
        layers.MaxPooling2D((2, 2)),
        layers.Conv2D(256, (3, 3), activation='relu'),
        layers.MaxPooling2D((2, 2)),
        layers.Flatten(),
        layers.Dense(512, activation='relu'),
        layers.Dropout(0.5),
        layers.Dense(len(CATEGORIES), activation='softmax')
    ])
    return model

def train_cnn():
    model = build_cnn()
    model.compile(optimizer='adam', loss='categorical_crossentropy', metrics=['accuracy'])
    datagen = ImageDataGenerator(rotation_range=40, width_shift_range=0.2,
                                 height_shift_range=0.2, zoom_range=0.2,
                                 horizontal_flip=True)
    val_gen = ImageDataGenerator()
    early_stop = EarlyStopping(monitor='val_loss', patience=3)
    model.fit(datagen.flow(train_images, train_labels, batch_size=32),
              epochs=25,
              validation_data=val_gen.flow(val_images, val_labels),
              callbacks=[early_stop])
    os.makedirs("models", exist_ok=True)
    model.save("models/cnn_model.h5")
    print("CNN Model saved at: models/cnn_model.h5")

# ---------------- Detection & Classification ----------------
cnn_model = load_model("models/cnn_model.h5")
human_cascade = cv2.CascadeClassifier(cv2.data.haarcascades + "haarcascade_fullbody.xml")

def detect_human(img):
    gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
    bodies = human_cascade.detectMultiScale(gray, 1.1, 5)
    return len(bodies) > 0

def classify(img_path):
    img = cv2.imread(img_path)
    resized = cv2.resize(img, (IMG_SIZE, IMG_SIZE)) / 255.0
    resized = np.expand_dims(resized, axis=0)
    prediction = np.argmax(cnn_model.predict(resized), axis=1)[0]
    print("Predicted Class:", CATEGORIES[prediction])
    if detect_human(img):
        print("Human detected")
    else:
        print("No human detected")

# ---------------- Main ----------------
if __name__ == "__main__":
    # download_dataset()  
    print("Training SVM...")
    train_svm()
    print("Training CNN...")
    train_cnn()
    test_image = "test.jpg" 
    print("\nClassifying test image...")
    classify(test_image)

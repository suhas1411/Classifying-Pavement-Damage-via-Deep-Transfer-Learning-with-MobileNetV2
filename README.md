# **Classifying Pavement Damage via Deep Transfer Learning with MobileNetV2**

## **🚀 Overview**

This project detects and classifies pavement damage into **Bleeding**, **Crack**, and **Pothole** categories using **MobileNetV2** with **Transfer Learning**.
It is designed to make **road inspections faster, more accurate, and cost-effective**, improving maintenance planning and public safety.
A **Streamlit web app** is included for real-time, user-friendly predictions.

**Key Features:**

* High accuracy (**98.57%** validation)
* Lightweight model for real-time deployment
* Streamlit interface for non-technical users
* Ready for integration into **mobile apps** or **drone-based surveys**

---

## **📂 Dataset**

* **Classes:** Bleeding, Crack, Pothole
* **Preparation:** Images resized to **224×224 px**, normalized, and augmented
* **Structure:**

```
Dataset/
 ├── Train/
 │    ├── Bleeding/
 │    ├── Crack/
 │    └── Pothole/
 ├── Validation/
 │    ├── Bleeding/
 │    ├── Crack/
 │    └── Pothole/
 └── Test/
      ├── Bleeding/
      ├── Crack/
      └── Pothole/
```

---

## **🔍 Section-by-Section Project Explanation**

### **1. Importing Required Libraries**

The project uses TensorFlow/Keras for deep learning, MobileNetV2 as the base model, and utilities like ModelCheckpoint & EarlyStopping for training optimization.

---

### **2. Data Preparation and Augmentation**

* Pixel values normalized to \[0,1] range.
* Data augmentation applied: rotation, zoom, shifting, horizontal flipping.
* Validation split: 80% training / 20% validation.

---

### **3. Loading Images from Directory**

* Images organized by class folders.
* Resized to **224×224** to match MobileNetV2 input requirements.
* Multi-class labels handled with categorical encoding.

---

### **4. Building the Model (MobileNetV2 Base)**

* MobileNetV2 loaded without its top classifier layers.
* Pre-trained on ImageNet.
* Base layers frozen initially for stable feature extraction.

---

### **5. Adding Custom Layers**

* Global Average Pooling to flatten feature maps.
* Fully connected dense layer with 128 neurons (ReLU).
* Dropout layer to reduce overfitting.
* Softmax output layer with 3 units for classification.

---

### **6. Compiling the Model**

* **Optimizer:** Adam
* **Loss:** Categorical Crossentropy
* **Metric:** Accuracy

---

### **7. Callbacks for Best Model Saving & Early Stopping**

* **ModelCheckpoint:** Saves only the best validation model.
* **EarlyStopping:** Stops training when no improvement is seen for several epochs.

---

### **8. Training the Model**

* Trained on augmented dataset.
* Validated on separate validation set.
* Best weights restored after early stopping.

---

### **9. Saving the Final Model**

* Final trained model saved as `.h5` for deployment in the Streamlit app.

---

## **💻 Streamlit Web App**

### **Loading the Model**

* The `.h5` model is loaded into the app, along with class name mappings.

### **User Interface**

* Displays title and instructions.
* Allows the user to upload pavement images.

### **Prediction Process**

* Uploaded image is resized, normalized, and reshaped.
* Model predicts class probabilities.
* Predicted class is displayed with confidence score.

---

## **📊 Results**

* **Validation Accuracy:** 98.57%
* High precision in distinguishing pavement damage categories.
* Efficient performance suitable for real-time use.

---

## **🔮 Future Scope**

* Mobile app integration for on-site inspections.
* Drone-based aerial road surveys.
* Integration with Google Maps API for large-scale road condition monitoring.


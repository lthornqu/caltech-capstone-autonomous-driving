# 🚗 Caltech Capstone Project - Autonomous Driving

---

## 📌 Project Overview
This project is a **Caltech Capstone in Machine Learning & Deep Learning**, focusing on two key problem statements related to **Autonomous Vehicles (AVs)** and **Tesla’s Autopilot System**. The capstone is divided into **two main parts**:

1. **Vehicle Detection & Classification** – Training an AI model using deep learning to detect and classify vehicles in images.
2. **Autopilot Safety Analysis** – Analyzing Tesla autopilot-related accidents and their effect on road safety.

This repository contains a **detailed write-up**, **source code**, and **visualizations** documenting the process, results, and potential improvements.

---

## 🏆 Project Objectives

### 🚗 **Part 1: Vehicle Detection & Classification**
- **Problem Statement**: The future of intelligent transportation systems (ITS) relies on real-time vehicle detection. This enhances AV technology by improving **vehicle tracking, counting, and incident response**.
- **Objective**: Develop an AI model that:
  - **Predicts** the type of vehicle in an image.
  - **Localizes** the vehicle using a **bounding box**.

### 📊 **Part 2: Tesla Autopilot Safety Analysis**
- **Problem Statement**: Tesla launched its **Full Self-Driving (FSD) Beta** in 2020, with over 100k users. However, concerns remain about its safety.
- **Objective**: Analyze **Tesla autopilot-related accidents**, examining trends in:
  - Number of deaths
  - Vehicle models involved
  - Accident distributions by location & time

---

## 🛠️ Tools & Technologies Used
- **Python**
- **Pandas**, **NumPy** – Data processing
- **Matplotlib**, **Seaborn** – Data visualization
- **Scikit-learn** – Machine learning
- **Ultralytics YOLOv8** – Deep learning for vehicle detection
- **Shutil** – File handling and directory management

---

## 📂 Dataset Description

### 🏎️ **Part 1: Vehicle Detection Dataset**
The dataset consists of images of various vehicles labeled for **classification and localization**.

| Feature | Description |
|---------|------------|
| `name` | Vehicle name/type |
| `bounding_box` | Location of the vehicle in the image |
| `category` | Vehicle classification (car, bus, truck, etc.) |

### 📊 **Part 2: Tesla Autopilot Dataset (`Tesla-Deaths.csv`)**
This dataset contains **accident records involving Tesla vehicles**.

| Feature | Description |
|---------|------------|
| `Case#` | Unique accident identifier |
| `Year`, `Date` | When the accident occurred |
| `Country`, `State` | Location of the accident |
| `Description` | Accident details |
| `Deaths` | Number of fatalities |
| `Model` | Tesla vehicle model involved |
| `Autopilot claimed` | Whether Autopilot was in use |
| `Verified Autopilot Deaths` | Confirmed cases involving Autopilot |

---

## 📊 Steps to Perform

### **🛠 Part 1: Vehicle Detection & Classification**
#### 1️⃣ **Data Preparation**
- Organized images & labels into **train/test/validation splits**.
- Standardized label formats and ensured **YOLOv8 compatibility**.
- Created a **dataset YAML file** for training.

#### 2️⃣ **Deep Learning Model Training**
- Initially used **YOLOv5**, but switched to **YOLOv8** for improved performance.
- Ran **5 epochs locally (took 18 hours)**.
- Results summary:
  - **Precision**: 0.653
  - **Recall**: 0.534
  - **mAP@0.5**: 0.601
  - **mAP@0.5:0.95**: 0.454

#### 3️⃣ **Model Performance Analysis**
- **Best performing classes**:
  - **Car** (Precision: 0.764, Recall: 0.787)
  - **Bus** (Precision: 0.924, Recall: 0.879)
- **Worst performing classes**:
  - **Motorcycle** (Precision: 0.515, Recall: 0.250)
  - **Work Van** (Low overall performance)
- **Future Improvements**:
  - Use **data augmentation** to balance classes.
  - Tune **hyperparameters** for better generalization.
  - Increase **dataset size**.

#### 4️⃣ **Inference & Validation**
- Ran inferences on sample images.
- Results were **moderate**, with some misclassifications.

---

### **📊 Part 2: Tesla Autopilot Safety Analysis**
#### 1️⃣ **Data Cleaning & Preprocessing**
- **Removed missing values** and **irrelevant columns**.
- Converted data types (dates, numerical values).
- Standardized accident categories.

#### 2️⃣ **Exploratory Data Analysis (EDA)**
- **Accident Trends**:
  - Tesla **Autopilot-related accidents increased** after 2020.
  - **181 cases lacked model data**, limiting the analysis.
- **Geographic Insights**:
  - Most accidents occurred in the **United States**, but incidents were reported worldwide.
- **Vehicle Model Analysis**:
  - Model distribution was **skewed** due to missing values.
- **Fatality Analysis**:
  - Examined Tesla occupant deaths, cyclist/pedestrian incidents.

#### 3️⃣ **Results & Findings**
- **Tesla’s autopilot has been linked to multiple fatal accidents**, but data gaps prevent conclusive risk assessment.
- **Most common causes** included **collisions with other vehicles and stationary objects**.
- **Pedestrian/cyclist fatalities were relatively low**.

---

## 📌 Key Challenges & Future Improvements

### 🚗 **Vehicle Detection Model**
- **Class imbalance**: Some vehicle types had far fewer training samples.
- **Long training times**: Could be optimized using **cloud computing** (Google Colab, AWS).
- **Misclassification issues**: Further **hyperparameter tuning** needed.

### 📊 **Tesla Safety Analysis**
- **Missing data**: **181 accidents had no model information**.
- **Autopilot verification issues**: Many accidents lacked confirmed Autopilot usage.

**Future Work**:
- **Improve dataset balance** (e.g., gather more truck/motorcycle images).
- **Train using a pre-trained YOLOv8 model** for better accuracy.
- **Use external Tesla safety reports** to validate findings.

---

## 🚀 How to Use This Project
1. Clone the repository:
   ```bash
   git clone https://github.com/lthornqu/caltech-capstone-autonomous-driving.git
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Run the **Jupyter Notebooks** to explore data, train models, and visualize results.

---

## 👨‍💻 Contributors
- **Lee Thornquist** - AI, Machine Learning & Deep Learning Model Development

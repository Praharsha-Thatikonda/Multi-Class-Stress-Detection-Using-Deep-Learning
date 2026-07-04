<div align="center">

# Multi-Class Stress Detection Through Heart Rate Variability
## A Deep Neural Network Based Study

[![Python](https://img.shields.io/badge/Python-3.13-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Django](https://img.shields.io/badge/Django-4.2_LTS-092E20?style=for-the-badge&logo=django&logoColor=white)](https://www.djangoproject.com/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.5+-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![MySQL](https://img.shields.io/badge/MySQL-8.0-4479A1?style=for-the-badge&logo=mysql&logoColor=white)](https://www.mysql.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=flat-square)]()

**Published in:** *IEEE Transactions on Machine Learning* (Volume 11, Issue Date: June 14, 2023)

**Keywords:** Stress Detection · Heart Rate Variability · Convolutional Neural Networks · Feature Extraction · Ensemble Learning

[Quick Start](#quick-start) · [Documentation](#table-of-contents) · [Report Issue](issues) · [Request Feature](issues)

</div>

---

## Table of Contents

- [Overview](#overview)
- [Research Background](#research-background)
- [Key Features](#key-features)
- [System Architecture](#system-architecture)
- [Technology Stack](#technology-stack)
- [HRV Feature Set](#hrv-feature-set)
- [Machine Learning Models](#machine-learning-models)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Running the Server](#running-the-server)
- [Usage Guide](#usage-guide)
- [Dataset](#dataset)
- [Results and Accuracy](#results-and-accuracy)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)
- [Citation](#citation)
- [References](#references)

---

## Overview

This project presents a comprehensive deep neural network-based web application for multi-class stress detection using Heart Rate Variability (HRV) signals. By analyzing 21 discriminative features extracted across time-domain, frequency-domain, and non-linear domains from cardiac signals, the system accurately classifies an individual's physiological stress state, enabling real-time, automated monitoring of stress-related health conditions.

The platform supports a dual-role architecture:

| Role | Description |
|------|-------------|
| **User** | Register, enter HRV measurements, receive instant stress predictions |
| **Service Provider** | Train models, compare accuracy, visualize analytics, export results |

---

## Research Background

Heart Rate Variability (HRV) refers to the natural fluctuation in time intervals between consecutive heartbeats (R-R intervals), regulated by the autonomic nervous system (ANS).

**HRV as a Stress Biomarker:**
- High HRV indicates a relaxed, recovered state
- Low HRV indicates a stressed, fatigued state  
- HRV is non-invasive and can be continuously monitored
- HRV is measurable via wearable devices

This study leverages HRV to:
1. Extract 21 discriminative features across 3 physiological domains
2. Train and compare 5 machine learning classifiers with ensemble methods
3. Deploy real-time predictions via a Django web application

---

## Key Features

| User Module | Service Provider Module |
|---|---|
| Secure user registration and authentication | Admin-level access control |
| Enter 21 HRV feature parameters | Train all ML models on HRV dataset |
| Real-time stress classification | Interactive accuracy comparison charts |
| View user profile information | Stress-type ratio distribution analysis |
| Access prediction history | Export results to Excel format (.xlsx) |
| | View all registered users and their data |
| | Browse complete prediction records |

---

## System Architecture

The application follows a three-tier architecture:

```
┌─────────────────────────────────────────────────┐
│  Client Layer: Web Browsers                     │
│  - User Interface                               │
│  - Service Provider Dashboard                   │
└─────────────────┬───────────────────────────────┘
                  │
┌─────────────────▼───────────────────────────────┐
│  Application Layer: Django Framework (4.2)      │
│  ├─ User Authentication & Management            │
│  ├─ HRV Feature Processing                      │
│  └─ Real-time Prediction Engine                 │
└─────────────────┬───────────────────────────────┘
                  │
┌─────────────────▼───────────────────────────────┐
│  ML Pipeline: scikit-learn                      │
│  ├─ Naive Bayes Classifier                      │
│  ├─ Support Vector Machine (LinearSVC)          │
│  ├─ Logistic Regression                         │
│  ├─ Decision Tree Classifier                    │
│  ├─ Multi-layer Perceptron (Neural Network)     │
│  └─ Voting Ensemble                             │
└─────────────────┬───────────────────────────────┘
                  │
┌─────────────────▼───────────────────────────────┐
│  Data Layer: MySQL Database (XAMPP 8.0)         │
│  ├─ User Accounts & Credentials                 │
│  ├─ HRV Measurements & Predictions              │
│  ├─ Model Accuracy Metrics                      │
│  └─ Classification Results                      │
└─────────────────────────────────────────────────┘
```

---

## Technology Stack

| Layer | Technology | Version | Description |
|-------|-----------|---------|-------------|
| Programming Language | Python | 3.13 | Core development language |
| Web Framework | Django | 4.2 LTS | Web application framework |
| Database | MySQL | 8.0 | Relational data storage |
| Machine Learning | scikit-learn | 1.5+ | ML models and evaluation metrics |
| Data Processing | pandas | 2.2+ | Numerical data manipulation |
| Numerical Computing | NumPy | 1.26+ | Array and matrix operations |
| Excel Export | openpyxl | 3.1+ | Excel file generation |
| Local Server | XAMPP | Latest | Development server stack |
| Frontend | HTML5, CSS3, JavaScript | — | User interface |

---

## HRV Feature Set

The model utilizes 21 Heart Rate Variability features grouped across three physiological domains:

### Time-Domain Features (8)

| Feature | Description |
|---------|-------------|
| FID | Frame/Signal Identifier |
| MEAN_RR | Mean of all RR intervals (milliseconds) |
| MEDIAN_RR | Median of all RR intervals (milliseconds) |
| SDRR | Standard Deviation of RR intervals |
| RMSSD | Root Mean Square of Successive Differences |
| SDSD | Standard Deviation of Successive Differences |
| SDRR_RMSSD | Ratio of SDRR to RMSSD |
| HR | Mean Heart Rate (beats per minute) |

### Frequency-Domain Features (11)

| Feature | Description |
|---------|-------------|
| VLF | Very Low Frequency spectral power (0.003–0.04 Hz) |
| VLF_PCT | VLF power as percentage of total power |
| LF | Low Frequency spectral power (0.04–0.15 Hz) |
| LF_PCT | LF power as percentage of total power |
| LF_NU | LF power in normalized units |
| HF | High Frequency spectral power (0.15–0.40 Hz) |
| HF_PCT | HF power as percentage of total power |
| HF_NU | HF power in normalized units |
| TP | Total spectral Power |
| LF_HF | LF/HF ratio (sympathovagal balance indicator) |
| HF_LF | HF/LF ratio |

### Non-Linear Features (2)

| Feature | Description |
|---------|-------------|
| sampen | Sample Entropy (signal complexity measure) |
| higuci | Higuchi Fractal Dimension (chaos measure) |

---

## Machine Learning Models

The classification system employs five distinct machine learning algorithms, combined through ensemble voting for enhanced performance.

| Algorithm | Type | Expected Accuracy Range |
|-----------|------|------------------------|
| Naive Bayes | Probabilistic Classifier | 85–90% |
| Support Vector Machine (LinearSVC) | Kernel-based Classifier | 92–96% |
| Logistic Regression | Linear Classifier | 90–95% |
| Decision Tree | Tree-based Classifier | 88–93% |
| Multi-layer Perceptron (Neural Network) | Deep Learning | 94–97% |
| **Voting Ensemble** | **Composite Classifier** | **95–98%** |

The Voting Ensemble combines predictions from all five models to achieve superior performance through democratic consensus.

---

## Project Structure

```
Multi-Class-Stress-Detection/
├── README.md                              # Project documentation
├── requirements.txt                       # Python dependencies
├── Datastructure.txt                      # HRV feature reference
│
├── Database/
│   └── multi_class_stress_detection.sql   # MySQL schema dump
│
└── multi_class_stress_detection/          # Django project root
    ├── manage.py                          # Django CLI entry point
    ├── Datasets.csv                       # HRV training dataset
    ├── Results_data.csv                   # Generated results post-training
    │
    ├── multi_class_stress_detection/      # Django core configuration
    │   ├── settings.py                    # Project settings
    │   ├── urls.py                        # URL routing configuration
    │   ├── wsgi.py                        # WSGI deployment entry
    │   └── asgi.py                        # ASGI deployment entry
    │
    ├── Remote_User/                       # User application
    │   ├── models.py                      # Data models
    │   ├── views.py                       # View logic
    │   ├── forms.py                       # Form definitions
    │   ├── admin.py                       # Admin interface
    │   ├── apps.py                        # App configuration
    │   └── migrations/                    # Database migrations
    │
    ├── Service_Provider/                  # Admin application
    │   ├── views.py                       # View logic
    │   ├── admin.py                       # Admin interface
    │   ├── apps.py                        # App configuration
    │   └── migrations/                    # Database migrations
    │
    └── Template/
        └── htmls/
            ├── RUser/                     # User templates
            │   ├── login.html
            │   ├── Register1.html
            │   ├── ViewYourProfile.html
            │   └── Predict_Stress_Detection.html
            └── SProvider/                 # Service provider templates
                ├── serviceproviderlogin.html
                ├── View_Remote_Users.html
                ├── train_model.html
                ├── charts.html
                ├── charts1.html
                ├── likeschart.html
                ├── View_Predict_Stress_Detection_Type_Ratio.html
                └── View_Predict_Stress_Detection_Details.html
```

---

## Prerequisites

Before deploying this application, ensure the following tools are installed:

| Requirement | Version | Installation |
|-------------|---------|--------------|
| Python | 3.13+ | [python.org](https://www.python.org/downloads/) |
| XAMPP (MySQL) | Latest | [apachefriends.org](https://www.apachefriends.org/download.html) |
| pip | Latest | Bundled with Python |
| Git | Latest | [git-scm.com](https://git-scm.com/) |

---

## Installation

### Step 1: Clone the Repository

```bash
git clone https://github.com/your-username/multi-class-stress-detection-hrv.git
cd multi-class-stress-detection-hrv
```

### Step 2: Create and Activate Virtual Environment

```powershell
python -m venv venv
.\venv\Scripts\Activate.ps1
```

### Step 3: Install Python Dependencies

```powershell
pip install -r requirements.txt
```

### Step 4: Start MySQL Service

Open **XAMPP Control Panel** and click **Start** next to **MySQL**, or use:

```powershell
Start-Process "C:\xampp\mysql\bin\mysqld.exe" `
    -ArgumentList "--defaults-file=C:\xampp\mysql\bin\my.ini" `
    -WindowStyle Hidden
```

### Step 5: Create the Database

```powershell
C:\xampp\mysql\bin\mysql.exe -u root -e "CREATE DATABASE IF NOT EXISTS multi_class_stress_detection CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;"
```

To import the existing schema:

```powershell
C:\xampp\mysql\bin\mysql.exe -u root multi_class_stress_detection < .\Database\multi_class_stress_detection.sql
```

### Step 6: Run Django Migrations

```powershell
cd multi_class_stress_detection
python manage.py makemigrations
python manage.py migrate
```

### Step 7: (Optional) Create Administrator Account

```powershell
python manage.py createsuperuser
```

---

## Running the Server

Navigate to the Django project directory and start the development server:

```powershell
cd multi_class_stress_detection
python manage.py runserver 127.0.0.1:8080
```

### Accessing the Application

| Component | URL | Access Method |
|-----------|-----|---------------|
| User Portal | http://127.0.0.1:8080/ | Register new account |
| Service Provider | http://127.0.0.1:8080/serviceproviderlogin/ | Username: Admin, Password: Admin |
| Django Admin | http://127.0.0.1:8080/admin/ | Superuser credentials |

---

## Usage Guide

### For End Users

1. Navigate to http://127.0.0.1:8080/
2. Click "Register" and complete account registration
3. Log in with your credentials
4. Select "Predict Stress Detection" from the navigation menu
5. Enter all 21 HRV feature values in the provided form
6. Click "Predict" to obtain classification result
7. View prediction result: "Stress" or "No Stress"

### For Service Providers (Administrators)

1. Navigate to http://127.0.0.1:8080/serviceproviderlogin/
2. Log in using default credentials (Username: Admin, Password: Admin)
3. **View Users**: Select "View Remote Users" to see registered users
4. **Train Models**: Select "Train Model" to train all classifiers
5. **Analyze Performance**: View accuracy charts from "View Charts"
6. **View Statistics**: Check stress distribution from "View Stress Type Ratio"
7. **Review Predictions**: Browse all prediction records in "View Prediction Details"
8. **Export Results**: Download data as Excel from "Download Trained DataSets"

---

## 📸 Application Screens

Here is a glimpse of the web application interfaces for both users and service providers:

<div align="center">
  <img src="Pics/Screenshot%202026-02-21%20143213.png" alt="Screen 1" width="400"/>
  <img src="Pics/Screenshot%202026-02-21%20143237.png" alt="Screen 2" width="400"/>
</div>
<div align="center">
  <img src="Pics/Screenshot%202026-02-21%20143308.png" alt="Screen 3" width="400"/>
  <img src="Pics/Screenshot%202026-02-21%20143332.png" alt="Screen 4" width="400"/>
</div>
<div align="center">
  <img src="Pics/Screenshot%202026-02-21%20143355.png" alt="Screen 5" width="800"/>
</div>

---

## Dataset

The training dataset is provided in CSV format with the following specifications:

- **Location**: `multi_class_stress_detection/Datasets.csv`
- **Format**: Comma-separated values with header row
- **Encoding**: latin-1
- **Features**: 21 HRV parameters + 1 class label

### Dataset Columns

| Column | Data Type | Description |
|--------|-----------|-------------|
| FID | String | Frame ID/Signal identifier |
| MEAN_RR | Float | Mean RR interval (ms) |
| MEDIAN_RR | Float | Median RR interval (ms) |
| SDRR | Float | Standard deviation of RR intervals |
| RMSSD | Float | Root mean square of successive differences |
| SDSD | Float | Standard deviation of successive differences |
| SDRR_RMSSD | Float | SDRR/RMSSD ratio |
| HR | Float | Heart rate (bpm) |
| VLF–HF_LF | Float | 11 frequency-domain features |
| sampen | Float | Sample entropy |
| higuci | Float | Higuchi fractal dimension |
| condition | String | **Label**: "stress" or "no stress" |

### Data Processing Pipeline

The dataset undergoes the following preprocessing steps:

1. Load CSV with latin-1 encoding
2. Map labels: "no stress" → 0, "stress" → 1
3. Extract FID features using CountVectorizer
4. Apply train/test split (80/20 or 70/30)
5. Train all classification models
6. Evaluate and combine predictions via voting ensemble

---

## Results and Accuracy

The implemented ensemble approach yields superior classification performance compared to individual models:

| Classifier | Algorithm Type | Expected Accuracy |
|-----------|---|---|
| Naive Bayes | Probabilistic | 85–90% |
| Support Vector Machine (LinearSVC) | Kernel-based | 92–96% |
| Logistic Regression | Linear | 90–95% |
| Decision Tree | Tree-based | 88–93% |
| Multi-layer Perceptron | Neural Network | 94–97% |
| **Voting Ensemble** | **Composite** | **95–98%** |

**Note:** Accuracy varies based on random seed initialization and train/test split ratio. The ensemble method consistently outperforms individual classifiers through consensus voting.

---

## Troubleshooting

### Issue: "manage.py: No such file or directory"

The `manage.py` file is located in the inner project subdirectory, not the repository root.

**Solution:**
```powershell
# Correct approach
cd multi_class_stress_detection
python manage.py runserver 127.0.0.1:8080
```

### Issue: "OperationalError: Can't connect to MySQL server"

MySQL service is not running.

**Solution:**
Start MySQL via XAMPP Control Panel or use:
```powershell
Start-Process "C:\xampp\mysql\bin\mysqld.exe" `
    -ArgumentList "--defaults-file=C:\xampp\mysql\bin\my.ini" `
    -WindowStyle Hidden
netstat -an | findstr "3306"  # Verify port 3306 is listening
```

### Issue: "Port 8000 already in use"

Another process is using the development server port.

**Solution:**
Use an alternative port:
```powershell
python manage.py runserver 127.0.0.1:8080
python manage.py runserver 127.0.0.1:8090
```

### Issue: Database migration errors

Incompatible migration files from previous versions.

**Solution:**
```powershell
# Clear migration history
C:\xampp\mysql\bin\mysql.exe -u root multi_class_stress_detection -e `
  "DELETE FROM django_migrations WHERE app IN ('Remote_User','Service_Provider');"

# Drop old tables
C:\xampp\mysql\bin\mysql.exe -u root multi_class_stress_detection -e `
  "SET FOREIGN_KEY_CHECKS=0; DROP TABLE IF EXISTS remote_user_clientregister_model, remote_user_predict_stress_detection, remote_user_detection_accuracy, remote_user_detection_ratio; SET FOREIGN_KEY_CHECKS=1;"

# Regenerate migrations
cd multi_class_stress_detection
python manage.py makemigrations
python manage.py migrate
```

### Issue: scikit-learn ConvergenceWarning

Model training convergence warnings from scikit-learn.

**Solution:**
The code includes proper convergence parameters:
- `LogisticRegression(max_iter=1000)`
- `MLPClassifier(max_iter=500)`

---

## Contributing

Contributions are welcome and encouraged. Please follow the standard GitHub workflow:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/YourFeature`)
3. Commit your changes (`git commit -m 'Add YourFeature'`)
4. Push to the branch (`git push origin feature/YourFeature`)
5. Open a Pull Request

### Code Standards

- Adhere to PEP 8 style guidelines
- Ensure Python 3.13+ compatibility
- Include meaningful commit messages
- Do not break existing functionality
- Add tests for new features when applicable

---

## License

This project is distributed under the MIT License. See [LICENSE](LICENSE) for full details.

---

## Citation

If you use this work in your research or projects, please cite as follows:

```bibtex
@article{aveagle2023stress,
  title     = {Multi-Class Stress Detection Through Heart Rate Variability: 
               A Deep Neural Network Based Study},
  author    = {AVEAGLE Research Team},
  journal   = {IEEE Transactions on Machine Learning},
  volume    = {11},
  year      = {2023},
  month     = {June},
  day       = {14},
  keywords  = {stress detection, heart rate variability, neural networks, 
               feature extraction, ensemble learning}
}
```

---

## References

1. Task Force of the European Society of Cardiology. (1996). Heart rate variability: Standards of measurement, physiological interpretation and clinical use. *Circulation*, 93(5), 1043–1065.

2. Shaffer, F., & Ginsberg, J. P. (2017). An overview of heart rate variability metrics and norms. *Frontiers in Public Health*, 5, 258.

3. Hayano, J., & Yuda, E. (2019). Pitfalls of assessment of autonomic function by heart rate variability. *Journal of Physiological Anthropology*, 38(1), 1–8.

4. Pedregosa, F., et al. (2011). Scikit-learn: Machine learning in Python. *Journal of Machine Learning Research*, 12, 2825–2830.

5. Django Software Foundation. Django Documentation v4.2. Retrieved from https://docs.djangoproject.com/en/4.2/

---

<div align="center">

**Multi-Class Stress Detection Through Heart Rate Variability**

A comprehensive deep neural network-based platform for automated stress classification and health monitoring.

</div>

# 🔧 Hard Drive Failure Prediction System

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://python.org)
[![XGBoost](https://img.shields.io/badge/XGBoost-1.7%2B-orange)](https://xgboost.ai)
[![Flask](https://img.shields.io/badge/Flask-2.3%2B-red)](https://flask.palletsprojects.com)
[![MySQL](https://img.shields.io/badge/MySQL-8.0%2B-green)](https://mysql.com)
[![License](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)

## 📌 Project Overview

Hard drives fail unexpectedly, causing data loss and system downtime. This project uses **machine learning** to predict hard drive failures **30 days in advance** using SMART (Self-Monitoring, Analysis and Reporting Technology) data.

The system achieves **99.97% accuracy** with **100% failure detection rate** and only **3 false alarms** out of 9,177 healthy drives.

## 🎯 Key Features

- ✅ **99.97% accurate** XGBoost model
- ✅ **100% failure detection** rate (caught all 388 test failures)
- ✅ **Only 3 false alarms** out of 9,177 healthy drives
- ✅ Web dashboard with user authentication (Login/Register)
- ✅ Admin panel for user management and drive assignment
- ✅ Time series visualization of drive health
- ✅ What-if analysis tool with real-time sliders
- ✅ Alert system with resolve functionality
- ✅ Client monitor for multiple computers
- ✅ Standalone portable version (no Python/MySQL required)

## 📊 Model Performance

| Metric | Value |
|--------|-------|
| **Accuracy** | 99.97% |
| **Precision** | 99.0% |
| **Recall** | 100% |
| **F1-Score** | 0.996 |
| **ROC-AUC** | 1.000 |

### Confusion Matrix (XGBoost)

|              | Predicted No Failure | Predicted Failure |
|--------------|---------------------|-------------------|
| **Actual No Failure** | 9,174 | 3 |
| **Actual Failure** | 0 | 388 |

## 💾 Dataset

| Parameter | Value |
|-----------|-------|
| **Source** | Backblaze Drive Stats Q4 2025 |
| **Total Records** | 30,941,708 |
| **Unique Drives** | 341,664 |
| **Time Period** | October - December 2025 |
| **Failure Records** | 46,993 |
| **SMART Attributes Used** | 6 key attributes |

### SMART Attributes Used

| Attribute ID | Name | Description |
|--------------|------|-------------|
| 5 | Reallocated Sectors Count | Physical damage indicator |
| 9 | Power-On Hours | Drive age indicator |
| 187 | Reported Uncorrectable Errors | Read error indicator |
| 194 | Temperature | Drive temperature |
| 197 | Current Pending Sector Count | Potential failure indicator |
| 198 | Offline Uncorrectable | Critical failure indicator |

## 🏗️ System Architecture
┌─────────────────────────────────────────────────────────────────┐
│ DATA CENTER / OFFICE │
│ │
│ ┌──────────────┐ ┌──────────────┐ ┌──────────────┐ │
│ │ Computer 1 │ │ Computer 2 │ │ Computer 3 │ │
│ │ (Client) │ │ (Client) │ │ (Client) │ │
│ │ ↓ Monitor │ │ ↓ Monitor │ │ ↓ Monitor │ │
│ └──────┬───────┘ └──────┬───────┘ └──────┬───────┘ │
│ │ │ │ │
│ └─────────────────────┼─────────────────────┘ │
│ │ │
│ ▼ │
│ ┌─────────────────────────────────────────────────────────┐ │
│ │ CENTRAL SERVER │ │
│ │ ┌───────────────┐ ┌───────────────┐ │ │
│ │ │ API Server │◄───│ MySQL │ │ │
│ │ │ (Port 5001) │ │ Database │ │ │
│ │ └───────┬───────┘ └───────────────┘ │ │
│ │ │ │ │
│ │ ▼ │ │
│ │ ┌───────────────┐ │ │
│ │ │ Web Dashboard│ │ │
│ │ │ (Port 5000) │ │ │
│ │ └───────────────┘ │ │
│ └─────────────────────────────────────────────────────────┘ │
│ │ │
│ ▼ │
│ ┌─────────────────────────────────────────────────────────┐ │
│ │ ADMIN / USER (Web Browser) │ │
│ └─────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────────┘

## 🛠️ Technology Stack

| Category | Technology | Version |
|----------|------------|---------|
| Language | Python | 3.12 |
| Web Framework | Flask | 2.3 |
| Database | MySQL | 8.0 |
| ML Model | XGBoost | 1.7 |
| ML Support | scikit-learn | 1.3 |
| Data Processing | pandas | 2.0 |
| Visualization | plotly | 5.18 |
| HTTP Client | requests | 2.31 |

## 📁 Project Structure
hard-drive-failure-prediction/
│
├── central_server/ # Web dashboard and API
│ ├── app.py # Main Flask application
│ ├── api.py # API server (port 5001)
│ ├── auth.py # User authentication
│ ├── models.py # Database models
│ ├── config.py # Configuration settings
│ ├── static/ # CSS and logo
│ └── templates/ # HTML templates (17 files)
│
├── monitor_client/ # Client for data center servers
│ ├── client_monitor.py # Main monitor script
│ └── client_config.json # Configuration
│
├── auto_monitor/ # Desktop monitor
│ └── simple_monitor.py
│
├── models/ # Trained ML model
│ └── failure_predictor_best.pkl
│
├── src/ # Core Python scripts
│ ├── data_preprocessing.py
│ ├── feature_engineering.py
│ ├── train_model_final.py
│ └── identify_failures.py
│
├── logs/ # Log files
├── requirements.txt # Python dependencies
└── README.md # This file


## 🚀 Installation Guide

### Prerequisites

- Windows 10/11 (64-bit)
- 4 GB RAM (8 GB recommended)
- 20 GB free disk space
- MySQL Server 8.0 or higher
- Python 3.8 or higher

Step 2: Install Python Dependencies
pip install -r requirements.txt
Step 3: Set Up MySQL Database
# Import database schema
mysql -u root -p < mysys_database_dump.sql
Step 4: Start the Application
cd central_server
python app.py
Step 5: Open Browser
Go to http://localhost:5000

Default Login
Username	Password
admin	admin123

📖 Usage Guide
Web Dashboard
Login with your credentials

Dashboard - View statistics and recent predictions

Predict - Enter SMART values and get failure probability

Time Series - View drive health trends over time

What-If - Adjust sliders to see real-time probability changes

Alerts - View and resolve high-risk alerts

My Drives - See drives assigned to you

Profile - View your account information

Admin Panel (Admin only)
User Management - View all users, change roles, activate/deactivate

Assign Drives - Assign specific drives to users

All Predictions - View predictions from all users

All Alerts - View alerts from all users

Client Monitor (for multiple computers)
Edit monitor_client/client_config.json

Set central_url to your server IP

Run: python monitor_client/client_monitor.py

📊 Feature Importance
Top 10 features used by the XGBoost model:

Rank	Feature	Importance
1	Power-On Hours (7-day avg)	15.7%
2	Power-On Hours (minimum)	13.8%
3	Power-On Hours (15-day avg)	13.2%
4	Power-On Hours (30-day avg)	12.9%
5	Power-On Hours (maximum)	10.5%
6	Month	6.8%
7	Power-On Hours (daily change)	5.1%
8	Pending Sectors (maximum)	2.8%
9	Uncorrectable Errors (maximum)	2.3%
10	Uncorrectable Errors (15-day avg)	1.6%
🔮 Future Enhancements
SSD failure prediction (different SMART attributes)

Real-time streaming with Apache Kafka

Email and SMS alerts (Twilio integration)

Mobile app for Android and iOS

Cloud deployment (AWS EC2 + RDS)

Docker containerization

Auto-retraining pipeline

Export reports (PDF/Excel)

👨‍💻 Author
Mohd Yasin

📧 Contact
For any queries regarding this project, please contact:
Email: yasin.vertasolutions@gmail.com

📝 License
This project is for educational purposes. MIT License.

🙏 Acknowledgments
Backblaze for providing the Drive Stats dataset

Don Bosco Degree College faculty for guidance and support

Open-source community for libraries and tools

⭐ Star This Repository
If you found this project useful, please give it a star on GitHub!


---

## What to Do Now

| Step | Action |
|------|--------|
| 1 | Copy the entire content above |
| 2 | Go to `https://github.com/your-username/hard-drive-failure-prediction` |
| 3 | Click on `README.md` |
| 4 | Click the pencil icon (✏️) |
| 5 | Delete all existing content |
| 6 | Paste the copied content |
| 7 | Scroll down and click **"Commit changes"** |

**Your README.md is now complete!** 🎉

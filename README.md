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


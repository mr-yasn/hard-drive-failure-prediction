
# 🔧 Hard Drive Failure Prediction System

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://python.org)
[![XGBoost](https://img.shields.io/badge/XGBoost-1.7%2B-orange)](https://xgboost.ai)
[![Flask](https://img.shields.io/badge/Flask-2.3%2B-red)](https://flask.palletsprojects.com)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

## 🎯 Project Overview
This project predicts hard drive failures 30 days in advance using SMART data. It achieves **99.97% accuracy** with **100% failure detection rate** and only **3 false alarms** out of 9,177 healthy drives.

## 📊 Key Results
| Metric | Value |
|--------|-------|
| **Accuracy** | 99.97% |
| **Failure Detection** | 100% |
| **False Alarms** | 3 / 9,177 (0.03%) |
| **F1 Score** | 0.996 |

## 💾 Dataset
- **Source**: Backblaze Drive Stats Q4 2025
- **Total Records**: 30,941,708
- **Unique Drives**: 341,664
- **Failure Records**: 46,993

## 🏗️ Architecture

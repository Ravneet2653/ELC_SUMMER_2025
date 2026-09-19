# Multimodal Mortality Risk Prediction using ECG and Clinical Data

## Overview

This project builds an end-to-end machine learning pipeline to predict **in-hospital mortality risk** using a combination of:

- ECG-derived biosignal features
- Patient demographic information
- Clinical laboratory values

The project uses the **MIMIC-IV ECG Demo** and **MIMIC-IV Clinical Database Demo** from PhysioNet.

The main objective was to study whether combining physiological ECG information with structured clinical data improves mortality risk prediction.

---

## Problem Statement

Hospital patients generate multiple types of data such as ECG signals, demographic information and laboratory measurements.

Using only one type of data may not capture the complete condition of a patient.

This project combines:

- ECG waveform characteristics
- Heart-rate and RR-interval information
- Age and gender
- Laboratory measurements

to predict whether a patient will experience **in-hospital mortality**.

---

## Dataset

Two related datasets were used:

### 1. MIMIC-IV ECG Demo

Contains diagnostic 12-lead ECG recordings.

Each ECG contains leads such as:

- I
- II
- III
- aVR
- aVL
- aVF
- V1–V6

The ECG recordings were loaded using the Python `wfdb` library.

### 2. MIMIC-IV Clinical Database Demo

Clinical information was obtained from:

- `patients.csv.gz`
- `admissions.csv.gz`
- `labevents.csv.gz`
- `d_labitems.csv.gz`

These tables provided demographic information, admission outcomes and laboratory measurements.

---

## Project Pipeline

```text
MIMIC-IV ECG
        ↓
Load ECG using WFDB
        ↓
ECG Quality Checks
        ↓
Feature Extraction
        ↓
Heart Rate / RR Features
        ↓
--------------------------------
        +
--------------------------------
Clinical Data
Age / Gender
Laboratory Values
        ↓
Temporal Matching
        ↓
Combined Dataset
        ↓
Patient-Level Train/Test Split
        ↓
Missing Value Imputation
        ↓
Feature Scaling
        ↓
ML Models
        ↓
Evaluation

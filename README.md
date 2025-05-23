# DoseDost 💊
# Patient App


This is a **Flutter** project demonstrating a simple **doctor-patient prescription workflow** using **Firebase Firestore**. The app includes:

- A **Patient** side, where users can see their profile (with a QR code) and any prescribed medications.
- A **Doctor** side, where doctors can scan the patient’s QR and add prescriptions.

---

## Table of Contents
1. [Overview](#overview)  
2. [Features](#features)
3. [Requirements](#requirements)  
4. [Setup & Installation](#setup--installation)  
5. [Running the App](#running-the-app)  
6. [Firestore Structure](#firestore-structure)  
7. [Dependencies](#dependencies)
8. [TEAM](#team)

---

## Overview

This app demonstrates how to:
- Store **patient information** (name, age, meal timings, etc.) in Firestore.
- Generate a **unique patient ID** and display it as a **QR code**.
- Fetch and display a **list of medications** (prescriptions) for a given patient.
- Show a **Profile screen** that includes basic info and the QR code on the same screen.

The **QR code** allows a doctor’s app (or “Doctor Mode”) to quickly scan and link to the correct patient’s data in Firestore, simplifying the prescription process.

---

## Features

1. **Profile Screen**  
   - Displays the patient’s name, age, meal timings, and a QR code for their unique ID.  
   - The layout has two sections:  
     - A top area for the QR code  
     - A bottom gray area for patient details  

2. **Medications Screen** (Patient Home)  
   - Lists all prescribed medications from the Firestore subcollection (`/patients/{patientId}/medications`).  
   - If no medications are found, it shows a placeholder text (“No prescriptions or medicines added yet.”).  

3. **Realtime Firestore Updates**  
   - Uses **StreamBuilder** to automatically refresh medication data whenever the database changes.  

4. **Firebase Integration**  
   - Configured via **FlutterFire CLI** or manual setup (`firebase_core`, `cloud_firestore`).  

5. **QR Code Generation**  
   - Uses the [qr_flutter](https://pub.dev/packages/qr_flutter) package to display the unique patient ID as a QR code.

---

## Requirements

- **Flutter SDK** (2.10+ or any recent stable version)
- **Dart** 2.12+
- **Firebase** project set up with **Firestore** enabled
- **Xcode** 14+ (if building for iOS) and **Android Studio** or **SDK** (if building for Android)
- iOS **minimum deployment target** of **13.0** (for newer Firebase plugins)

---

## Setup & Installation

1. **Clone this repository** (or download the ZIP):
   ```bash
   git clone https://github.com/SakD2006/prescription-app.git
   cd prescription-app

---

## Running the app
1. **Using run command**:
   ```bash
   flutter run

---

## App Structure
1. **A structure for App**
    ```bash
    my_prescription_app/
          ├── android/                    # Android-specific config & Gradle files
          ├── ios/                        # iOS-specific config & Xcode files
          ├── lib/
          │   ├── main.dart               # App entry point, Firebase initialization, routing
          │   ├── firebase_options.dart   # Generated by FlutterFire CLI (Firebase config)
          │   ├── models/                 # Data models for the app
          │   │   ├── user_model.dart     # Represents a user with email, age, meal timings, etc.
          │   │   └── medication_model.dart   # Represents a medicine with name, dosage, frequency, duration, etc.
          │   ├── services/               # Business logic and integration with Firebase/notifications
          │   │   ├── auth_service.dart   # Firebase Authentication (login,  signup, sign-out)
          │   │   ├── firestore_service.dart   # Firestore CRUD operations (fetch/add prescriptions)
          │   │   └── notification_service.dart  # Scheduling and handling notifications
          │   ├── screens/                # UI screens organized by feature
          │   │   ├── splash_screen.dart  # Animated splash screen
          │   │   ├── auth/               # Authentication flow
          │   │   │   ├── login_screen.dart
          │   │   │   └── signup_screen.dart
          │   │   ├── home/               # Home screen for the patient
          │   │   │   ├── home_screen.dart  # Shows list of medicine cards
          │   │   │   └── profile_screen.dart  # Shows patient details and embedded QR code
          │   ├── widgets/                # Reusable UI components
          │   │   ├── qr_code_widget.dart  # A reusable widget to display a QR code
          │   │   └── medicine_card.dart   # A reusable widget for medicine cards with a "taken" button
          │   └── utils/                  # (Optional) Utilities, constants, helper functions, etc.
          │       └── routes.dart         # Named route definitions
          ├── pubspec.yaml                # Dart/Flutter dependencies
          ├── README.md                   # Project documentation
          └── ...                         # Other configuration files (analysis_options.yaml, etc.)


---

## Firestore Structure
1. **A structure for online Database**
    ```bash
    patients (collection)
    └── patient001 (document)
                ├── Name: "Saksham"
                ├── Age: 18
                ├── Meal-timing:
                │    ├── Breakfast: "7:30 AM"
                │    ├── Lunch: "1:00 PM"
                │    └── Dinner: "7:30 PM"
                └── medications (subcollection)
                        └── {medicationId} (document)
                         ├── medicineName: "Paracetamol"
                         ├── dosage: "500 mg"
                         ├── frequency: "1-0-1"
                         └── durationDays: 5


---

## Dependencies

Below are the primary dependencies used in this project:

- **Flutter SDK**  
  The core framework for building cross-platform apps.  
  *(Ensure you have a recent stable version installed, e.g. Flutter 3.x or above.)*

- **firebase_core**  
  For initializing and configuring Firebase within your Flutter app.

- **cloud_firestore**  
  To perform read/write operations on Firestore (the NoSQL database from Firebase).

- **qr_flutter**  
  Generates QR codes within the app, allowing for easy scanning of unique patient IDs.

*(Optional)*

- **firebase_auth**  
  If you need user authentication or want to restrict database access to certain roles (doctor vs. patient).

Check your `pubspec.yaml` for the exact versions:
```yaml
dependencies:
  flutter:
    sdk: flutter
  firebase_core: ^2.10.0
  cloud_firestore: ^4.7.1
  qr_flutter: ^4.0.0
  firebase_auth: ^4.6.2
```

---

## TEAM

**BigBoyCoders**
- Saksham 24BBS0081
- Aryaman 24BBS0110
- Prakyath 24BBS0079
- Devarsh 24BBS0153
- Tanay 24BBS0104


# 🔐 QRVault – Smart QR Code Contact Sharing App

<p align="center">
  <b>Generate, Save and Share Your Contacts Instantly Using QR Codes</b>
</p>

## 📌 Introduction

QRVault is an Android-based contact-sharing application developed using Kotlin. It provides a simple, fast, and convenient way to share contact information through QR codes.

Instead of manually saving someone's phone number or email address, users can select a contact from their device, generate a unique QR code containing their contact details, and share it instantly.

The application uses the vCard 3.0 format to encode contact information into QR codes. Users can save generated QR codes to their gallery, share them with other applications, and access previously generated QR codes through the built-in history section.

QRVault aims to make digital contact sharing easier, faster, and more efficient.

## ✨ Key Features

- 📱 **Contact Integration:** Fetch contacts directly from the device.
- 🔍 **Contact Search:** Search contacts by name or phone number.
- 📇 **Contact Details:** View contact names, phone numbers, and email addresses.
- 🔳 **QR Code Generation:** Generate QR codes using contact information.
- 📤 **Share QR Code:** Share generated QR codes through other applications.
- 💾 **Save QR Code:** Save QR code images directly to the device gallery.
- 🕒 **QR History:** Maintain a history of previously generated QR codes.
- 🗑️ **Delete History:** Delete unwanted QR code records.
- 🔐 **Permission Management:** Request contact and legacy storage permissions when required.
- 🎨 **Modern UI:** Clean interface with attractive layouts and animations.
- 💽 **Local Database:** Store QR code history using SQLite.

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Kotlin | Application Development |
| Android Studio | Development Environment |
| XML | User Interface Design |
| SQLite | Local Database Management |
| ZXing | QR Code Generation |
| RecyclerView | Display Contacts and History |
| Material Components | UI Components |
| Android FileProvider | Secure QR Image Sharing |
| vCard 3.0 | Contact Information Encoding |

## ⚙️ Application Modules

### 1. Splash Screen
- Displays the application branding.
- Provides an animated introduction.

### 2. Home Screen
- Main dashboard of the application.
- Provides navigation to contacts, QR history, and about section.

### 3. Contact Management
- Fetch contacts from the device.
- Search contacts by name or number.
- Display contact information.
- Select a contact for QR generation.

### 4. QR Code Generator
- Converts contact details into vCard 3.0 format.
- Generates a QR code using ZXing.
- Displays the generated QR code.
- Provides save and share functionality.

### 5. QR Code History
- Stores generated QR code records.
- Displays previously generated contact QR codes.
- Allows users to view and delete history records.

### 6. About Section
- Displays application information.

## 🔄 How It Works

1. Open the QRVault application.
2. Navigate to the Fetch Contacts section.
3. Grant contact permission.
4. Select a contact from the contact list.
5. View the selected contact details.
6. Generate the QR code.
7. Save the QR code to the gallery or share it.
8. Access previously generated QR codes from the History section.

## 🗄️ Database Structure

**Database Name:** `QRVault.db`

**Table Name:** `qr_history`

| Column | Description |
|---|---|
| id | Unique record ID |
| contact_name | Contact name |
| phone_number | Contact phone number |
| email | Contact email address |
| vcard_data | Encoded vCard information |
| created_at | Creation timestamp |

The application uses SQLite to maintain QR code generation history locally on the device.

## 📂 Project Structure

```text
QRVault/
│
├── app/
│   ├── src/main/
│   │   ├── java/com/qrvault/app/
│   │   │   │
│   │   │   ├── adapter/
│   │   │   │   ├── ContactAdapter.kt
│   │   │   │   └── HistoryAdapter.kt
│   │   │   │
│   │   │   ├── data/
│   │   │   │   ├── QRVaultDbHelper.kt
│   │   │   │   └── QrRepository.kt
│   │   │   │
│   │   │   ├── model/
│   │   │   │   ├── Contact.kt
│   │   │   │   └── QrRecord.kt
│   │   │   │
│   │   │   ├── ui/
│   │   │   │   ├── SplashActivity.kt
│   │   │   │   ├── MainActivity.kt
│   │   │   │   ├── ContactsActivity.kt
│   │   │   │   ├── ContactDetailsActivity.kt
│   │   │   │   ├── QrCodeActivity.kt
│   │   │   │   ├── HistoryActivity.kt
│   │   │   │   └── AboutActivity.kt
│   │   │   │
│   │   │   └── util/
│   │   │       ├── ContactProvider.kt
│   │   │       ├── QrGenerator.kt
│   │   │       ├── ImageStorage.kt
│   │   │       ├── PermissionHelper.kt
│   │   │       └── UiExt.kt
│   │   │
│   │   ├── res/
│   │   │   ├── layout/
│   │   │   ├── drawable/
│   │   │   ├── anim/
│   │   │   └── values/
│   │   │
│   │   └── AndroidManifest.xml
│   │
│   └── build.gradle.kts
│
├── gradle/
├── build.gradle.kts
├── settings.gradle.kts
├── gradle.properties
└── README.md
```

## 📋 Requirements

- Android Studio Koala (2024.1) or newer.
- JDK 17.
- Android SDK 34.
- Minimum Android Version: Android 7.0 (API 24).
- Gradle 8.7.
- Android Gradle Plugin 8.5.2.

## 🚀 Installation and Setup

**Step 1: Clone the Repository**

```bash
git clone https://github.com/your-username/QRVault.git
```

**Step 2: Open in Android Studio**

- Open Android Studio.
- Select File → Open.
- Choose the QRVault project folder.

**Step 3: Gradle Sync**

Wait for Gradle to download the required dependencies and complete synchronization.

**Step 4: Run the Application**

- Connect an Android device or start an emulator.
- Enable USB debugging if using a physical device.
- Click the Run button in Android Studio.
- Grant contact permission when requested.

## 🔑 Permissions Used

| Permission | Purpose |
|---|---|
| READ_CONTACTS | Access device contacts |
| WRITE_EXTERNAL_STORAGE | Save QR images on Android 9 and below |

**Note:** The application does not require internet or camera permissions. QR code scanning can be performed using an external QR scanner or the phone's camera.

## 🔮 Future Enhancements

- QR code scanning within the application.
- Support for custom QR code colors and designs.
- Generate QR codes for websites and text.
- Generate QR codes for business cards.
- Cloud backup and synchronization.
- Password-protected QR codes.
- Export and import contact records.
- Dark mode support.

## 🎯 Project Objective

The main objective of QRVault is to simplify contact sharing through QR code technology. It reduces manual effort, saves time, and provides a convenient digital solution for sharing contact information.

## 👨‍💻 Developer

**Project Name:** QRVault  
**Platform:** Android  
**Language:** Kotlin  
**Database:** SQLite  
**Development Tool:** Android Studio

## 📜 License

This project is developed for educational and academic purposes.

---

<p align="center">
  ⭐ If you like this project, don't forget to star the repository!
</p>

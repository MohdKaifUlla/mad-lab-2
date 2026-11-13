# QRVault – Contact Sharing with QR Code Generator

Android app (Kotlin + XML) that reads contacts from the phone, builds a **vCard 3.0 QR code** for the selected
contact with ZXing, lets you **save** (MediaStore) or **share** (FileProvider) it, and keeps a **history in SQLite**
(`QRVault.db`).

## Requirements
- Android Studio Koala (2024.1) or newer, JDK 17 (bundled with Android Studio)
- Android SDK Platform 34
- **Minimum Android version: 7.0 (API 24)** · Target/Compile SDK: 34
- Internet is needed only once, for Gradle to download dependencies

## Open and run
1. Unzip the project. In Android Studio choose **File > Open** and select the `QRVault` folder.
2. Wait for **Gradle sync** (it downloads Gradle 8.7, the Android Gradle Plugin 8.5.2 and the libraries).
   If Studio offers an AGP/Gradle upgrade, you can decline or accept it; both work.
3. Pick an emulator or a phone and press **Run**.

### Run on a real phone
1. Settings > About phone > tap **Build number** 7 times to enable Developer options.
2. Developer options > enable **USB debugging**; connect via USB and accept the prompt.
3. Select the device in Android Studio's device drop-down and press **Run**.
4. When the app opens the contact list, tap **Continue** and **Allow** the Contacts permission.

(Emulator: add a few contacts in the Contacts app first, since a fresh emulator has none.)

## Permissions
| Permission | Why |
|---|---|
| `READ_CONTACTS` | List contacts (name, phone, email). Requested at runtime with an explanation dialog. |
| `WRITE_EXTERNAL_STORAGE` (API 24-28 only) | Save the QR image to Pictures/QRVault on old Android versions. Not needed on Android 10+. |

No internet, camera or other permissions are used. Scanning is done with any external scanner or the phone camera.

## Project structure (`app/src/main/java/com/qrvault/app`)
- `ui/` Splash, Main (home), Contacts, ContactDetails, QrCode, History, About activities
- `adapter/` `ContactAdapter`, `HistoryAdapter` (RecyclerView ListAdapters)
- `model/` `Contact`, `QrRecord`
- `data/` `QRVaultDbHelper` (SQLiteOpenHelper), `QrRepository` (insert / query / delete)
- `util/` `ContactProvider`, `QrGenerator` (vCard + ZXing), `ImageStorage`, `PermissionHelper`, `UiExt`
- `res/` layouts, vector drawables, animations, theme (navy + electric blue)

## Database
`QRVault.db` > table `qr_history`: `id`, `contact_name`, `phone_number`, `email`, `vcard_data`, `created_at` (epoch ms).

## Manual test checklist
1. Launch (splash animation) > Home. 2. Fetch Contacts > allow permission. 3. Search by name and by number.
4. Select a contact > details. 5. Generate QR Code. 6. Scan the QR with another phone; it should offer "Add contact".
7. Save QR (Gallery > Pictures/QRVault). 8. Share QR (chooser). 9. Generate Another / Back to Home.
10. QR History > View an entry > Delete an entry. 11. Force-stop and reopen; history is still there.
12. Deny the permission to see the graceful "Permission required" screen.

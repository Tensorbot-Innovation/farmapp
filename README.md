# Samposhi Farm Automation — Android Mobile App

This repository contains the standalone source code and build automation to generate the native Android APK (`.apk`) for the **Samposhi Farm Automation Mobile Application**.

---

## 🚀 How to Build the APK on GitHub (Zero Local Setup)

This repository includes a pre-configured **GitHub Actions** CI/CD pipeline in [`.github/workflows/build-apk.yml`](.github/workflows/build-apk.yml) that builds the Android APK in the cloud for free.

### Step-by-Step:

1. **Upload/Push this folder to GitHub**:
   - Open **GitHub Desktop**
   - Click **File** $\rightarrow$ **Add Local Repository...**
   - Select this `SamposhiFarm_AndroidApp` folder
   - Click **Publish repository** to push it to your GitHub account.

2. **Trigger Build**:
   - Pushing your code will **automatically start the build**!
   - You can also manually trigger it anytime:
     1. Open your repository on GitHub in your web browser.
     2. Click the **Actions** tab at the top.
     3. Select **"Build Samposhi Farm Android APK"** on the left.
     4. Click **Run workflow** $\rightarrow$ **Run workflow**.

3. **Download Your APK**:
   - Once the build finishes (approx. 60–90 seconds, green checkmark), click on the completed run.
   - Scroll down to the **Artifacts** section at the bottom.
   - Click **`SamposhiFarm-Android-APK`** to download `SamposhiFarm-v2.0.apk`.
   - Install it directly on any Android device!

---

## 🛠️ Alternative: Open in Android Studio

If you prefer building locally on your computer with Android Studio:

1. Launch **Android Studio**.
2. Select **File $\rightarrow$ Open**.
3. Choose the `MobileApp_v2/android` folder inside this directory.
4. Click **Build $\rightarrow$ Build Bundle(s) / APK(s) $\rightarrow$ Build APK(s)**.
5. The generated APK will be in `app/build/outputs/apk/debug/`.

---

## 📁 Repository Structure

```text
SamposhiFarm_AndroidApp/
├── .github/
│   └── workflows/
│       └── build-apk.yml       # Cloud APK builder workflow
├── .gitignore                  # Ignores build caches and temp files
├── README.md                   # This instruction file
└── MobileApp_v2/
    ├── index.html              # Mobile Web App Interface
    ├── manifest.json           # PWA Web App Manifest
    ├── sw.js                   # Service Worker
    ├── build_deployable.py     # Web & Android asset bundler
    ├── css/                    # Stylesheets
    ├── js/                     # Application logic & MQTT client
    ├── icons/                  # High-resolution icons
    └── android/                # Native Android Gradle Project
        ├── build.gradle        # Project build config
        ├── settings.gradle     # Project settings
        ├── gradle.properties   # JVM & AndroidX settings
        ├── gradlew             # Gradle wrapper
        ├── sync_assets.py      # Asset synchronization script
        ├── gradle/wrapper/     # Gradle wrapper config
        └── app/
            ├── build.gradle    # App module config (SDK 34)
            ├── proguard-rules.pro
            └── src/main/
                ├── AndroidManifest.xml              # Permissions & cleartext HTTP
                ├── java/com/samposhi/farm/          # Native WebView & Camera bridge
                ├── assets/                          # Offline web app bundle
                └── res/                             # Android mipmap icons & layouts
```

---

## 🔒 Key Android Features Configured

- **100% Offline Asset Execution**: Web assets are stored directly in `assets/` so the app loads instantaneously without internet.
- **Cleartext HTTP Support**: Configured with `android:usesCleartextTraffic="true"` to connect directly to the ESP32 Gateway hotspot at `http://192.168.4.1`.
- **Camera Barcode/QR Scanner**: Android runtime `CAMERA` permissions are wired to the WebChromeClient for fixture MAC address scanning.
- **OTA Firmware Uploads**: File chooser support enabled for selecting `.bin` updates.

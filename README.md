# Samposhi Farm Automation — Android Mobile App

This repository contains the standalone source code and build automation to generate the native Android APK (`.apk`) for the **Samposhi Farm Automation Mobile Application**.

---

## 🚀 How to Build the APK on GitHub (Zero Local Setup)

This repository includes a pre-configured **GitHub Actions** CI/CD pipeline in [`.github/workflows/build-apk.yml`](.github/workflows/build-apk.yml) that builds the Android APK in the cloud for free.

### Step-by-Step:

1. **Trigger Build**:
   - Pushing your code will **automatically start the build**!
   - You can also manually trigger it anytime:
     1. Open your repository on GitHub in your web browser.
     2. Click the **Actions** tab at the top.
     3. Select **"Build Samposhi Farm Android APK"** on the left.
     4. Click **Run workflow** $\rightarrow$ **Run workflow**.

2. **Download Your APK**:
   - Once the build finishes (approx. 60–90 seconds, green checkmark), click on the completed run.
   - Scroll down to the **Artifacts** section at the bottom.
   - Click **`SamposhiFarm-Android-APK`** to download `SamposhiFarm-v2.0.apk`.
   - Install it directly on any Android device!

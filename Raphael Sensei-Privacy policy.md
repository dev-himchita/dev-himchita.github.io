# Privacy Policy — Raphael Sensei

**Last updated: July 2026 (version - 31(1.0.0-prod)**
**Developer: Raphael Sama | Package: com.himadri.raphael_sensei**

---

## Overview

Raphael Sensei is a study assistant app for competitive exam preparation. This policy explains exactly what data the app accesses, how it is used, and what is shared with third parties — including our security, advertising, and crash reporting partners. We are committed to full transparency.

---

## 1. Data We Do NOT Collect

Raphael Sensei does not collect, transmit, or store any of the following on our own servers:

- Your name, email address, or account credentials
- Your coarse and precise location
- Your contacts or call logs
- Keystrokes or clipboard content
- Browsing history inside or outside this app
- The content of your study notes, PDFs, or images

---

## 2. Data Stored Locally On Your Device

All of the following is stored **only on your device** in a local database and app storage. It never leaves your device except as described in the sections below.

- **Study topics and notes** — text notes, PDF content, and images you capture or import
- **Your Name** — saved by you in app settings screen
- **Revision schedule data** — due dates and revision logs for spaced repetition
- **Video files and frames** — videos you add to topics and extracted frame screenshots
- **App preferences** — theme, TTS settings, AI model settings
- **Backup files** — ZIP archives of your data saved to your chosen storage location

---

## 3. Permissions Used and Why

| Permission | Why it is needed |
|---|---|
| **Internet** | Required for Firebase App Check, Firebase Crashlytics, the security backend (purchase verification), and displaying ads |
| **Access Network State** | Detects connectivity to show the offline screen and guard ad loading |
| **Camera** | Lets you photograph notes, textbook pages, and whiteboards directly into a topic |
| **Read Media — Images (Android 13+)** | Lets you import photos from your gallery into topics |
| **Read Media — Video (Android 13+)** | Lets you import videos from your gallery into topics |
| **Read Media — Visual User Selected (Android 14+)** | Scoped media picker for photos and videos on Android 14+ |
| **Read External Storage (Android ≤ 12)** | Import files on older Android versions |
| **Write External Storage (Android ≤ 9)** | Save backup files on older Android versions |
| **Post Notifications** | Sends revision-due reminders you schedule yourself |
| **Receive Boot Completed** | Reschedules your revision reminders automatically after a device reboot, so they still fire at 8 AM without requiring you to open the app first |
| **Request Ignore Battery Optimizations** | Asks the OS to exempt the app from battery optimisation so revision reminders arrive on time even when battery saver mode is active. Prompted only when you turn on Remind Me to Revise — you can decline without affecting any other feature |
| **Detect Screen Capture (Android 14+)** | Enables freeRASP to detect and respond to live screen capture attempts (security feature — not used to record your screen) |
| **Vibrate** | Optional haptic feedback for alerts |
| **Flashlight** | Used in Document Scanner for scanning in low lighted areas |

Note : No permission is used to track, profile, or build advertising audiences directly by this app.

---

## 4. On-Device AI — Raphael Sensei Local Model

The Raphael Sensei AI chat feature uses a model file (`.litertlm`) stored entirely on your device and runs via Google's LiteRT LM runtime. This feature:

- Runs **100% offline** — no internet connection is required
- Sends **no data** to any server
- Processes only the note context you actively share within a chat session
- Retains no conversation history between sessions

---

## 5. Security Service & Backend Communication

To verify your subscription and protect the app against tampering, the app communicates with a private Firebase Cloud Functions backend hosted at:

`asia-south1-raphael-sensei-backend.cloudfunctions.net`

### What is sent to the backend

| Data | Purpose |
|---|---|
| **Play Integrity token** | A cryptographic attestation from Google Play confirming the app and device are genuine |
| **Firebase App Check token** | Proves the request originates from the genuine app binary |
| **Google Play purchase token** (if subscribed) | Sent to verify your subscription status with Google Play |
| **Existing JWT** (token refresh only) | Sent to /refreshToken to renew your subscription status token without a full Play Integrity round-trip |

### What the backend returns

A short-lived JWT (JSON Web Token) containing your subscription status. The JWT does not contain any personal information.

The backend **does not log or retain** your note content, study data, or any personal identifiers beyond what is listed above.

---

## 6. Device Security — freeRASP (Talsec)

To protect against tampering, rooting, hooking, and app cloning, Raphael Sensei uses **freeRASP**, a Runtime Application Self-Protection (RASP) SDK developed by **Talsec a.s.** (Czech Republic).

FreeRASP **may send security incident reports** to Talsec's servers when a threat is detected. These reports may include:

- The app's package name and signing certificate hash
- The type of security threat detected (e.g. root, emulator, debugger, hook, tamper, unofficial store)
- Basic device metadata associated with the incident

Additionally, freeRASP applies **`FLAG_SECURE`** to the app's activity window on launch. This blocks screenshots, screen recordings, and the Android `DETECT_SCREEN_CAPTURE` signal — you will not be able to screenshot the app from outside. This is a security measure to protect your study data.

**Talsec Privacy Policy:** https://www.talsec.app/privacy-policy

---

## 7. Shake-to-Snip (Accelerometer)

If you enable the **Shake to Snip** feature in Settings, the app uses your device's accelerometer sensor to detect shaking gestures. This sensor data is processed entirely on-device in real time and is never recorded or transmitted.

---

## 8. Scan to Notes — Document Scanner & OCR

The **Scan to Notes** feature lets you photograph physical documents (textbook pages, handwritten notes, whiteboards) and either save them as images or extract the text via OCR.

- The document scanner is provided by the **cunning_document_scanner** library, which uses Google's GMS Document Scanner API on devices with Google Play Services, or an on-device OpenCV-based fallback on other devices.
- Text recognition (OCR) is performed by **Google MLKit Text Recognition**, using a model that runs entirely on your device via the Google Mobile Services Vision runtime. 
- The Latin script package is compiled during app build time, other script packages are downloaded on first use via **Google Play Services** — a one-time download managed by GMS on your device.  
- No scanned image or extracted text is uploaded to any server by this app.
- Scanned pages and OCR results are saved on your device only. 

The app does not record audio or capture microphone input at any point.

---

## 9. Screenshot Sharing to the App

The app can receive screenshots shared from other apps (e.g. from a browser or document viewer) via the Android share sheet. When you share an image to Raphael Sensei, the image is processed locally on your device — cropped and **permanently saved into the topic you choose**. The app does not upload or transmit shared images to any server.

---

## 10. Sharing Features

When you use the **Share AI Response** feature, the app renders chat bubbles as PNG images and passes them to your device's standard OS share sheet. The app itself does not upload or transmit this content — it is sent only to the app you choose in the share sheet (e.g. WhatsApp, Gmail).

---

## 11. Backup & Restore

The **Backup** feature creates a ZIP file of your local database and saves it to a folder you choose on your device. The **Auto Backup** feature does the same automatically on app start. These backup files:

- Contain a plain SQLite database — the study content is not sensitive enough to require encryption at rest
- Are never uploaded by this app to any cloud service automatically
- Are stored only in the folder you pick — protect that folder if you consider the content sensitive

---

## 12. Advertising

Raphael Sensei is free to use and is supported by advertising. Ads are served through **Google AdMob**, which uses the following mediation partners. These SDKs run directly within the app and may independently collect data on your device to serve and measure ads.

### 12a. Google AdMob

Operated by Google LLC.

**May collect:** Android Advertising ID, device information (model, OS version, screen size), app interaction data (impressions, clicks), IP address.

**Privacy policy:** https://policies.google.com/privacy

---

### 12b. Meta Audience Network

Operated by Meta Platforms, Inc.

**May collect:** Android Advertising ID, IP address, device information, app interaction data. If you have Facebook or Instagram installed, Meta may correlate this data with your Meta account to serve more relevant ads. Meta does not support banner ads in this app — only interstitial and app open formats.

**Privacy policy:** https://www.facebook.com/privacy/policy/

---

### Your Advertising Choices

You can opt out of personalised ads or reset your Advertising ID at any time:

- **Android 12+:** Settings → Google → Ads → **Delete advertising ID**
- **Android 11 and below:** Settings → Google → Ads → **Opt out of Ads Personalisation**

Resetting or deleting your Advertising ID limits the ability of all ad networks above to show you personalised ads.

---

## 13. Firebase Services

This app uses the following Firebase services, all provided by Google LLC:

| Service | Purpose |
|---|---|
| **Firebase App Check** | Verifies that API calls come from the genuine app binary — prevents abuse of backend resources |
| **Firebase Crashlytics** | Automatically collects crash reports and non-fatal error logs to help diagnose and fix app stability issues |

### Firebase App Check

Uses **Play Integrity**, which sends a signed attestation from your device to Google to verify the app's authenticity. No personal data is included in this attestation beyond confirming your device has a valid Play Integrity verdict.

### Firebase Crashlytics

Operated by Google LLC. When the app crashes or encounters a non-fatal error, Crashlytics automatically collects and sends a crash report. This may include:

- Stack trace and exception details (Dart and native C++ layers)
- Device information (model, Android version, available RAM, disk space)
- App version and build number
- Whether the crash was fatal or non-fatal
- Time of the crash

Crashlytics **does not collect** your study notes, images, or any content from your database.

**Privacy policy:** https://policies.google.com/privacy

---

## 14. Text-to-Speech

The TTS feature uses your device's installed **system TTS engine** (e.g. Google Text-to-Speech). Audio is synthesized entirely on-device. This app does not use the microphone or record audio input in any form.

---

## 15. Screen Capture Protection

Raphael Sensei blocks screenshots and screen recordings system-wide using Android's `FLAG_SECURE` flag, applied on app launch by the freeRASP security SDK. This means:

- You will not be able to take a screenshot of the app from outside (e.g. via the power button shortcut or another app).
- Screen recording tools will show a black frame while Raphael Sensei is in the foreground.

This is a deliberate security measure to protect your study content. It applies to the entire app and cannot be toggled by the user.

---

## 16. Children's Privacy

Raphael Sensei is rated for users aged **16 and above** in the Google Play Console and is not directed at children. We do not knowingly collect personal information from anyone under 16. The advertising SDKs used in this app (see Section 12) are configured for a general audience under this age restriction. If you believe a user under 16 is using this app, please contact us at **dev.himchita@gmail.com**.

---

## 17. Data Security

| Layer | Protection |
|---|---|
| Local database | Plain SQLite — stored in app private storage, inaccessible to other apps without root |
| JWT & subscription status | Stored in Android hardware-backed Keystore (encrypted shared preferences) |
| Backup files | Unencrypted ZIP — stored only in the folder you choose; protect that folder if needed |
| Network transmission | All communication with Firebase, the security backend, and ad networks occurs over HTTPS |
| Screen capture | Blocked system-wide by `FLAG_SECURE` (freeRASP) |

We do not operate any servers that store your personal data or study content.

---

## 18. Changes to This Policy

We may update this policy as new features are added. The "Last updated" date at the top will reflect any changes. Continued use of the app after changes constitutes acceptance of the updated policy. Significant changes will also be noted in the Play Store update description.

---

## 19. Data Deletion

All study notes, PDFs, videos, images and app settings are stored **locally on your device only**. You can delete all app data at any time by:

- **Uninstalling the app** — removes all local data permanently
- **Clearing app data** — Settings → Apps → Raphael Sensei → Storage → Clear Data

For data collected by third-party SDKs:

| Data | Retention | How to delete |
|---|---|---|
| **Crash logs** (Firebase Crashlytics) | Automatically deleted within 90 days | Contact us to request earlier deletion |
| **Device/Advertising ID** (AdMob) | Managed by Google | Settings → Google → Ads → Delete Advertising ID |
| **Security incident reports** (freeRASP/Talsec) | Reports are sent only when a specific threat is detected (e.g. root, tamper, hook) — not continuously. We have no visibility into Talsec's server-side retention period; see their policy for details. | Contact Talsec at https://www.talsec.app/privacy-policy |

To request deletion of any data associated with your device, contact us at: **dev.himchita@gmail.com**

We will respond to deletion requests within 30 days.

---

## 20. Contact

For privacy-related questions or requests, please contact the developer through the **Raphael Sensei Play Store listing page** or at **dev.himchita@gmail.com**.

---

*This privacy policy covers the Android version of Raphael Sensei (com.himadri.raphael_sensei).*

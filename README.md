# Bing Chilling — Edge Camoufox Automator

Bing Chilling is a stealthy, multi-account automation manager designed to help you securely cycle through multiple Bing Rewards accounts without triggering Microsoft's bot detection systems. 

It leverages the **Camoufox** browser engine for native C++ fingerprint spoofing and integrates directly with Android **ADB** to rotate your IP address via cellular data airplane mode toggling.

---

## 🚀 Key Features

- **Anti-Detection Browser:** Uses `AsyncCamoufox` to spoof your OS, block WebRTC, match GeoIP, and humanize cursor movement, keeping you under the radar.
- **Automated IP Rotation:** Automatically toggles airplane mode on your tethered Android phone via ADB to fetch a fresh CGNAT IP before opening a new account.
- **Background Cooldown Timer:** Built-in randomized 20–60 minute timer enforces safe account cycling. The timer runs in the background (System Tray) and notifies you via Windows Toast Notifications when it's safe to continue.
- **Credential Storage:** Securely store your emails and passwords inside the app for quick reference.
- **Progress Tracking:** Check off accounts as "Done" to keep track of your daily progress.

---

## ⚙️ Initial Setup

### 1. Phone & Network Setup (REQUIRED for IP Rotation)
You must use a specific Android + PC tethering configuration to safely rotate IPs without getting flagged.
1. **Cellular Data Only**: Ensure your phone is using a 4G/5G cellular network (Turn Wi-Fi OFF).
2. **Physical Connection**: Connect your Android phone to your PC via a USB cable.
3. **USB Debugging**: Go to Developer Options on your phone and turn on **USB Debugging**.
4. **USB Tethering**: Go to your phone's network settings and enable **USB Tethering**.
5. **Every Proxy**: Install the *Every Proxy* app on your Android phone and turn on the **HTTP Proxy** (Port 8080).
6. **Find Ethernet Name**: On your PC, press `Win + R`, type `ncpa.cpl`, and hit Enter. Find the newly created network adapter (usually listed as an NDIS compatible device, e.g., `Ethernet 3`). Note this name down.
7. **Keep Screen Awake**: Your phone screen must remain ON (unlocked/awake) AND the *Every Proxy* app must remain open on the screen (not in the background) while using the app, otherwise Android may block the proxy connection and ADB toggles.

### 2. App Configuration
When you launch the app:
1. Under **Settings**, click `⟳` to scan for connected ADB devices. 
2. Open the dropdown and **choose your specific ADB Device**. This is crucial if you have other Android emulators running on your PC.
3. Enter the exact name of your USB tethering adapter (from step 6 above) into the **Ethernet** box.
4. *(Optional but Recommended):* Go back to `ncpa.cpl`, right-click your Ethernet tethering adapter -> Properties -> IPv4 -> Advanced. Uncheck "Automatic metric" and type `9999`. This forces Windows to prioritize your Wi-Fi, leaving the tethering adapter *exclusively* for Camoufox.
5. *Note: These settings save automatically.*

---

## 📖 How to Use the App

### Managing Profiles
1. Use the dropdown to select **"-- Create New Profile --"** to add an account. 
2. Click **Credentials** next to a profile to securely store its Microsoft email and password.
3. Every profile maintains its own separate browser cache and cookies, meaning you only need to log in once!

### Daily Workflow
1. Click the name of the account you want to run.
2. The app will automatically execute the ADB airplane mode toggle to get a new IP address.
3. The app will verify your new IP in the background (without leaving a browser trace).
4. A stealthy Camoufox browser will open directly to `bing.com`. Perform your tasks manually.
5. **Close the browser** when finished.

### Cooldown Timer
For your account's safety, running accounts back-to-back will trigger detection. 
- The moment you close the browser, a **random 20–60 minute countdown** will automatically start.
- During this time, the account list is locked. 
- You can safely click the `X` on the window to minimize the app to your **System Tray**. The timer will keep ticking.
- Once the cooldown is finished, a Windows Notification will pop up and chime, letting you know it's time for the next account.

### Tracking Progress
- Click the checkbox next to an account to mark it as **Done** for the day.
- At the end of the day, click **Clear Done Marks** to reset.

---

## ⚠️ Safety Warning
- **Never use a VPN.** Microsoft strictly bans VPNs for Rewards.
- **Do not bypass the timer.** Sequential logins from the same cellular subnet are the #1 cause of account suspensions.
- **Unique Phone Numbers.** Ensure none of your accounts share a phone number for SMS verification.

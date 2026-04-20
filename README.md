# Bing Chilling — Edge Camoufox Automator

Bing Chilling is a stealthy, multi-account automation manager designed to help you securely cycle through multiple Bing Rewards accounts without triggering Microsoft's bot detection systems. 

It leverages the **Camoufox** browser engine for native C++ fingerprint spoofing and integrates directly with Android **ADB** to rotate your IP address via cellular data airplane mode toggling.

---

## 🚀 Key Features

- **Anti-Detection Browser:** Uses `AsyncCamoufox` to spoof your OS, block WebRTC, match GeoIP, and humanize cursor movement, keeping you under the radar.
- **Automated IP Rotation:** Automatically toggles airplane mode on your tethered Android phone via ADB to fetch a fresh CGNAT IP before opening a new account.
- **Background Cooldown Timer:** Built-in randomized 20–60 minute timer enforces safe account cycling. The timer runs in the background (System Tray) and notifies you via Windows Toast Notifications when it's safe to continue.
- **Progress Tracking:** Check off accounts as "Done" to keep track of your daily progress.

---

## ⚙️ Initial Setup

### 1. Phone Setup (REQUIRED for IP Rotation)
You must use a specific Android + PC tethering configuration to safely rotate IPs without getting flagged.
1. **Cellular Data Only**: Ensure your phone is using a 4G/5G cellular network (Turn Wi-Fi OFF).
2. **Physical Connection**: Connect your Android phone to your PC via a USB cable.
3. **USB Debugging**: Go to Developer Options on your phone and turn on **USB Debugging**.
4. **Every Proxy**: Install the *Every Proxy* app on your Android phone and turn on the **HTTP Proxy** (Port 8080).

### 2. App Configuration (Fully Automated!)
When you launch the app:
1. Under **Settings**, click `⟳` to scan for connected ADB devices. 
2. Open the dropdown and **choose your specific ADB Device**.
3. **Auto-Configuration**: The app will immediately turn on USB Tethering on your phone, find your tethered Ethernet adapter on Windows, and automatically configure its interface metric to `9999` to ensure your Wi-Fi is prioritized!
4. *(Note: You will get a User Account Control (UAC) prompt to allow the app to change the network metric. This is required for safety).*

---

## 📖 How to Use the App

### Managing Profiles
1. Use the dropdown to select **"-- Create New Profile --"** to add an account. 
2. Every profile maintains its own separate browser cache and cookies, meaning you only need to log in once!

### The Daily Workflow
1. Click the name of the account you want to run.
2. The app will automatically execute the ADB airplane mode toggle to get a new IP address, and pull the Every Proxy app to the foreground on your phone.
3. A warning will appear reminding you to keep Every Proxy in the foreground.
4. The app will verify your new IP in the background (without leaving a browser trace).
5. A stealthy Camoufox browser will open directly to `bing.com`. Perform your tasks manually.
6. **Close the browser** when finished.

### The Cooldown Timer
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
- **Keep Every Proxy on foreground while doing tasks**

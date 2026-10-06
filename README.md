# BYD Seal U DMi ADB Unlock and Sideloading Guide

A step by step guide to unlocking ADB and enabling direct APK installation from USB drives on the BYD Seal U DMi infotainment system.

---

> [!WARNING]
> **Firmware 2602 Downgrade Limitation**
> If your vehicle is on firmware version 2602, attempting to downgrade to an older release will not work. The update progress bar runs for approximately thirty seconds before the system restarts straight back into version 2602. Most guides floating around the web were written for the standard Seal rather than the Seal U DMi. Follow the process below rather than attempting firmware rollbacks.

---

## Remote Service Details

The remote unlock process requires an authorization token provided via Telegram.

* **Contact:** `@bydadb_open` on Telegram
* **Operating Hours:** 08:30 to 23:30 Beijing Time (UTC+8)
* Contact the provider ahead of time so they are ready before you generate your QR code, as the code will expire quickly once displayed.

---

## Prerequisites

* Android smartphone with **Bugjaeger** installed from Google Play.
* `PackageInstallerUnlocker.apk` saved locally on your Android phone storage.
* Shared Wi Fi network (both the car and your phone connected to the same wireless router or mobile hotspot).
* USB flash drive formatted to FAT32 or NTFS containing the APK files you plan to install.
* Active Bluetooth link between your phone and the car.

---

## Step 1: Generate the Unlock QR Code

1. Connect your mobile phone to the vehicle multimedia system via Bluetooth.
2. Launch the standard **Phone** application on the vehicle centre screen.
3. Dial the diagnostic sequence:

```text
*#91532547#*
```

4. An engineering window displaying a unique QR code will appear on screen. This QR code remains valid for roughly five minutes.

---

## Step 2: Remote Unlock and ADB Activation

1. Take a clear photograph of the QR code shown on the car screen.
2. Send the photograph immediately to `@bydadb_open` on Telegram.
3. Once the provider authorizes the request remotely, the vehicle display will automatically refresh and show an engineering test interface.
4. From the menu list, tap **Test Tools**.
5. Scroll all the way down to the bottom of the page and enable both toggles:
   * **Wireless adb debug switch**
   * **Debug mode when USB is connected**

> [!CAUTION]
> **DO NOT** press or touch **Revoke USB debugging authorisations**. Doing so will immediately wipe access permissions.

---

## Step 3: Retrieve the Vehicle IP Address

1. Verify that your vehicle is connected to the same Wi Fi network or hotspot as your Android handset.
2. Open **Settings** on the car screen and navigate to **Wi Fi**.
3. Tap the small information icon (**i**) next to your active network name.
4. Record the displayed IPv4 address (for example `192.168.1.150`).

---

## Step 4: Install PackageInstallerUnlocker via Bugjaeger

The native BYD system blocks direct installation attempts from external USB storage. You must install `PackageInstallerUnlocker.apk` over ADB first to bypass this restriction.

1. Open **Bugjaeger** on your Android smartphone.
2. Tap the **Connect** icon (the plug symbol) in the top toolbar.
3. Enter the vehicle IP address alongside the ADB port:

```text
CAR_IP_ADDRESS:5555
```

4. Tap **Connect**.
5. Look at the car centre display. A prompt requesting USB debugging permission will appear. Tap **Allow** (optionally tick the option to always permit connections from this device).
6. Return to Bugjaeger and open the **Packages** tab (the box/cube icon).
7. Tap the **+** (Add) icon in the top toolbar, then select **Select APK file**.
8. Browse your device storage and select `PackageInstallerUnlocker.apk`.
9. Bugjaeger will transfer and install the package within a couple of seconds, displaying a success confirmation upon completion.

---

## Step 5: Sideload APKs from USB

1. Insert your USB flash drive with your desired APKs into the vehicle front data port.
2. Open the onboard BYD **File Manager** app on the central display.
3. Select your USB drive, locate your APK files, and tap them to install.
4. The system will now allow standard installation without being blocked by the stock package manager.

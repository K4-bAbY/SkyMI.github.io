# SkyMI Kernel Detailed Installation Guide

This guide provides detailed steps to help you safely flash the SkyMI Kernel. Please read and follow each step carefully.

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Preparation](#preparation)
3. [Unlock Bootloader](#unlock-bootloader)
4. [Install Recovery](#install-recovery)
5. [Flash Kernel](#flash-kernel)
6. [Verify Installation](#verify-installation)
7. [Troubleshooting](#troubleshooting)

---

## Prerequisites

Before you begin, ensure you have the following:

### Hardware Requirements
- **Supported Device**: Xiaomi Redmi 12 5G (Codename: `sky`)
- **USB Cable**: For connecting your device to your computer
- **Computer**: Windows, macOS, or Linux
- **Sufficient Battery**: At least 50% battery life

### Software Requirements
- **ADB and Fastboot**: Android debugging tools
- **Custom Recovery**: TWRP or OrangeFox
- **SkyMI Kernel ZIP Package**: Downloaded from official channels

### Knowledge Requirements
- Basic command-line operation knowledge
- Understanding of the risks involved in flashing

---

## Preparation

### Step 1: Back Up Data

**This is the most important step!** Unlocking the Bootloader will erase all data.

1. **Back up to Cloud Services**:
   - Use Google Account to sync data
   - Use Xiaomi Cloud backup
   - Use other cloud storage services

2. **Back up to Computer**:
   - Use ADB to back up apps and data
   - Copy photos, videos, documents, etc.

3. **Record Important Information**:
   - Save app lists and settings
   - Record WiFi passwords
   - Save account information

### Step 2: Enable Developer Options

1. Go to **Settings** → **About Phone**
2. Tap **Build Number** 7 times consecutively
3. Go back to Settings, enter **System & Device** → **Developer Options**
4. Enable the following options:
   - **USB Debugging**
   - **OEM Unlocking** (if available)

### Step 3: Install ADB and Fastboot

#### Windows
1. Download [Android SDK Platform Tools](https://developer.android.com/studio/releases/platform-tools)
2. Extract to `C:\adb` or another directory
3. Add the directory to your system PATH

#### macOS
```bash
brew install android-platform-tools
```

#### Linux
```bash
sudo apt-get install android-tools-adb android-tools-fastboot
```

### Step 4: Verify ADB Connection

1. Connect your device to your computer
2. Allow USB debugging on your device
3. Execute on your computer:
```bash
adb devices
```
4. If you see your device listed, the connection is successful.

---

## Unlock Bootloader

### ⚠️ Important Warning
Unlocking the Bootloader will:
- **Erase all data** (including apps, settings, files)
- **Affect warranty** (may void official warranty)
- **Require a Xiaomi Account** (bound to your device)

### Unlocking Steps

1. **Enter Fastboot Mode**:
```bash
adb reboot bootloader
```

2. **Verify Fastboot Connection**:
```bash
fastboot devices
```

3. **Unlock Bootloader**:
```bash
fastboot flashing unlock
```

4. **Confirm Unlock**:
   - Press the volume key on your device to confirm
   - The device will reboot and erase data

5. **Wait for Completion**:
   - The device will automatically reboot
   - The first boot may take a long time

### Verify Unlock

1. Go to **Settings** → **About Phone**
2. Check if "Bootloader Unlocked" is displayed

---

## Install Recovery

### Choose Recovery

Recommended options:
- **TWRP** (Team Win Recovery Project): Full-featured, widely used
- **OrangeFox Recovery**: Based on TWRP, more user-friendly interface

### Install TWRP

1. **Download TWRP Image**:
   - Visit the [TWRP Official Website](https://twrp.me/)
   - Download the image for Redmi 12 5G

2. **Enter Fastboot Mode**:
```bash
adb reboot bootloader
```

3. **Flash Recovery**:
```bash
fastboot flash recovery twrp-xxx.img
```

4. **Enter Recovery**:
   - Press and hold Volume Down + Power button
   - Select Recovery in the Fastboot menu

### Verify Recovery Installation

1. Enter Recovery mode
2. Check Recovery version information
3. Ensure it displays TWRP or OrangeFox

---

## Flash Kernel

### Step 1: Prepare Kernel File

1. **Download SkyMI Kernel**:
   - Obtain the latest version from official channels
   - Ensure it matches your Android version

2. **Verify File Integrity**:
```bash
# Windows
certutil -hashfile SkyMI-kernel.zip SHA256

# macOS/Linux
sha256sum SkyMI-kernel.zip
```

3. **Copy to Device**:
```bash
adb push SkyMI-kernel.zip /sdcard/
```

### Step 2: Enter Recovery

1. Turn off the device
2. Press and hold **Volume Down** + **Power button**
3. Enter Recovery mode

### Step 3: Back Up Original Partitions

**Highly Recommended!** This allows you to restore in case of issues.

1. Select **Backup** in Recovery
2. Select the following partitions:
   - Boot
   - Vendor Boot
   - DTBO
3. Select backup location (Internal Storage or External SD Card)
4. Start backup

### Step 4: Flash Kernel

1. Select **Install** in Recovery
2. Navigate to the `/sdcard/` directory
3. Select the `SkyMI-kernel.zip` file
4. Swipe right to confirm flashing
5. Wait for flashing to complete

### Step 5: Wipe Cache (Recommended)

1. Return to the Recovery main menu
2. Select **Wipe**
3. Select **Dalvik/ART Cache** and **Cache**
4. Swipe right to confirm wiping

### Step 6: Reboot System

1. Select **Reboot**
2. Select **System**
3. Wait for the device to boot

---

## Verify Installation

### Method 1: System Settings

1. Go to **Settings** → **About Phone**
2. Check the **Kernel Version** field
3. It should display the SkyMI Kernel version

### Method 2: ADB Command

```bash
adb shell uname -a
```

The output should contain "SkyMI" or related kernel identifiers.

### Method 3: Terminal App

1. Open a terminal app on your device
2. Execute the command:
```bash
uname -a
```

### Method 4: System Info App

Use a third-party system info app (e.g., CPU-Z) to view kernel information.

---

## Troubleshooting

### Issue 1: Device Won't Boot

**Symptom**: Device stuck on the boot screen after flashing

**Solution**:
1. Enter Recovery mode
2. Wipe Dalvik/Cache
3. Reboot system
4. If it still won't boot, restore the original Boot partition

### Issue 2: Cannot Enter Recovery

**Symptom**: Key combination fails to enter Recovery

**Solution**:
1. Try using ADB command: `adb reboot recovery`
2. Ensure USB debugging is enabled
3. Reinstall ADB drivers

### Issue 3: Flashing Failed

**Symptom**: Recovery displays a flashing failure error

**Solution**:
1. Verify ZIP file integrity
2. Wipe Cache and try again
3. Try using a different Recovery version
4. Check if device storage is sufficient

### Issue 4: Performance Issues

**Symptom**: Device slow or laggy after flashing

**Solution**:
1. Clear app cache: Settings → Apps → Storage → Clear Cache
2. Wipe Dalvik/Cache: Perform in Recovery
3. Reboot device
4. Check background running apps

### Issue 5: Excessive Heat

**Symptom**: Device abnormally hot

**Solution**:
1. Check CPU usage
2. Close unnecessary apps
3. Clear app cache
4. If the issue persists, restore the official kernel

---

## Restore to Official Kernel

If you want to go back to the official kernel, follow these steps:

1. **Enter Recovery**: Press Volume Down + Power button

2. **Restore Backup**:
   - Select **Restore**
   - Select the Boot partition you backed up earlier
   - Confirm restoration

3. **Reboot System**:
   - Select **Reboot** → **System**

4. **Verify**:
   - Check if the kernel version has returned to the official version

---

## Get Help

If you encounter issues during installation:

1. **Check FAQ**: [FAQ_EN.md](FAQ_EN.md)
2. **GitHub Issues**: Submit an issue and get community help
3. **Community Forums**: Discuss with other users
4. **Official Channels**: Contact project developers

---

## Safety Recommendations

- ✅ Always download kernel from official channels
- ✅ Verify file SHA256 checksum
- ✅ Perform a full data backup before flashing
- ✅ Keep a backup of the original Boot partition
- ✅ Update to the latest version regularly
- ✅ Do not flash in an unstable network environment
- ✅ Ensure device has sufficient battery

---

*Last Updated: March 2026*

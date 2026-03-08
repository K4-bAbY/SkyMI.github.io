# Frequently Asked Questions (FAQ)

## Installation & Compatibility

### Q: Does my device support SkyMI Kernel?
**A:** Currently, SkyMI Kernel primarily supports Xiaomi Redmi 12 5G (Codename: `sky`). We are gradually expanding support for other devices. Please check project updates regularly for the latest support list.

### Q: How can I confirm if my device is Redmi 12 5G?
**A:** 
1. Go to **Settings** → **About Phone** → **Device Name**
2. Check if the device codename is `sky`
3. Or execute in ADB: `adb shell getprop ro.product.device`

### Q: Can devices with different Android versions use the same kernel?
**A:** No. SkyMI Kernel is optimized for specific Android versions. Ensure you download the kernel version that matches your device's Android version.

---

## Flashing Process

### Q: What preparation is needed before flashing?
**A:** 
1. **Back Up Data**: Full backup of your device data (photos, files, apps, etc.)
2. **Unlock Bootloader**: If not already unlocked, unlock it first
3. **Install Recovery**: Install TWRP or OrangeFox Recovery
4. **Download Kernel**: Obtain the latest SkyMI Kernel ZIP package from official channels
5. **Verify File**: Check the SHA256 checksum to ensure file integrity

### Q: What happens when I unlock the Bootloader?
**A:** Unlocking the Bootloader will:
- Erase all data on the device (including apps, settings, files, etc.)
- Allow you to flash custom Recovery and kernels
- Potentially affect device warranty

**Warning**: Back up all important data before unlocking.

### Q: How do I enter Recovery mode?
**A:** 
1. Turn off the device
2. Simultaneously press **Volume Down** + **Power button**
3. After entering Fastboot mode, select the Recovery option
4. Or execute in ADB: `adb reboot recovery`

### Q: What if the device loses power during flashing?
**A:** This may lead to device bricking. If this happens:
1. Connect to power
2. Enter Recovery mode
3. Try reflashing the kernel
4. If the issue persists, seek professional help or contact the community

### Q: How long does the first boot take after flashing?
**A:** The first boot may take 5-10 minutes. This is normal as the system optimizes apps. Please wait patiently and do not interrupt the process.

---

## Post-Flashing Issues

### Q: What if the device won't boot after flashing?
**A:** 
1. **Enter Recovery**: Press Volume Down + Power button
2. **Wipe Cache**: Select Wipe Dalvik/Cache in Recovery
3. **Reboot System**: Select Reboot System
4. **If it still won't boot**:
   - Enter Recovery
   - Flash the official Boot image to restore
   - Or reflash SkyMI Kernel

### Q: How do I verify if the kernel was successfully flashed?
**A:** 
1. **In System**: Settings → About Phone, check the kernel version
2. **Using ADB**: Execute `adb shell uname -a`
3. **Using Terminal App**: Open a terminal on the device, execute `uname -a`

### Q: Performance hasn't improved after flashing, what should I do?
**A:** 
1. **Wipe Cache**: Enter Recovery and wipe Dalvik/Cache
2. **Reboot Device**: Restart after a full shutdown
3. **Wait for Optimization**: The system needs time to optimize apps
4. **Check Settings**: Ensure no unnecessary features are enabled
5. **Check Logs**: Use logcat to check for errors

### Q: Does the kernel cause the device to heat up?
**A:** SkyMI Kernel is optimized and should not cause excessive heating. If you find the device abnormally hot:
1. Check for background apps consuming CPU
2. Clear app cache
3. Wipe Dalvik/Cache in Recovery
4. If the issue persists, consider reverting to the official kernel

---

## Features & Performance

### Q: What performance improvements does SkyMI Kernel provide?
**A:** SkyMI Kernel provides the following improvements:
- **CPU Scheduling Optimization**: Faster task response
- **I/O Optimization**: Faster app launches and data loading
- **Memory Optimization**: Better multitasking
- **Power Optimization**: Longer battery life

### Q: Does the kernel support overclocking?
**A:** SkyMI Kernel itself does not include overclocking features, but you can use third-party tools (e.g., Kernel Adiutor) to adjust CPU frequencies. Please operate with caution to avoid device damage.

### Q: Can I customize kernel parameters?
**A:** Yes, SkyMI Kernel provides several adjustable parameters. You can use the following tools:
- **Kernel Adiutor**: Graphical interface
- **Termux**: Command-line tool
- **Settings App**: Some parameters can be adjusted in system settings

### Q: Does the kernel affect gaming performance?
**A:** SkyMI Kernel optimizations should improve gaming performance, including:
- Lower frame rate fluctuations
- Faster loading times
- More stable frame rates

---

## Reverting & Recovery

### Q: How do I revert to the official kernel?
**A:** 
1. **Enter Recovery**: Press Volume Down + Power button
2. **Flash Official Boot Image**: Select the original Boot partition you backed up
3. **Reboot System**: The system will boot using the official kernel

### Q: What if I didn't back up the original Boot partition?
**A:** 
1. Download the official ROM for your device from the Xiaomi official website
2. Extract the Boot image from the ROM
3. Flash the image in Recovery

### Q: Does reverting delete data?
**A:** Flashing only the Boot image will not delete data. However, for safety, it's recommended to back up data before flashing.

---

## Warranty & Safety

### Q: Does flashing SkyMI Kernel affect the warranty?
**A:** This depends on your device manufacturer's warranty policy. Generally:
- Flashing a custom kernel may affect the official warranty
- Xiaomi may refuse warranty service for devices with custom kernels
- You can restore warranty eligibility by flashing the official kernel

### Q: Is SkyMI Kernel safe?
**A:** SkyMI Kernel is based on the official Linux LTS kernel and regularly merges upstream security patches. However, as with any custom software, there are risks. Please:
- Only download kernel from official channels
- Verify file integrity
- Update to the latest version regularly

### Q: How do I report security issues?
**A:** If you find a security vulnerability, please:
1. Do not discuss it in public channels
2. Contact the developer via GitHub private issues or email
3. Provide a detailed vulnerability description and reproduction steps

---

## Community & Support

### Q: How do I get technical support?
**A:** 
1. **GitHub Issues**: Report bugs and ask questions
2. **Community Forums**: Discuss with other users
3. **Social Media**: Follow official accounts for the latest information

### Q: How do I contribute code or documentation?
**A:** Please see [CONTRIBUTING_EN.md](CONTRIBUTING_EN.md) for detailed steps.

### Q: How often is the project updated?
**A:** Update frequency depends on development progress and community feedback. Please follow the GitHub repository for the latest updates.

---

## Other Questions

### Q: Which Android versions does SkyMI Kernel support?
**A:** Currently supports Android 13 and Android 14. We are working on adaptations for other versions.

### Q: Where is the kernel source code?
**A:** The kernel source code may be hosted in a separate repository. Please check the project homepage or contact the developer for details.

### Q: How do I get the latest information on the kernel?
**A:** 
1. **Star this repository**: Get update notifications
2. **Watch this repository**: Receive all activity notifications
3. **Follow the developer**: Get the latest updates

---

## Still Have Questions?

If your question is not listed here, please:
1. Raise it in [GitHub Issues](https://github.com/K4-bAbY/SkyMI.github.io/issues)
2. Seek help in community forums
3. Contact the developer through official channels

---

*Last Updated: March 2026*

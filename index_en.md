# SkyMI Android Kernel Project

## Welcome

Welcome to the **SkyMI Android Kernel Project**! This is an open-source project dedicated to providing optimized, stable, and high-performance kernels for compatible Android devices.

SkyMI Kernel is based on the Linux LTS kernel and integrates several performance optimizations, power management, and stability enhancements to bring a smoother user experience to your device.

---

## Quick Navigation

| Link | Description |
|------|-------------|
| [Project Overview](#project-overview) | Learn about the core features of SkyMI Kernel |
| [Supported Devices](#supported-devices) | View the list of compatible devices |
| [Flashing Guide](#flashing-guide) | Learn how to safely flash the kernel |
| [FAQ](FAQ_EN.md) | Get answers to common questions |
| [Contribution Guide](CONTRIBUTING_EN.md) | Participate in project development |
| [Changelog](CHANGELOG_EN.md) | View version update history |
| [中文版本](index.md) | Switch to Chinese version |

---

## Project Overview

### Core Features

SkyMI Kernel provides the following optimizations and features:

#### 🚀 Performance Optimizations
- **CPU Scheduler Optimization**: Uses EAS (Energy-Aware Scheduling) and PELT optimizations for faster task response.
- **I/O Optimization**: Integrates efficient I/O schedulers (FIOPS, Maple) to accelerate app launches and data loading.
- **Memory Management**: Optimizes ZRAM/ZSWAP configurations to improve multitasking capabilities.

#### 🔋 Battery Life Enhancements
- **Power Management**: Fine-tuned CPU/GPU frequency control to optimize idle state power consumption.
- **Wakeup Management**: Reduces unnecessary wakeup sources to prevent background app battery drain.

#### 🛡️ Stability & Compatibility
- **Upstream Merges**: Regularly merges the latest patches from the Linux LTS kernel to ensure security.
- **Platform Compatibility**: Optimized for specific Android versions.

#### ⚙️ Additional Features
- **Fast Charge Support**: Optimized support for fast charging protocols.
- **Custom Tuning**: Provides kernel parameter tuning options.

---

## Supported Devices

Currently, SkyMI Kernel primarily supports the following devices:

| Device Name | Codename | Android Version | Status |
|-------------|----------|-----------------|--------|
| Xiaomi Redmi 12 5G | `sky` | 13/14 | ✅ Supported |

**Note**: Please confirm your device model and kernel version are compatible before flashing.

---

## Flashing Guide

### ⚠️ Important Warning

Flashing a custom kernel carries risks and may lead to device bricking or data loss. Please ensure you:
- Back up your device data.
- Understand every step of the flashing process.
- Are able to restore the official Boot image if issues occur.

### Flashing Steps

1. **Unlock Bootloader**
   - Your device must have an unlocked bootloader.
   - Unlocking will erase device data.

2. **Install Custom Recovery**
   - Recommended to use TWRP or OrangeFox Recovery.
   - Ensure the Recovery version is compatible with your device.

3. **Download Kernel Package**
   - Obtain the latest SkyMI Kernel ZIP package from official release channels.
   - Verify the SHA256 checksum to ensure integrity.

4. **Enter Recovery Mode**
   - Turn off the device.
   - Press and hold the specific key combination (usually Volume Down + Power button).

5. **Backup Partitions**
   - Back up `Boot`, `Vendor Boot`, and `DTBO` partitions in Recovery.
   - Export backup files to a safe location.

6. **Flash Kernel**
   - Select the downloaded kernel ZIP package and flash it.
   - Wait for the flashing to complete.

7. **Wipe Cache (Optional but Recommended)**
   - Wipe Dalvik/Cache after flashing.
   - This helps avoid boot issues.

8. **Reboot System**
   - Reboot your device into the system.
   - The first boot may take a long time.

For more details, see the [Detailed Installation Guide](INSTALLATION_EN.md).

---

## FAQ

### Q: Does my device support SkyMI Kernel?
**A:** Currently, it primarily supports Xiaomi Redmi 12 5G (sky). Please follow project updates for the latest support list.

### Q: What should I do if I encounter issues after flashing?
**A:** 
- Try reflashing the official boot image.
- Check logcat logs to diagnose the issue.
- Seek help in relevant community forums or GitHub Issues.

For more questions, see [FAQ_EN.md](FAQ_EN.md).

---

## Contribution

The SkyMI Kernel project welcomes community contributions! You can participate by:

- **Submitting Bug Reports**: Report issues you find in GitHub Issues.
- **Providing Feedback**: Share your user experience and improvement suggestions.
- **Improving Documentation**: Help us refine project documentation.
- **Contributing Code**: Submit code patches and new features.

See the [Contribution Guide](CONTRIBUTING_EN.md) for details.

---

## License

The SkyMI Kernel project follows an open-source license. See the [LICENSE](LICENSE) file for specific license information.

---

## Acknowledgments

Thanks to all developers, testers, and users who contribute to the Android open-source community!

---

## Contact

- **GitHub Issues**: For reporting bugs and feature suggestions.
- **Community Forums**: For community support and discussion.

---

*Last Updated: March 2026*

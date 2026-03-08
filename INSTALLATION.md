# SkyMI 内核详细安装指南

本指南提供了详细的步骤，帮助您安全地刷入 SkyMI 内核。请仔细阅读并遵循每一步。

## 目录

1. [前置要求](#前置要求)
2. [准备工作](#准备工作)
3. [解锁 Bootloader](#解锁-bootloader)
4. [安装 Recovery](#安装-recovery)
5. [刷入内核](#刷入内核)
6. [验证安装](#验证安装)
7. [故障排除](#故障排除)

---

## 前置要求

在开始之前，请确保您拥有以下条件：

### 硬件要求
- **支持的设备**：Xiaomi Redmi 12 5G (代号: `sky`)
- **USB 数据线**：用于连接设备和电脑
- **电脑**：Windows、macOS 或 Linux
- **充足电量**：设备电量至少 50%

### 软件要求
- **ADB 和 Fastboot**：Android 调试工具
- **自定义 Recovery**：TWRP 或 OrangeFox
- **SkyMI 内核 ZIP 包**：从官方渠道下载

### 知识要求
- 基本的命令行操作知识
- 理解刷入过程中的风险

---

## 准备工作

### 步骤 1: 备份数据

**这是最重要的一步！** 解锁 Bootloader 会清除所有数据。

1. **备份到云服务**：
   - 使用 Google 账户同步数据
   - 使用小米云服务备份
   - 使用其他云存储服务

2. **备份到电脑**：
   - 使用 ADB 备份应用和数据
   - 复制照片、视频、文档等文件

3. **记录重要信息**：
   - 保存应用列表和设置
   - 记录 WiFi 密码
   - 保存账户信息

### 步骤 2: 启用开发者选项

1. 进入 **设置** → **关于手机**
2. 连续点击 **版本号** 7 次
3. 返回设置，进入 **系统和设备** → **开发者选项**
4. 启用以下选项：
   - **USB 调试**
   - **OEM 解锁**（如果可用）

### 步骤 3: 安装 ADB 和 Fastboot

#### Windows
1. 下载 [Android SDK Platform Tools](https://developer.android.com/studio/releases/platform-tools)
2. 解压到 `C:\adb` 或其他目录
3. 将该目录添加到系统 PATH

#### macOS
```bash
brew install android-platform-tools
```

#### Linux
```bash
sudo apt-get install android-tools-adb android-tools-fastboot
```

### 步骤 4: 验证 ADB 连接

1. 连接设备到电脑
2. 在设备上允许 USB 调试
3. 在电脑上执行：
```bash
adb devices
```
4. 如果看到设备列表，说明连接成功

---

## 解锁 Bootloader

### ⚠️ 重要警告
解锁 Bootloader 会：
- **清除所有数据**（包括应用、设置、文件）
- **影响保修**（可能无法获得官方保修）
- **需要 Xiaomi 账户**（绑定到您的设备）

### 解锁步骤

1. **进入 Fastboot 模式**：
```bash
adb reboot bootloader
```

2. **验证 Fastboot 连接**：
```bash
fastboot devices
```

3. **解锁 Bootloader**：
```bash
fastboot flashing unlock
```

4. **确认解锁**：
   - 在设备屏幕上按音量键确认
   - 设备将重启并清除数据

5. **等待完成**：
   - 设备会自动重启
   - 首次启动可能需要较长时间

### 验证解锁

1. 进入 **设置** → **关于手机**
2. 查看是否显示 "Bootloader 已解锁"

---

## 安装 Recovery

### 选择 Recovery

推荐使用以下之一：
- **TWRP** (Team Win Recovery Project)：功能完整，使用广泛
- **OrangeFox Recovery**：基于 TWRP，界面更友好

### 安装 TWRP

1. **下载 TWRP 镜像**：
   - 访问 [TWRP 官网](https://twrp.me/)
   - 下载适用于 Redmi 12 5G 的镜像

2. **进入 Fastboot 模式**：
```bash
adb reboot bootloader
```

3. **刷入 Recovery**：
```bash
fastboot flash recovery twrp-xxx.img
```

4. **进入 Recovery**：
   - 按住音量减键 + 电源键
   - 在 Fastboot 菜单中选择 Recovery

### 验证 Recovery 安装

1. 进入 Recovery 模式
2. 查看 Recovery 版本信息
3. 确保显示为 TWRP 或 OrangeFox

---

## 刷入内核

### 步骤 1: 准备内核文件

1. **下载 SkyMI 内核**：
   - 从官方渠道获取最新版本
   - 确保与您的 Android 版本匹配

2. **验证文件完整性**：
```bash
# Windows
certutil -hashfile SkyMI-kernel.zip SHA256

# macOS/Linux
sha256sum SkyMI-kernel.zip
```

3. **复制到设备**：
```bash
adb push SkyMI-kernel.zip /sdcard/
```

### 步骤 2: 进入 Recovery

1. 关闭设备
2. 按住 **音量减键** + **电源键**
3. 进入 Recovery 模式

### 步骤 3: 备份原始分区

**强烈推荐！** 这样您可以在出现问题时恢复。

1. 在 Recovery 中选择 **Backup**
2. 选择以下分区：
   - Boot
   - Vendor Boot
   - DTBO
3. 选择备份位置（内部存储或外部 SD 卡）
4. 开始备份

### 步骤 4: 刷入内核

1. 在 Recovery 中选择 **Install**
2. 导航到 `/sdcard/` 目录
3. 选择 `SkyMI-kernel.zip` 文件
4. 向右滑动确认刷入
5. 等待刷入完成

### 步骤 5: 清除缓存（推荐）

1. 返回 Recovery 主菜单
2. 选择 **Wipe**
3. 选择 **Dalvik/ART Cache** 和 **Cache**
4. 向右滑动确认清除

### 步骤 6: 重启系统

1. 选择 **Reboot**
2. 选择 **System**
3. 等待设备启动

---

## 验证安装

### 方法 1: 系统设置

1. 进入 **设置** → **关于手机**
2. 查看 **内核版本** 字段
3. 应显示为 SkyMI 内核版本

### 方法 2: ADB 命令

```bash
adb shell uname -a
```

输出应包含 "SkyMI" 或相关内核标识。

### 方法 3: 终端应用

1. 在设备上打开终端应用
2. 执行命令：
```bash
uname -a
```

### 方法 4: 系统信息应用

使用第三方系统信息应用（如 CPU-Z）查看内核信息。

---

## 故障排除

### 问题 1: 设备无法启动

**症状**：刷入后设备卡在启动画面

**解决方案**：
1. 进入 Recovery 模式
2. 清除 Dalvik/Cache
3. 重启系统
4. 如果仍无法启动，恢复原始 Boot 分区

### 问题 2: 无法进入 Recovery

**症状**：按键组合无法进入 Recovery

**解决方案**：
1. 尝试使用 ADB 命令：`adb reboot recovery`
2. 确保 USB 调试已启用
3. 重新安装 ADB 驱动程序

### 问题 3: 刷入失败

**症状**：Recovery 显示刷入失败错误

**解决方案**：
1. 验证 ZIP 文件完整性
2. 清除 Cache 后重试
3. 尝试使用不同的 Recovery 版本
4. 检查设备存储空间是否充足

### 问题 4: 性能问题

**症状**：刷入后设备变慢或卡顿

**解决方案**：
1. 清除应用缓存：设置 → 应用 → 存储 → 清除缓存
2. 清除 Dalvik/Cache：进入 Recovery 执行
3. 重启设备
4. 检查后台运行的应用

### 问题 5: 过度发热

**症状**：设备异常发热

**解决方案**：
1. 检查 CPU 使用率
2. 关闭不必要的应用
3. 清除应用缓存
4. 如果问题持续，恢复官方内核

---

## 回退到官方内核

如果您想回到官方内核，请按照以下步骤：

1. **进入 Recovery**：按住音量减键 + 电源键

2. **恢复备份**：
   - 选择 **Restore**
   - 选择您之前备份的 Boot 分区
   - 确认恢复

3. **重启系统**：
   - 选择 **Reboot** → **System**

4. **验证**：
   - 检查内核版本是否恢复为官方版本

---

## 获取帮助

如果您在安装过程中遇到问题：

1. **查看 FAQ**：[常见问题解答](FAQ.md)
2. **GitHub Issues**：提交问题并获取社区帮助
3. **社区论坛**：与其他用户讨论
4. **官方渠道**：联系项目开发者

---

## 安全建议

- ✅ 始终从官方渠道下载内核
- ✅ 验证文件的 SHA256 校验和
- ✅ 在刷入前完整备份数据
- ✅ 保留原始 Boot 分区的备份
- ✅ 定期更新到最新版本
- ✅ 不要在不稳定的网络环境中刷入
- ✅ 确保设备有充足电量

---

*最后更新：2026 年 3 月*

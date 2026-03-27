# Android Studio安装与配置指南

## 当前状态
- Android Studio已下载完成
- OPPO K9x手机需要开启开发者选项

## 第一部分：安装Android Studio

### 安装步骤
1. **找到下载的文件**
   - 通常在"下载"文件夹或桌面
   - 文件名: `android-studio-2023.3.1.19-windows.exe`（或类似）

2. **运行安装程序**
   - 双击文件运行
   - 如果无法运行，使用管理员命令行：
     ```bash
     cd Downloads
     .\android-studio-2023.3.1.19-windows.exe
     ```

3. **安装过程**
   - 点击"Next"
   - 选择"Standard"安装（推荐）
   - **必须包含**：
     - ✅ Android SDK
     - ✅ Android Virtual Device  
     - ✅ Performance (Intel® HAXM)
   - 使用默认安装路径
   - 完成安装

4. **首次启动配置**
   - 启动Android Studio
   - 选择"Standard"安装类型
   - 选择主题（Light或Dark）
   - 等待SDK组件下载（可能需要10-30分钟）
   - 完成设置

### 环境变量配置
安装完成后，必须配置环境变量：

#### 1. 找到SDK路径
通常路径：
```
C:\Users\Administrator\AppData\Local\Android\Sdk
```

#### 2. 设置ANDROID_HOME
1. 右键"此电脑" → 属性 → 高级系统设置 → 环境变量
2. 系统变量 → 新建
3. **变量名**: `ANDROID_HOME`
4. **变量值**: `C:\Users\Administrator\AppData\Local\Android\Sdk`

#### 3. 添加到Path变量
1. 找到`Path`变量 → 编辑
2. 添加以下路径（每个一行）：
   - `%ANDROID_HOME%\platform-tools`
   - `%ANDROID_HOME%\tools`
   - `%ANDROID_HOME%\tools\bin`

### 验证安装
**重启命令提示符**，输入：
```bash
adb --version
```
应该显示Android Debug Bridge版本信息

## 第二部分：OPPO K9x开发者选项开启

### 正确开启步骤
OPPO手机开启开发者选项的步骤：

#### 步骤1：进入关于手机
1. 打开手机"设置"
2. 滑动到底部，找到"关于手机"
3. 点击进入

#### 步骤2：找到"版本号"
1. 在"关于手机"页面，找到"版本号"
2. **注意**: 不是"Android版本"，是"版本号"
3. 连续点击"版本号"7次
4. 会提示"您已处于开发者模式"

#### 步骤3：返回找到开发者选项
1. 返回到设置主页面
2. 现在应该能看到"**系统设置**"或"**其他设置**"
3. 进入后找到"**开发者选项**"

#### 步骤4：开启USB调试
1. 进入"开发者选项"
2. 找到"USB调试"
3. 开启开关
4. 确认提示"允许USB调试吗？" → 点击"确定"

### 如果还是找不到开发者选项
**尝试以下方法**：

#### 方法A：搜索设置
1. 在设置页面顶部有"搜索设置"框
2. 输入"开发者选项"或"USB调试"
3. 从搜索结果进入

#### 方法B：通过"关于手机"直接进入
1. 设置 → 关于手机
2. 找到"版本信息"
3. 有时点击"版本号"后，会直接出现"开发者选项"入口

#### 方法C：OPPO特定路径
OPPO手机可能的路径：
- 设置 → 其他设置 → 开发者选项
- 设置 → 系统设置 → 开发者选项
- 设置 → 更多设置 → 开发者选项

#### 方法D：使用ADB命令开启
如果以上都不行，可以使用ADB命令：
1. 在电脑上安装ADB工具（Android SDK的一部分）
2. 手机连接电脑
3. 命令提示符输入：
   ```bash
   adb shell settings put global development_settings_enabled 1
   ```

### 验证USB调试
开启后：
1. 用USB线连接手机和电脑
2. 手机上会出现"允许USB调试吗？"提示
3. 勾选"总是允许"，点击"确定"
4. 在电脑命令提示符输入：
   ```bash
   adb devices
   ```
5. 应该显示设备ID和"device"状态

## 第三部分：React Native CLI安装

### 安装命令
Android Studio安装配置完成后，安装React Native CLI：
```bash
npm install -g react-native-cli
```

### 验证安装
```bash
react-native --version
```
应该显示版本号

## 第四部分：完整环境验证

### 验证所有工具
打开新的命令提示符，逐一验证：

```bash
# 1. Node.js
node --version
npm --version

# 2. Git
git --version

# 3. Java
java --version
javac --version

# 4. Android环境
echo %ANDROID_HOME%
adb --version

# 5. React Native
react-native --version
```

### 创建测试项目验证
```bash
npx react-native init TestApp
cd TestApp
npx react-native run-android
```

## 问题解决

### 常见问题1：adb devices找不到设备
- **原因**: USB调试未开启，或驱动问题
- **解决**:
  1. 确认手机已开启USB调试
  2. 更换USB线或USB口
  3. 安装OPPO手机驱动

### 常见问题2：ANDROID_HOME not set
- **解决**: 检查环境变量设置，重启命令提示符

### 常见问题3：Java版本错误
- **解决**: 确认使用的是JDK 17，不是JRE

## 时间安排
- **Android Studio安装**: 30-45分钟
- **开发者选项开启**: 5-10分钟
- **环境配置**: 10分钟
- **验证测试**: 15分钟

**总计**: 约1小时

## 下一步
所有环境配置完成后，明天开始：
1. 创建React Native项目
2. 实现菜系选择界面
3. 开始编码"就它了"App

---
*文档创建时间: 2026-03-27 14:09*
*预计完成时间: 今天下午15:00前*
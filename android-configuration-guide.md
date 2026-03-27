# Android Studio 配置与验证指南

## 当前状态
- ✅ Android Studio 已安装
- ✅ OPPO K9x USB调试已开启
- 🔄 需要配置环境变量和验证连接

## 第一部分：查找Android SDK路径

### 方法A：通过Android Studio查看
1. **打开Android Studio**
2. 点击右上角的"..."或"More Actions"
3. 选择"**SDK Manager**"
4. 在"Android SDK"标签页，查看"**Android SDK Location**"
5. **记下这个路径**（通常类似）：
   - `C:\Users\Administrator\AppData\Local\Android\Sdk`
   - `C:\Android\Sdk`
   - 或其他自定义路径

### 方法B：通过文件管理器查找
1. 打开文件管理器
2. 进入以下路径查看：
   - `C:\Users\Administrator\AppData\Local\Android\`
   - `C:\Android\`
   - `C:\Program Files\Android\`
3. 寻找包含以下文件夹的路径：
   - `platform-tools\`（包含adb.exe）
   - `tools\`
   - `build-tools\`

### 方法C：使用Everything搜索（如果有安装）
1. 打开Everything搜索工具
2. 搜索"adb.exe"
3. 查看所在文件夹，其父文件夹就是SDK路径

## 第二部分：配置环境变量

### 步骤1：设置ANDROID_HOME
1. 右键"此电脑" → 属性 → 高级系统设置 → 环境变量
2. 在"**系统变量**"中点击"新建"
3. **变量名**: `ANDROID_HOME`
4. **变量值**: 你找到的SDK路径（如`C:\Android\Sdk`）
5. 点击"确定"

### 步骤2：添加到Path变量
1. 找到"系统变量"中的`Path`，点击"编辑"
2. 点击"新建"，添加以下路径（**每个一行**）：
   - `%ANDROID_HOME%\platform-tools`
   - `%ANDROID_HOME%\tools`
   - `%ANDROID_HOME%\tools\bin`
3. 点击"确定"保存所有更改

## 第三部分：验证Android环境

### 验证步骤
**重要**：重启命令提示符后验证

1. **检查ANDROID_HOME**
   ```bash
   echo %ANDROID_HOME%
   ```
   应该显示你设置的SDK路径

2. **检查adb版本**
   ```bash
   adb --version
   ```
   应该显示Android Debug Bridge版本信息

3. **检查手机连接**
   ```bash
   adb devices
   ```
   **手机需要**：
   - 用USB线连接电脑
   - 开启USB调试
   - 出现"允许USB调试吗？"提示时点击"确定"
   - 勾选"总是允许"

   **成功显示**：
   ```
   List of devices attached
   xxxxxxxx    device
   ```

## 第四部分：安装React Native CLI

### 安装命令
```bash
npm install -g react-native-cli
```

### 验证安装
```bash
react-native --version
```
应该显示类似：`react-native-cli: 2.0.1`

## 第五部分：完整环境验证

### 验证所有工具
打开**新的**命令提示符，输入以下命令：

```bash
# 1. Node.js
node --version
npm --version

# 2. Git
git --version

# 3. Java
java --version

# 4. Android环境
echo %ANDROID_HOME%
adb --version

# 5. React Native
react-native --version
```

### 期望输出
```
node --version
v24.14.1

npm --version
11.11.0

git --version
git version 2.53.0.windows.2

java --version
openjdk 17.0.18 2026-01-20

echo %ANDROID_HOME%
C:\Android\Sdk（你的路径）

adb --version
Android Debug Bridge version 1.0.41

react-native --version
react-native-cli: 2.0.1
```

## 第六部分：手机连接测试

### 测试步骤
1. **用USB线连接OPPO K9x和电脑**
2. **手机上操作**：
   - 下拉通知栏
   - 点击"USB充电中"通知
   - 选择"传输文件"或"MIDI"
   - 出现"允许USB调试吗？" → 点击"确定"，勾选"总是允许"

3. **电脑上验证**：
   ```bash
   adb devices
   ```
   应该显示设备ID和"device"状态

### 如果adb devices不显示设备
1. **更换USB线**：有些线只能充电不能传输数据
2. **更换USB口**：尝试电脑后面的USB口
3. **安装OPPO驱动**：
   - 访问OPPO官网下载USB驱动
   - 或使用第三方驱动工具
4. **重启adb服务**：
   ```bash
   adb kill-server
   adb start-server
   adb devices
   ```

## 第七部分：创建测试项目（可选）

如果所有验证通过，可以创建测试项目：

```bash
# 创建测试项目（时间较长，约5-10分钟）
npx react-native init TestApp

# 进入项目目录
cd TestApp

# 运行到手机（确保手机已连接）
npx react-native run-android
```

## 问题解决

### 问题1：'adb'不是内部或外部命令
- **原因**: 环境变量没设置好，或SDK路径错误
- **解决**: 重新检查ANDROID_HOME和Path设置

### 问题2：手机连接但adb devices不显示
- **原因**: 驱动问题或USB模式不对
- **解决**:
  1. 手机设置USB模式为"传输文件"
  2. 安装手机厂商驱动
  3. 重启adb服务：`adb kill-server && adb start-server`

### 问题3：Java版本错误
- **解决**: 确保使用的是JDK 17，环境变量JAVA_HOME设置正确

### 问题4：React Native init失败
- **解决**: 使用淘宝镜像加速
  ```bash
  npm config set registry https://registry.npmmirror.com/
  ```

## 下一步计划

### 完成配置后
1. **今天剩余时间**：
   - 创建GitHub仓库（如果没有）
   - 准备项目结构
   - 规划第一个界面

2. **明天开始**：
   - 创建"就它了"React Native项目
   - 实现菜系选择界面
   - 开始编码

### 成功标志
- ✅ 所有验证命令通过
- ✅ adb devices显示手机连接
- ✅ React Native CLI安装成功

---
*配置指南创建时间: 2026-03-27 14:27*
*预计完成时间: 30-45分钟*
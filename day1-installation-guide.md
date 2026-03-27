# 第一天：开发环境安装指南

## 目标
今天下午（2026-03-27）完成所有必要开发工具的安装，为明天开始编码做好准备。

## 预计时间
- **总时间**: 1.5-2.5小时（取决于网速和电脑配置）
- **分步时间**:
  - Node.js + Git: 20分钟
  - Java JDK: 15分钟  
  - Android Studio: 45-60分钟（下载较大）
  - 环境验证: 15分钟

## 安装清单

### 1. Node.js 安装
**用途**: React Native开发的基础运行环境

**步骤**:
1. 访问 https://nodejs.org
2. 下载 **LTS版本**（左侧绿色按钮）
3. 运行安装程序
4. **重要**: 安装时勾选 "Add to PATH" 选项
5. 完成安装

**验证**:
1. 打开命令提示符（按 Win+R，输入 `cmd`，回车）
2. 输入以下命令检查版本：
   ```bash
   node --version
   npm --version
   ```
3. 应该显示版本号（如: v18.17.0 和 9.6.7）

### 2. Git 安装
**用途**: 代码版本控制

**步骤**:
1. 访问 https://git-scm.com/download/win
2. 下载Windows版本
3. 运行安装程序，使用默认选项即可
4. 完成安装

**验证**:
```bash
git --version
```

### 3. Java JDK 安装
**用途**: Android开发必需

**步骤**:
1. 访问 https://adoptium.net/temurin/releases
2. 选择版本: **JDK 17** (LTS)
3. 操作系统: Windows
4. 架构: x64
5. 下载安装程序并运行

**环境变量配置**（重要！）:
1. 右键点击"此电脑" → 属性 → 高级系统设置 → 环境变量
2. 在"系统变量"中:
   - 新建变量名: `JAVA_HOME`
   - 变量值: `C:\Program Files\Eclipse Adoptium\jdk-17.0.9.7-hotspot`（具体路径根据安装位置）
3. 找到`Path`变量，点击编辑
4. 添加: `%JAVA_HOME%\bin`

**验证**:
```bash
java --version
javac --version
```

### 4. Android Studio 安装
**用途**: Android SDK和开发工具

**步骤**:
1. 访问 https://developer.android.com/studio
2. 下载Android Studio
3. 运行安装程序
4. **安装选项**:
   - 选择"Standard"安装
   - 确保包含:
     - Android SDK
     - Android SDK Platform
     - Android Virtual Device
5. 完成安装（首次启动可能较慢）

**Android SDK配置**:
1. 打开Android Studio
2. 进入"More Actions" → "SDK Manager"
3. 确保安装:
   - Android SDK Platform 33 (或最新)
   - Intel x86 Atom_64 System Image 或 Google APIs Intel x86 Atom System Image
4. 点击"Apply"安装

**环境变量配置**:
1. 添加系统变量:
   - 变量名: `ANDROID_HOME`
   - 变量值: `C:\Users\你的用户名\AppData\Local\Android\Sdk`（默认位置）
2. 在`Path`变量中添加:
   - `%ANDROID_HOME%\platform-tools`
   - `%ANDROID_HOME%\tools`
   - `%ANDROID_HOME%\tools\bin`

### 5. React Native CLI 安装
**用途**: React Native命令行工具

**命令**:
```bash
npm install -g react-native-cli
```

**验证**:
```bash
react-native --version
```

## 可选：代码编辑器

### VS Code（推荐）
1. 访问 https://code.visualstudio.com
2. 下载安装
3. 建议安装的扩展:
   - React Native Tools
   - ES7+ React/Redux/React-Native snippets
   - Prettier - Code formatter
   - JavaScript (ES6) code snippets

## 安装后验证

运行以下命令检查所有工具是否安装正确：

```bash
# 1. Node.js和npm
node --version
npm --version

# 2. Git
git --version

# 3. Java
java --version

# 4. Android环境
# 查看Android SDK路径
echo %ANDROID_HOME%

# 5. React Native CLI
react-native --version
```

应该看到类似输出：
```
node --version
v18.17.0

npm --version  
9.6.7

git --version
git version 2.42.0

java --version
openjdk 17.0.9 2023-10-17

react-native --version
react-native-cli: 2.0.1
```

## 故障排除

### 常见问题1：命令找不到
- **症状**: `'node' 不是内部或外部命令`
- **解决**: 重新启动命令提示符，或重启电脑

### 常见问题2：Android环境变量错误
- **症状**: `ANDROID_HOME is not set`
- **解决**: 检查环境变量设置，确保路径正确

### 常见问题3：Java版本问题
- **症状**: `JAVA_HOME is not set`
- **解决**: 确保JAVA_HOME变量指向正确的JDK安装目录

### 常见问题4：端口占用
- **症状**: React Native服务器启动失败
- **解决**: 
  ```bash
  # 查看占用8081端口的进程
  netstat -ano | findstr :8081
  
  # 结束进程（替换<PID>为实际进程ID）
  taskkill /PID <PID> /F
  ```

## 下一步

### 安装完成后
1. **联系我**: 告诉我安装是否成功
2. **创建GitHub仓库**（如果没有）:
   - 访问 https://github.com
   - 注册/登录
   - 创建新仓库，名称为"pick-it"
3. **测试设备准备**:
   - 准备Android手机
   - 开启"开发者选项"（设置→关于手机→连点版本号7次）
   - 开启"USB调试"

### 明天计划
1. **创建React Native项目**
2. **配置项目结构**
3. **开始编写第一个界面**（用户注册引导页）

## 重要提醒

### 网络要求
- Android SDK下载需要较好的网络（约2-3GB）
- 如果下载慢，可以考虑使用国内镜像

### 存储空间
- 确保C盘有至少10GB可用空间
- Android SDK和虚拟设备需要较多空间

### 时间安排
- 建议连续完成安装，避免中断
- 如果遇到问题，随时截图或描述问题问我

## 成功标准
- 所有验证命令都能正确显示版本号
- Android Studio能正常启动
- 能够运行 `react-native init TestApp` 创建测试项目

---
*文档创建时间: 2026-03-27 11:50*
*预计完成时间: 今天下午14:00前*
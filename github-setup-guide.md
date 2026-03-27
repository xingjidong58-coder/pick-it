# GitHub仓库设置完整指南

## 当前状态
- 所有开发环境已配置完成
- 已有9个项目文档
- 需要在桌面创建项目文件夹并推送到GitHub

## 第一步：在桌面创建项目文件夹

### 操作步骤
1. **回到桌面**：按 `Windows键 + D`
2. **创建文件夹**：
   - 在桌面空白处右键点击
   - 选择"新建" → "文件夹"
   - 命名为 `pick-it`
3. **进入文件夹**：双击打开`pick-it`文件夹

## 第二步：复制项目文档到文件夹

### 需要复制的文件
从我的工作空间复制以下文件到你的桌面`pick-it`文件夹：

1. `requirements.md` - 详细需求文档（22菜系+17忌口）
2. `development-plan.md` - 6周开发计划
3. `skills-analysis.md` - 技能需求分析
4. `user-manual-tasks.md` - 用户手动任务指南
5. `day1-installation-guide.md` - 第一天安装指南
6. `android-studio-installation.md` - Android Studio安装指南
7. `android-configuration-guide.md` - Android配置指南
8. `installation-step-by-step.md` - Node.js安装步骤
9. `nodejs-install-troubleshooting.md` - Node.js问题解决

### 复制方法（最简单）
**方法A：手动复制**
1. 按 `Windows键 + E` 打开文件管理器
2. 左侧导航到：`C:\Users\Administrator\.openclaw\workspace\projects\pick-it`
3. 选中上述9个文件
4. 右键 → 复制
5. 回到桌面，打开`pick-it`文件夹
6. 右键 → 粘贴

**方法B：使用命令行**（如果你熟悉）
```bash
# 进入桌面
cd Desktop

# 创建文件夹
mkdir pick-it

# 复制文件
copy "C:\Users\Administrator\.openclaw\workspace\projects\pick-it\*.md" "pick-it\"
```

## 第三步：GitHub账户准备

### 1. 注册GitHub账户（如果没有）
访问：https://github.com
- 点击"Sign up"
- 填写邮箱、密码、用户名
- 完成邮箱验证

### 2. 创建仓库
1. 登录GitHub
2. 点击右上角 **"+"** → **"New repository"**
3. 填写：
   - **Repository name**: `pick-it`
   - **Description**: "解决外卖选择困难症的App"
   - 选择 **Public**
   - ✅ **勾选** "Add a README file"
4. 点击 **"Create repository"**

### 3. 获取仓库地址
创建成功后，在仓库页面：
1. 点击绿色的 **"Code"** 按钮
2. 选择 **"HTTPS"**
3. **复制地址**（类似）：
   ```
   https://github.com/你的用户名/pick-it.git
   ```

## 第四步：Git配置与推送

### 打开命令提示符
按 `Windows键 + R`，输入 `cmd`，回车

### 完整命令序列
**请按顺序执行以下命令**（一行一行输入，每行后按回车）：

```bash
# 1. 进入桌面文件夹
cd Desktop\pick-it

# 2. 初始化Git仓库
git init

# 3. 设置你的Git用户信息（替换成你的实际信息）
git config --global user.name "你的GitHub用户名"
git config --global user.email "你的GitHub注册邮箱"

# 4. 添加所有文件到暂存区
git add .

# 5. 提交更改
git commit -m "初始提交：项目需求文档、开发计划、环境配置指南"

# 6. 连接远程仓库（替换成你的实际仓库地址）
git remote add origin https://github.com/你的用户名/pick-it.git

# 7. 推送到GitHub主分支
git push -u origin main
```

### 命令示例（假设用户名是 liuyihao）
```bash
cd Desktop\pick-it
git init
git config --global user.name "liuyihao"
git config --global user.email "liuyihao@example.com"
git add .
git commit -m "初始提交：项目需求文档、开发计划、环境配置指南"
git remote add origin https://github.com/liuyihao/pick-it.git
git push -u origin main
```

## 第五步：验证推送成功

### 1. 刷新GitHub仓库页面
应该看到9个.md文件

### 2. 或者使用命令验证
```bash
# 查看远程仓库状态
git remote -v

# 查看提交历史
git log --oneline
```

## 问题解决

### 问题1：git push 要求用户名密码
GitHub现在需要使用**Personal Access Token**：
1. 访问：https://github.com/settings/tokens
2. 点击"Generate new token"
3. 选择权限：勾选"repo"
4. 生成并复制令牌
5. 推送时用**令牌**代替密码

### 问题2：提示"fatal: remote origin already exists"
```bash
# 先删除旧的
git remote remove origin
# 再重新添加
git remote add origin https://github.com/你的用户名/pick-it.git
```

### 问题3：提示"Please tell me who you are"
```bash
# 设置用户信息
git config --global user.name "你的名字"
git config --global user.email "你的邮箱"
```

### 问题4：提示"branch 'main' does not exist"
```bash
# 重命名本地分支
git branch -M main
# 再推送
git push -u origin main
```

## 快速操作脚本

如果你觉得命令行复杂，可以使用这个**批处理脚本**：

在桌面`pick-it`文件夹中，新建一个文件`setup.bat`，内容：
```batch
@echo off
echo 正在设置Git仓库...

cd /d "%~dp0"
git init
git add .
git commit -m "初始提交：项目文档"

echo.
echo 请设置你的GitHub信息：
set /p github_user="输入GitHub用户名: "
set /p github_email="输入GitHub注册邮箱: "

git config --global user.name "%github_user%"
git config --global user.email "%github_email%"

echo.
echo 请粘贴你的GitHub仓库地址（从网页复制）：
set /p repo_url="仓库地址: "

git remote add origin "%repo_url%"
git push -u origin main

echo.
echo 完成！按任意键退出...
pause > nul
```

## 完成标志

✅ **成功标志**：
1. GitHub仓库页面显示9个.md文件
2. 命令提示符显示类似：
   ```
   Enumerating objects: 12, done.
   Counting objects: 100% (12/12), done.
   Writing objects: 100% (12/12), 45.23 KiB | 2.26 MiB/s, done.
   Total 12 (delta 0), reused 0 (delta 0), pack-reused 0
   To https://github.com/你的用户名/pick-it.git
    * [new branch]      main -> main
   Branch 'main' set up to track remote branch 'main' from 'origin'.
   ```

## 下一步

仓库设置完成后：
1. **今天剩余时间**：学习React Native技能
2. **明天**：创建React Native项目，开始编码
3. **后续**：每天代码推送到GitHub，形成开发历史

---
*指南创建时间: 2026-03-27 17:02*
1. 图标打算使用 iconify api 直接调用

### 媒体查询中的 样式还没有修改 前缀

@media only screen and (max-width: 767px)

含义：当设备视口宽度 小于或等于 767px 时应用。常把它当作“移动端”样式（小屏手机）。
典型用途：隐藏侧边栏、简化布局、使用单栏布局、增大触控目标等。

@media only screen and (min-width: 768px)

含义：当视口宽度 ≥ 768px 时应用（通常从这个宽度开始进入“平板/小屏桌面”样式）。
典型用途：两栏布局、显示次级导航、更多横向空间的 UI 布局。

@media only screen and (min-width: 992px)

含义：视口宽度 ≥ 992px（小型桌面/大平板 → 桌面样式）。
典型用途：主内容 + 侧栏常驻，更多细节/装饰显示，较大字体或更复杂网格。

@media only screen and (min-width: 1200px)

含义：视口宽度 ≥ 1200px（标准桌面及更大显示器）。
典型用途：多列网格、更宽容的容器、较大图片展示区、额外视觉装饰。

@media only screen and (min-width: 1920px)

含义：视口宽度 ≥ 1920px（超大屏 / 4K 桌面）。
典型用途：超宽布局、展示更多侧边信息、增加行宽或更复杂的仪表盘布局。

### 修改构建结束的文件内容

# git tag

很好的问题！Git tag 是一个非常重要的概念，让我详细为你解释：

🏷️ Git Tag 是什么？
Git tag 就像是给代码的某个时刻贴标签，用来标记重要的版本或里程碑。

# 简单理解：

# Commit = 代码的一个快照

# Tag = 给这个快照起个好记的名字

📊 Tag vs Branch vs Commit 的区别

# Commit: 代码变更的记录点

git log --oneline

# a1b2c3d fix: 修复登录 bug

# e4f5g6h feat: 添加用户注册功能

# h7i8j9k chore: 更新依赖

# Branch: 可以移动的指针，会随着新提交而移动

git branch

# \* main

# develop

# feature/login

# Tag: 固定不动的标签，永远指向特定的 commit

git tag

# v1.0.0

# v1.1.0

# v2.0.0

🎯 Tag 的主要用途

1. 版本发布标记

# 标记软件版本

git tag v1.0.0 # 第一个正式版本
git tag v1.1.0 # 功能更新版本
git tag v1.1.1 # bug 修复版本 2. 重要里程碑
git tag release-candidate-1
git tag beta-2023-12
git tag stable-production 3. 方便回滚和查找

# 快速切换到某个版本

git checkout v1.0.0

# 查看某个版本的代码

git show v1.1.0
🛠️ Tag 的基本操作
创建 Tag

# 1. 轻量标签（lightweight tag）- 只是一个指针

git tag v1.0.0

# 2. 注释标签（annotated tag）- 包含更多信息（推荐）

git tag -a v1.0.0 -m "第一个正式版本"

# 3. 给特定 commit 打标签

git tag v0.9.0 a1b2c3d

# 4. 强制创建/覆盖标签

git tag -f v1.0.0
查看 Tag

# 列出所有标签

git tag

# 列出匹配模式的标签

git tag -l "v1.\*"

# v1.0.0

# v1.1.0

# v1.2.0

# 查看标签详细信息

git show v1.0.0

# 查看标签和对应的 commit

git tag -n
推送 Tag

# 推送单个标签

git push origin v1.0.0

# 推送所有标签

git push origin --tags

# 推送所有内容（包括标签）

git push --follow-tags
删除 Tag

# 删除本地标签

git tag -d v1.0.0

# 删除远程标签

git push origin --delete v1.0.0

# 或者

git push origin :refs/tags/v1.0.0
📝 实际使用示例
典型的发布流程

# 1. 完成开发，准备发布

git add .
git commit -m "feat: 完成用户管理功能"

# 2. 创建版本标签

git tag -a v1.2.0 -m "版本 1.2.0: 添加用户管理功能"

# 3. 推送代码和标签

git push origin main
git push origin v1.2.0

# 4. 在 GitHub 上基于这个 tag 创建 Release

查看项目历史

# 查看所有版本

git tag --sort=-version:refname

# v2.1.0

# v2.0.0

# v1.2.1

# v1.2.0

# v1.1.0

# 查看两个版本之间的变化

git log v1.1.0..v1.2.0 --oneline

# 比较两个版本的差异

git diff v1.1.0 v1.2.0
🌟 在 GitHub/GitLab 上的应用
GitHub Releases

# 当你推送 tag 后，可以在 GitHub 上：

# 1. 自动创建 Release 页面

# 2. 上传编译后的文件

# 3. 写发布说明

# 4. 让用户下载特定版本

自动化部署

# CI/CD 可以监听 tag 推送

# 当推送 v*.*.\* 格式的 tag 时，自动：

# 1. 运行测试

# 2. 构建项目

# 3. 部署到生产环境

🎨 Tag 命名规范
语义化版本（Semantic Versioning）

# 格式：v 主版本.次版本.修订版本

v1.0.0 # 第一个稳定版本
v1.1.0 # 添加新功能，向后兼容
v1.1.1 # bug 修复
v2.0.0 # 重大更新，可能不向后兼容

# 预发布版本

v1.2.0-alpha.1
v1.2.0-beta.1
v1.2.0-rc.1 # release candidate
其他命名方式

# 日期格式

release-2023-12-25
v2023.12.25

# 代号格式

v1.0.0-codename-phoenix
stable-winter-2023
🔄 回到你的原始问题
现在回看这个命令：

npm version patch --git-tag-version=false --force && git tag -f $(npm view . version)
它的作用就是：

升级 package.json 中的版本号（比如 1.2.3 → 1.2.4）
创建一个对应的 git tag（比如创建标签 "1.2.4"）
这样就把 npm 包的版本和 git 仓库的版本标签同步了
💡 最佳实践

# 1. 使用注释标签而不是轻量标签

git tag -a v1.0.0 -m "版本说明"

# 2. 遵循语义化版本规范

# 主版本.次版本.修订版本

# 3. 在重要版本打标签前先测试

git tag -a v1.0.0-rc.1 -m "候选版本"

# 4. 推送标签到远程仓库

git push origin --tags

# 5. 写清楚标签说明

git tag -a v1.1.0 -m "
新功能：

- 添加用户头像上传
- 支持深色主题

Bug 修复：

- 修复登录状态丢失问题
  "
  Git tag 就是这样一个简单但强大的工具，帮助我们管理项目版本！你现在对 git tag 有清楚的理解了吗？😊

【来源于 传音智库 发现更多精彩 点击进入体验】

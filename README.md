# 潘伟鑫 · 个人主页（静态网站）

深色科技风个人展示网站：首屏 AI 形象、荣誉证书墙（22 张证书可点开看大图）、生活照片墙、白天/夜间切换、一键打印 PDF。

**纯静态网页，没有后端，永久免费托管在 GitHub Pages，全程不需要命令行。**

---

## 一、文件夹里都有什么

```
panweixin-site/
├── index.html                  ← 网站主页面（所有文字内容都在这一个文件里改）
├── assets/img/
│   ├── avatar.jpg              ← 首屏 AI 形象图
│   ├── certs/cert-01.jpg … 22  ← 22 张证书照片（高清）
│   └── life/life-01.jpg … 05   ← 5 张生活照
├── .github/workflows/deploy.yml ← 自动部署配置（别动、别删）
├── .nojekyll                   ← 让 GitHub 原样发布文件（别删）
└── README.md                   ← 本说明书
```

> 注意：`.github` 文件夹名字前面有一个点，Windows 里它是个隐藏文件夹，这是正常的。

---

## 二、上线步骤（照着点就行，约 10 分钟）

### 第 1 步：注册 / 登录 GitHub

打开 https://github.com ：
- 没有账号：点 **Sign up**（注册）→ 填邮箱、密码、用户名 → 邮箱里点验证链接。
- 有账号：直接登录。

> 用户名会出现在你网站的网址里，起个正经点的，比如 `panweixin`。

### 第 2 步：新建仓库

登录后，点右上角头像左边的 **＋** 号 → **New repository**（新建仓库）：

| 选项 | 怎么填 |
|------|--------|
| Repository name（仓库名） | **推荐填：`你的用户名.github.io`**（比如 `panweixin.github.io`）→ 这样网址最短、最好记 |
| Public / Private | 选 **Public**（公开，免费，必选） |
| Add a README file | **不要勾选** |

点绿色的 **Create repository**（创建仓库）。

> 想用别的仓库名（比如 `my-homepage`）也可以，只是网址会变成 `https://你的用户名.github.io/my-homepage`。

### 第 3 步：上传网站文件（最关键的一步）

刚建好的仓库页面中间有一行小字 **"uploading an existing file"**，点它；或者点 **Add file → Upload files**。

然后把电脑上 `panweixin-site` 文件夹里的**全部内容**拖进网页中间的大框里：
- `index.html`
- `assets` 文件夹（里面含图片）
- `.nojekyll`

**注意：`.github` 文件夹拖不进去（GitHub 网页会忽略它）。** 没关系，按下面补上：

1. 回到仓库页面，点 **Add file → Create new file**（创建新文件）
2. 文件名这一格，分两次输入：先输入 `.github/`（输完斜杠，文件夹就自动建好了），再输入 `workflows/deploy.yml`
3. 把本 README 最末尾「附：deploy.yml 完整内容」的代码**全部复制粘贴**进去
4. 点绿色 **Commit changes**（提交）

现在回到刚才拖文件的页面，页面底部确认框里写点说明（比如「网站上线」），点绿色 **Commit changes** 按钮。

> 检查清单：仓库里能看到 `index.html`、`assets` 文件夹、`.nojekyll`、`.github/workflows/deploy.yml` —— 四样齐了才行。

### 第 4 步：让 GitHub 自动发布

提交完成的那一刻，GitHub 就已经自动开始部署了（这就是 `deploy.yml` 的作用）。只需做一件事：

点仓库上方的 **Settings**（设置）→ 左侧 **Pages** →
**Build and deployment → Source** 下拉框选 **GitHub Actions**。

### 第 5 步：拿到你的网址

1. 点仓库上方的 **Actions** 标签页 → 看到工作流跑出一个绿色 ✓，就说明发布成功（第一次大约 1~3 分钟）。
2. 回到 **Settings → Pages**，页面顶部会显示：

   > ✅ Your site is live at **https://你的用户名.github.io**

3. 点开这个网址——网站上线了！手机、电脑都能访问，发给谁都能看。

> 如果打开是 404 页面：说明还没部署完，等两分钟再刷新即可。

---

## 三、以后怎么改内容

网站上线后想改内容，不用重新部署，直接改文件、重新上传即可：

### 改文字（名字、介绍、邮箱、技能等）

用记事本打开 `index.html`，搜索 **「改这里」** 四个字，所有文字内容都集中在那个 `PROFILE` 大括号里，改完保存。
- 邮箱：改 `email` 那一行
- 微信号：把 `wechat: ""` 改成 `wechat: "你的微信号"`，网站上会自动出现「复制微信号」按钮

### 换照片

把新照片处理成同名文件，替换 `assets/img` 下对应文件即可：
- 头像 → 覆盖 `avatar.jpg`
- 证书 → 覆盖 `certs/cert-01.jpg` …（顺序对应荣誉墙从左到右）
- 生活照 → 覆盖 `life/life-01.jpg` …

### 加新证书

1. 新照片放进 `certs` 文件夹，命名接着排：`cert-23.jpg`
2. 记事本打开 `index.html`，把 `certCount: 22` 改成 `certCount: 23`
3. 上传覆盖这两个位置 → 搞定

### 上传更新

仓库页面 → **Add file → Upload files** → 把改过的文件拖进去 → **Commit changes** → 等 1~2 分钟自动生效。

---

## 四、常见问题

| 现象 | 解决 |
|------|------|
| 打开网址是 404 | 刚部署完要等 1~3 分钟，刷新即可；超过 10 分钟还是 404，检查第 4 步 Source 是否选了 GitHub Actions |
| Actions 是红色 ✗ | 点开看报错信息，九成是文件没传全（`.github` 文件夹丢了） |
| 图片显示不出来 | 检查 `assets` 文件夹是否完整上传；图片文件名大小写必须一致 |
| 仓库默认分支不是 main | Settings → General → Default branch 改成 main；或者用记事本打开 `deploy.yml`，把第一处 `main` 改成你的分支名 |
| 想改回旧版本 | 仓库里每个文件的历史版本都能恢复：点文件 → History → 恢复 |

---

## 附：deploy.yml 完整内容

（如果第 3 步需要手动创建该文件，把下面内容整段复制进去）

```yaml
name: Deploy static content to Pages

on:
  push:
    branches: ["main"]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      - name: Setup Pages
        uses: actions/configure-pages@v5
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: "."
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

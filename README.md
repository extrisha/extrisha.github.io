# LemonBerry

一个用 Jekyll + minima 主题搭的 GitHub Pages 博客，仓库名 `extrisha.github.io`，上线后地址是：

**https://extrisha.github.io**

---

## 一、上线：只需要三步

### 1. 在 GitHub 上建仓库

打开 https://github.com/new ，**Repository name** 必须填 `extrisha.github.io`（一字不差，这就是你的域名）。

- 可见性选 **Public**（免费账户的 Pages 只对公开仓库开放）
- 不要勾选 README / .gitignore / license，保持空仓库

### 2. 把本地代码推上去

在 PowerShell 里执行（Git 已经装好了）：

```powershell
cd C:\Users\prima\Documents\LemonBerry
git remote add origin https://github.com/extrisha/extrisha.github.io.git
git push -u origin main
```

第一次 push 会弹出浏览器让你登录 GitHub，授权即可（用的是 Git Credential Manager，不用手打密码）。

### 3. 打开 Pages

进入仓库 → **Settings** → 左侧 **Pages**：

- **Source** 选 `Deploy from a branch`
- **Branch** 选 `main`，目录选 `/ (root)`
- 点 **Save**

等 1~2 分钟，访问 https://extrisha.github.io 就能看到站点。之后每次 push，GitHub 都会自动重新构建，通常一分钟内生效。

---

## 二、日常写作

新文章 = 在 `_posts/` 里新建一个文件，文件名 `年-月-日-英文短标题.md`：

```markdown
---
title: 文章标题
date: 2026-11-12 10:00:00 +0800
---

正文从这里开始，用 Markdown 写。
```

写完后：

```powershell
git add .
git commit -m "新文章：文章标题"
git push
```

嫌本地麻烦的话，也可以直接在 GitHub 网页上点进 `_posts/` → **Add file** → **Create new file**，写完提交，效果完全一样。

---

## 三、改站点信息

| 想改什么 | 改哪里 |
|---|---|
| 站点标题、描述、作者 | `_config.yml` 顶部 |
| 顶部导航栏有哪些页面 | `_config.yml` 的 `header_pages` |
| 关于页 | `about.md` |
| 首页样式 | 主题决定，改 `_config.yml` 的 `minima.skin`（可选 `classic` / `dark` / `solarized` 等） |
| 自定义样式 | 新建 `assets/main.scss`，见下方 |

改完 `_config.yml` 一定要 push，GitHub 才会重新构建。

---

## 四、本地预览（可选）

工作区目前**没有安装 Ruby**，所以本地跑不了 `jekyll serve`。两种选择：

**A. 不装，直接线上看**（推荐先用这个）——改完 push，等一分钟刷新网页。

**B. 想本地实时预览**，需要装 Ruby：

1. 下载 https://rubyinstaller.org/downloads/ 的 **Ruby+Devkit 3.x (x64)**，安装时勾选 `ridk install` 的默认项
2. 新开一个 PowerShell：

```powershell
cd C:\Users\prima\Documents\LemonBerry
gem install bundler
bundle install
bundle exec jekyll serve --livereload
```

然后打开 http://127.0.0.1:4000 。`bundle install` 第一次会慢几分钟，正常。

---

## 五、几个容易踩的坑

- **仓库名写错**：叫 `blog` 之类的话，网址会变成 `extrisha.github.io/blog`，此时必须把 `_config.yml` 里的 `baseurl` 改成 `"/blog"`。
- **文件没被识别**：文章必须在 `_posts/` 下，且文件名日期格式必须是 `2026-11-12-xxx.md`，`2026-11-12-xxx.MD` 或日期写成 `2026/11/12` 都不会生成页面。
- **改了没生效**：先在仓库 **Actions** 标签页看构建是否成功；失败时红色 ✗ 点进去有报错原因。
- **图片 404**：路径用 `/assets/images/xxx.png`（以斜杠开头）。
- **主题样式错乱**：`_config.yml` 里 `theme: minima` 不能删，这是 GitHub 内置主题，不需要装。
- **自定义域名**：以后想用自己的域名，在仓库 Settings → Pages → Custom domain 填，再到域名商处加一条 CNAME 记录指向 `extrisha.github.io`，HTTPS 证书 GitHub 会自动签发。

---

## 目录结构

```
├── _config.yml          # 站点配置
├── Gemfile              # 本地预览用的依赖（线上构建用不到）
├── index.md             # 首页
├── about.md             # 关于页
├── 404.html             # 404 页面
├── _posts/              # 所有文章
│   └── 2026-11-05-hello-world.md
└── assets/              # 图片等静态资源
```

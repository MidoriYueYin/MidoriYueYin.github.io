# Yue 的学术个人网站

基于 [al-folio](https://github.com/alshedivat/al-folio) v1（Jekyll），部署在 GitHub Pages。
日常更新**只需要改 Markdown / YAML / .bib 文件**，push 之后 GitHub 会自动重新构建网站（约 4–5 分钟）。

---

## 一、第一次上线（只做一次）

1. 在 GitHub 新建一个**空仓库**，名字必须是 `你的用户名.github.io`（不要勾选添加 README）。
2. 在本文件夹里：
   ```bash
   git init
   git add .
   git commit -m "initial site"
   git branch -M main
   git remote add origin https://github.com/你的用户名/你的用户名.github.io.git
   git push -u origin main
   ```
3. 仓库 **Settings → Actions → General → Workflow permissions** → 选 **Read and write permissions** → Save。
4. 到 **Actions** 标签页，等 "Deploy site" 跑完（绿色对勾）。如果第 3 步之前它已经失败了，点进去 **Re-run jobs**。
5. **Settings → Pages → Build and deployment**：Source 选 **Deploy from a branch**，分支选 **gh-pages**，文件夹 `/ (root)`。
6. 一分钟后访问 `https://你的用户名.github.io`。

### 上线前必须填的 TODO

在整个文件夹里搜索 `TODO` 就能找到全部，主要是：

| 文件 | 要改什么 |
|---|---|
| `_config.yml` | `last_name`（第 8 行左右）、`url`（换成你的用户名）、`scholar:` 下的 `last_name` |
| `_data/socials.yml` | 邮箱；想显示的 Google Scholar / ORCID / GitHub 取消注释并填写 |
| `assets/img/prof_pic.jpg` | 用你的照片覆盖（同名） |
| `assets/pdf/cv.pdf` | 用你的 CV 覆盖（同名） |
| `_bibliography/papers.bib` | 用 Zotero 导出覆盖（见下文） |
| `_pages/about.md`、`_pages/personal.md`、`_projects/*.md` | 文字都是初稿，按你的语气改 |

---

## 二、日常更新

### 加一条 News（首页显示最近 5 条）

在 `_news/` 里新建一个文件，文件名随意但建议带日期，例如 `_news/2026-11-03-icphs.md`：

```markdown
---
layout: post
date: 2026-11-03
inline: true
related_posts: false
---

Paper on Long'an Zhuang tone sandhi accepted to ICPhS 2027! 🎉
```

一句话里可以放链接：`[论文](/publications/)`。首页 news 标题可以点进完整的新闻归档页。

### 加 / 改论文

推荐直接从 Zotero 导出：

1. Zotero 里给自己的论文建一个 collection。
2. 右键 collection → **Export Collection…** → 格式选 **Better BibTeX** → 覆盖保存为 `_bibliography/papers.bib`。
   （更省事：勾选 **Keep updated**，以后在 Zotero 里改了会自动同步到这个文件，你只要 commit + push。）
3. 确认 `papers.bib` 最上面有两行 `---`（没有就手动加回去）。

al-folio 的额外按钮写在 Zotero 条目的 **Extra** 栏里，每行一个：

```
tex.selected: true
tex.abbr: ICPhS
tex.pdf: yue2027zhuang.pdf
tex.slides: yue2027zhuang-slides.pdf
tex.code: https://github.com/...
tex.bibtex_show: true
```

`pdf` / `slides` / `poster` 指向的文件放在 `assets/pdf/`。`selected: true` 的论文会出现在首页。

Publications 页面按类型分三组：`@article`（期刊）、`@inproceedings`（会议论文集）、`@misc` / `@unpublished`（报告和海报）。在 Zotero 里把条目类型设对就会自动归类。

### 加一个研究项目

复制 `_projects/` 里任意一个文件，改文件名和内容即可。`importance` 决定排序（小的在前）。想要卡片封面图，就把图片放进 `assets/img/`，取消 `img:` 那行的注释。

### 更新 CV

用新 PDF 覆盖 `assets/pdf/cv.pdf`，文件名不变，所有链接自动生效。

### 改导航栏

每个 `_pages/*.md` 顶部的 `nav: true` 决定是否出现在导航栏，`nav_order` 决定顺序。

---

## 三、可选：本地预览

不想每次都 push 才看效果的话，装 Docker 后在本文件夹运行：

```bash
docker compose up -d
```

然后打开 http://localhost:8080 。改文件后刷新即可（改 `_config.yml` 需要等它自动重启几秒）。

## 四、网站没更新 / 构建失败？

去仓库 **Actions** 标签页看最新一次 "Deploy site"，红色叉号点进去看报错。最常见的原因：YAML 缩进错了、`.bib` 里有不匹配的大括号。更多见 `docs/TROUBLESHOOTING.md`。

# Liu Hanqing — al-folio 个人学术主页

基于官方 [alshedivat/al-folio](https://github.com/alshedivat/al-folio) 的真实 Jekyll 项目，使用 `al_folio_core 1.0.15`、`jekyll-scholar`、`al_math` 与 al-folio 自带的导航、搜索和深浅色切换。

上游起点：`929fbf71c5a45b13e9b5a20dfa425ce9e9de7935`。依赖锁定在 `Gemfile` / `Gemfile.lock`，原始 MIT 许可证保留在 `LICENSE`。

## 本地预览

进入本目录后运行：

```bash
./bin/site serve
```

浏览器打开 <http://127.0.0.1:4000/>。按 `Ctrl+C` 停止。

这个 Mac 已安装 Ruby 3.3 和 Node 22，脚本自动使用对应 Homebrew 路径；其他电脑请先准备 Ruby 3.3+、Node 22+ 和 Bundler，再运行 `./bin/site setup`。Gem 安装在 `vendor/bundle`，不会混入系统 Ruby。

```bash
./bin/site build   # Jekyll 编译到 _site/
./bin/site check   # Prettier 格式检查
./bin/site audit   # al-folio 升级与本地覆盖审计
```

`_site` 是构建结果，不要直接编辑。它包含多页和独立资源，请通过本地服务预览。

## 内容维护

| 内容                   | 文件                                        |
| ---------------------- | ------------------------------------------- |
| 姓名、网址、站点开关   | `_config.yml`                               |
| 首页简介、头像、座右铭 | `_pages/about.md`                           |
| 研究方向               | `_data/research.yml`                        |
| 首页动态               | `_news/`                                    |
| 邮箱、GitHub           | `_data/socials.yml`                         |
| 论文                   | `_bibliography/papers.bib`                  |
| CV PDF                 | `assets/pdf/Liu_Hanqing.pdf`                |
| 博客入口与文章         | `_pages/blog.md`、`_posts/`                 |
| 配色、排版、响应式样式 | `assets/css/personal.css`                   |
| 头像原图               | `assets/img/ayanami-rei-pixiv-88718073.png` |

论文条目设置 `selected = {true}` 后会同时出现在首页和 publications 页面。BibTeX、摘要按钮由原生 al-folio 组件生成。论文资料来自 <https://arxiv.org/abs/2605.06152>；邮箱和机构参考公开论文 <https://openreview.net/pdf?id=9a8RE9pnB3>。

首页简介之后依次显示 News 和 Selected publications，各区使用相同的分隔线。详细研究方向仅在 `/research/` 页面展示。News 按日期倒序读取 `_news/`，日期显示为 `YYYY.MM`；Selected publications 在首页内容中调用原生 `selected_papers.liquid`，因此关闭了布局末尾的重复输出。

导航栏的 `cv` 直接打开本人提供的 PDF，链接由 `_config.yml` 中的 `cv_pdf` 设置。更新简历时，用新版替换 `assets/pdf/Liu_Hanqing.pdf` 后重新构建即可。

论文缩略图 `assets/img/publication_preview/mlp-precision.png` 由本人提供的原始 `MLP_precision.pdf` 整页渲染为 1600 × 1200 PNG，保留完整图表，不含论文排版中的 `(a)` 标签；通过 BibTeX 的 `preview` 字段显示。

头像使用本人提供的 DALIYANG 插画，在页面中居中裁成正方形，图下链接至 [Pixiv 原作](https://www.pixiv.net/artworks/88718073)。原图保留完整内容，裁切由 `personal.css` 控制。

Research 的三部分为 Learning mechanics、Generative models 和 Physics of Neural Networks。`_data/research.yml` 的 `body` 字段使用 Markdown；已有 Slingshot 工作链接到公开论文，未公开的研究细节不放在网站中。两篇示例博客仍标注为草稿。教育经历不设独立页面；About 开头已按本人提供的内容介绍东京大学 Koyama Lab 硕士在读身份及清华大学物理学学士、历史学硕士背景。

## 本地覆盖

保留两处局部覆盖：`_layouts/default.liquid` 加入首次访问默认深色的设置和 `personal.css`；`_includes/header.liquid` 在所有页面的左上角显示可返回首页的姓名字标，支持通过 `nav_title` 单独设置导航文字（如小写 `publications`，页面标题仍为 `Publications`），并加入直接打开 PDF 的 `cv` 链接。其余导航逻辑、首页 `about`、论文 `bib`、搜索、公式和主题切换仍使用原版 gem 的实现。

四个社交图标只在简介后的链接行显示，由 `_data/socials.yml` 和原生 `social_links` 标签生成；首页底部的重复社交区已关闭。

`.al-folio-overrides.yml` 记录覆盖来源与哈希。更新 gem 后运行 `./bin/site audit` 检查是否需要同步上游布局。

官方演示人物、文章、图片和简历已移出本项目，保存在同级 `../al-folio-template-examples/`，避免出现在个人网站中。最初的单文件 HTML 原型仍保留在上一级目录。

## GitHub Pages 发布

仓库：[liuhanqing-phy/liuhanqing-phy.github.io](https://github.com/liuhanqing-phy/liuhanqing-phy.github.io)。主页地址：<https://liuhanqing-phy.github.io/>。`_config.yml` 已配置该网址，并保持 `baseurl: ""`。

在仓库 **Settings → Pages → Source** 中选择 **GitHub Actions**。`.github/workflows/deploy.yml` 在推送到 `main` 后自动检查格式与 al-folio 覆盖、编译 Jekyll，再通过 GitHub 官方 Pages actions 发布。也可以在 **Actions → Deploy site → Run workflow** 手动运行。免费套餐需要公开仓库才能使用 Pages。

更新内容后，先运行 `./bin/site build` 检查，再提交并推送到 `main`。在 Actions 中等待 Deploy site 成功后刷新线上页面。`_site/`、依赖目录和 `preview/` 检查截图均不提交。模板自带的维护工作流、演示截图和旧 Lighthouse 报告已移到同级 `../al-folio-template-examples/`，个人仓库只保留网站部署工作流。

# 传奇游戏宣传网站 · 部署与收录指南

一个可直接推送到 GitHub Pages 的传奇类游戏宣传落地页，已内置完整 SEO 配置。

## 目录结构

```
传奇宣传网站/
├── index.html      # 宣传落地页（自包含，含 SEO meta / OG / JSON-LD）
├── robots.txt      # 爬虫规则 + sitemap 指向
├── sitemap.xml     # 站点地图（域名占位，需替换）
├── assets/         # 图片素材（hero 主视觉 + 三职业立绘）
└── README.md       # 本说明
```

## 部署前必改：待替换清单

搜索 `yourname.github.io` 与 `data-demo` 可定位全部占位：

| 位置 | 内容 | 说明 |
|---|---|---|
| `<head>` canonical / og:url / og:image | `https://yourname.github.io/` | 换成你的真实域名或 github.io 地址 |
| robots.txt / sitemap.xml | `https://yourname.github.io/` | 同上，三处一起改 |
| Hero / 简介 / 页脚 | 游戏名称「传奇」、介绍文案 | 换成你的真实游戏名与介绍 |
| 下载按钮（Hero 与下载区） | `data-demo="下载链接待配置..."` | 把按钮改成真实下载链接（或换成 `<a href="..." class="btn btn-gold">`） |
| 资讯公告 3 条 | 示例条目 | 换成真实公告，并把 `data-demo` 占位删除 |
| 简介数据（3 / 7×24 / 1 座沙城） | 示例数据 | 换成真实游戏数据 |
| 页脚版权 | `© 2026 传奇宣传站` | 换成真实版权信息 |

> Hero 主视觉图为 AI 生成，画面左侧带一段金色书法装饰字（生成时自动添加）。若需无字版本，可让助手重新生成。

## GitHub Pages 部署步骤（5 分钟）

1. 登录 GitHub，新建仓库，例如 `legend-website`（Public，勾选 Add a README 可省略）。
2. 把本目录内所有文件（index.html、robots.txt、sitemap.xml、assets/ 整个文件夹）上传到仓库根目录：
   - 网页端：仓库页 → Add file → Upload files → 拖入文件 → Commit。
   - 或命令行：`git init && git add . && git commit -m "init" && git remote add origin https://github.com/<你的用户名>/legend-website.git && git push -u origin main`。
3. 仓库页 → Settings → Pages → Source 选择 `Deploy from a branch`，Branch 选 `main`，保存。
4. 等待 1~2 分钟，访问 `https://<你的用户名>.github.io/legend-website/`（若仓库名就是 `<用户名>.github.io` 则访问根地址）。
5. 建议绑定自定义域名（可显著提升百度收录概率）：在仓库 Settings → Pages → Custom domain 填入你的域名，并按提示在 DNS 加 CNAME 记录指向 `<用户名>.github.io`。

## 搜索引擎快速收录（提交清单）

| 引擎 | 操作 |
|---|---|
| Google | 登录 [Google Search Console](https://search.google.com/search-console)，添加资源 → 输入网站地址（属性类型选「网域」）→ 按提示验证 → 「站点地图」提交 `https://<你的域名>/sitemap.xml` |
| Bing | 登录 [Bing Webmaster Tools](https://www.bing.com/webmasters)，可直接「从 Google Search Console 导入」，无需重复验证；再提交 sitemap |
| 百度 | 登录 [百度搜索资源平台](https://ziyuan.baidu.com) → 站点验证（把验证文件放到网站根目录或改 HTML 的 meta 验证标签）→ 「普通收录-手动提交」逐条提交首页 → 「sitemap 提交」提交 sitemap.xml。百度对 github.io 收录偏慢，建议绑定自定义域名并保持内容更新 |

加分项（可选）：用 GitHub Actions 定时调用百度「主动推送」API，可显著加快百度收录；需要时可以让助手帮你配置。

## 内容更新建议（影响排名）

- 保持资讯区持续更新真实公告（每周 1~2 条），爬虫回访频率随更新频率提高。
- 每个页面的 `<title>` 与 `<meta description>` 尽量包含「传奇」等核心关键词。
- 站外：在贴吧、知乎、游戏论坛发布带官网链接的介绍内容，积累外链。

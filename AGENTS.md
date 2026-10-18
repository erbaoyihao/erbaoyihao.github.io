# AGENTS.md

This file is the onboarding guide for AI coding agents working in this repository.

## Project overview

This repository is the source for the GitHub Pages **user site** `erbaoyihao.github.io`
(remote: `https://github.com/erbaoyihao/erbaoyihao.github.io`). The site's content is
served directly from the `main` branch at `https://erbaoyihao.github.io`.

It is a Chinese-language personal website covering 科研 (research), 教学 (teaching),
生活 (music, running, outdoors and gathering photos), 简历/CV, and 历届毕业生
(graduated students).
Visual style: 黑白涂鸦 + 少量学术冷幽默 — 近白纸面、墨色大标题、手绘圈线、
麦田卡通肖像、开放式目录与细线分隔。整体只用中性灰阶；正文保持清楚严谨，
幽默集中在首页、页眉批注与 404。照片保留原色，不做灰度处理；首页肖像与生活相册按原比例完整展示。

## Repository layout

```
.
├── index.html       # 首页：麦田卡通肖像首屏 + 身份简介 + 开放式板块目录
├── research.html    # 科研：方向标签、论文（DOI 链接）、专利（申请号检索）、项目卡片、科研照片
├── teaching.html    # 教学：课程卡片、资料索取方式与答疑联系方式
├── life.html        # 生活：音乐、跑步、户外相册 + 合影网格
├── cv.html          # 简历：教育/工作经历时间线、联系方式
├── students.html    # 历届毕业生：毕业合影 + 按届分组的 student-chip
├── 404.html         # 彩蛋 404 页
├── css/style.css    # 全部样式：设计令牌（:root 变量）+ 涂鸦组件 + 响应式
├── js/main.js       # 移动端导航开合（含 Escape 关闭）+ 当前页高亮
├── assets/img/      # 图片原图（照片、肖像）放这里
├── assets/optimized/# 由原图生成的 480w / 960w 响应式版本，供页面 srcset 引用
├── assets/cv.pdf    # 可下载的 PDF 简历
├── README.md
└── AGENTS.md
```

## Technology stack

**Plain static HTML/CSS/JS — no build step, no dependencies, no frameworks.**
GitHub Pages serves the files as-is. Keep it that way: do not introduce Jekyll,
npm, or a bundler without asking the site owner first.

## Build and test commands

There is no build. To preview locally:

```bash
python3 -m http.server 8000   # then open http://localhost:8000
```

Opening an HTML file directly in a browser also works (all paths are relative).
Before pushing, click through every page and check that navigation links resolve.

## Editing conventions

- **Colors and spacing**: change the CSS variables in `:root` at the top of
  `css/style.css` — do not hardcode new color values in page markup. Radius,
  shadows, and the neutral grays all live there. Inline SVG decorations use
  `currentColor` and CSS tokens; keep them editable and `aria-hidden`. `theme-blue` / `theme-green` /
  `theme-coral` / `theme-yellow` / `theme-purple` classes are kept for markup
  compatibility but now all resolve to the same ink accent (single-color scheme).
- **Shared header/footer**: each page duplicates the same `<header class="site-header">`
  and `<footer class="site-footer">` markup (no templating). When changing the
  navigation, update **all seven** HTML files.
- **Content**: lists (papers, patents, courses, students, timeline entries,
  photos) follow repeatable block patterns — copy an existing block to add an
  entry. Papers link to `https://doi.org/...`; patents link to a Google Patents
  application-number search.
- **Images**: keep full-resolution originals in `assets/img/` and generate
  `480w` / `960w` variants into `assets/optimized/` (same base name plus
  `-480` / `-960`), e.g. with `sips -Z 960` or ImageMagick. Pages reference the
  optimized files through `src` + `srcset` + `sizes`, always declare the original
  `width` / `height` (to prevent layout shift), use `loading="lazy"` except for
  the homepage portrait (`fetchpriority="high"`), and link the `assets/img/`
  original from the surrounding photo link. Do not delete an original while a
  page still links it; every image in `assets/img/` should have a home on a page.
- **Fonts**: system font stack only (PingFang SC / Microsoft YaHei / ...). Do not
  add webfont CDNs.
- The site brand is「二宝」; the owner's real name (王芸 / Yun Wang) appears in
  page content. Update both consistently when the brand changes.
- Lecture files were intentionally removed (`assets/lectures/` is gone), so the
  teaching page offers materials by email request instead of direct downloads.
  Do not link to lecture files that are not committed.
- Accessibility: keep decorative elements `aria-hidden`; honor
  `prefers-reduced-motion` (already handled in CSS).

## Deployment

- Deployment is automatic: GitHub Pages publishes whatever is on the `main` branch
  (repository root) to `https://erbaoyihao.github.io` after each push.
- There is no staging environment; pushing to `main` makes changes live immediately.
  Verify changes locally before pushing, and prefer pull requests or at least a local
  preview for non-trivial changes.

## Development conventions

- Git default branch: `main`.
- No code style, commit-message convention, or review process is established yet.
- Keep this `AGENTS.md` up to date as content and tooling are added.

## Security considerations

- This is a public repository (GitHub Pages user sites must be public unless the
  account has a paid plan): never commit secrets, API keys, or personal data.
- Everything committed to `main` is publicly served — treat the whole tree as public.

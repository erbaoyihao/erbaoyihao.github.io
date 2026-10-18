# AGENTS.md

This file is the onboarding guide for AI coding agents working in this repository.

## Project overview

This repository is the source for the GitHub Pages **user site** `erbaoyihao.github.io`
(remote: `https://github.com/erbaoyihao/erbaoyihao.github.io`). The site's content is
served directly from the `main` branch at `https://erbaoyihao.github.io`.

It is a Chinese-language personal website covering 科研 (research), 教学 (teaching),
生活 (life/essays/photography), 简历/CV, and 历届毕业生 (graduated students).
Visual style: 黑白涂鸦 + 少量学术冷幽默 — 近白纸面、墨色大标题、手绘圈线、
麦田卡通肖像、开放式目录与细线分隔。整体只用中性灰阶；正文保持清楚严谨，
幽默集中在首页、页眉批注与 404。照片保留原色，不做灰度处理；首页肖像与生活相册按原比例完整展示。

## Repository layout

```
.
├── index.html       # 首页：麦田卡通肖像首屏 + 开放式板块目录 + 自我介绍
├── research.html    # 科研：方向标签、论文（按年份分组）、项目卡片
├── teaching.html    # 教学：课程卡片、讲义链接
├── life.html        # 生活：音乐与跑步相册 + 随笔列表 + 摄影网格
├── cv.html          # 简历：教育/工作经历时间线、联系方式
├── students.html    # 历届毕业生：按届分组的 student-chip
├── 404.html         # 彩蛋 404 页
├── css/style.css    # 全部样式：设计令牌（:root 变量）+ 涂鸦组件 + 响应式
├── js/main.js       # 移动端导航开合（含 Escape 关闭）+ 当前页高亮
├── assets/img/      # 图片（头像、照片）放这里
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
- **Content placeholders**: real personal info is marked with `TODO:` comments in
  the HTML. Lists (papers, courses, students, timeline entries) follow repeatable
  block patterns — copy an existing block to add an entry.
- **Fonts**: system font stack only (PingFang SC / Microsoft YaHei / ...). Do not
  add webfont CDNs.
- Placeholder name in the current content is「二宝」; it is meant to be replaced
  with the owner's real name/nickname.
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

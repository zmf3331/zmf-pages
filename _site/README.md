# 朱名斐的博客

> 记录学习、思考与技术实践。

基于 Jekyll + GitHub Pages 的个人博客，主题为水墨风格的「码志」重构版。

- 线上地址：<https://zmf3331.github.io/zmf-pages/>
- 仓库：<https://github.com/zmf3331/zmf-pages>

## 本地预览

```bash
bundle install
bundle exec jekyll serve --baseurl="" --config _config.yml,_config_dev.yml
```

访问 <http://localhost:4000/>。

## 部署

推送到 `main` 分支后，由 GitHub Pages 自动构建：

```bash
git add .
git commit -m "update"
git push
```

## 说明

- 这是**项目站点**，`_config.yml` 里 `baseurl: "/zmf-pages"`、`url: "https://zmf3331.github.io"`。
- 内部链接统一使用 `{{ '/path' | relative_url }}` 或 `{{ post.url | relative_url }}`，本地用 `--baseurl=""` 覆盖即可在根路径预览。
- 评论使用 giscus，需在 <https://giscus.app/zh-CN> 生成配置后填入 `_config.yml`。

## 写文章

在 `_posts/` 下新建 `YYYY-MM-DD-标题别名.md`：

```markdown
---
layout: post
title: 文章标题
date: 2026-10-10 10:00:00 +0800
categories: [随笔]
tags: [标签1, 标签2]
---

正文……
```

## License

代码遵循仓库 [LICENSE](./LICENSE)；文章内容采用 [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.zh)。

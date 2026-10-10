---
layout: page
title: 关于
subtitle: 记录学习、思考与技术实践
keywords: 关于,朱名斐
comments: false
menu: 关于
permalink: /about/
---

你好，我是**朱名斐**。这里记录我的学习笔记、技术实践和日常思考。欢迎通过邮箱 [zmf3331@163.com](mailto:zmf3331@163.com) 与我联系。


## 关于本站

- 主题：水墨风 Jekyll 主题（基于 [码志](https://github.com/mzlogin) 重构）
- 站点地址：<https://zmf3331.github.io/zmf-pages/>
- 源码仓库：<https://github.com/zmf3331/zmf-pages>

## 技能关键词

{% for skill in site.data.skills %}
### {{ skill.name }}
<p class="chips">{% for keyword in skill.keywords %}<span class="tag">{{ keyword }}</span>{% endfor %}</p>
{% endfor %}


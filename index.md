---
title: Online Hosted Instructions
permalink: index.html
layout: home
---

# 컨텐츠 디렉토리

각 연습에 대한 하이퍼 링크는 강사가 데모를 하거나 학생이 연습을 할 때 사용할 수 있습니다.

## 연습

{% assign wts = site.pages | where_exp:"page", "page.url contains '/Instructions/Walkthroughs'" %}
| 모듈 | 연습 |
| --- | --- | 
{% for activity in wts %}| {{ activity.wts.module }} | [{{ activity.wts.title }}{% if activity.wts.type %} - {{ activity.wts.type }}{% endif %}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}


---
layout: post
title:  "google verify with HTML tag"
date:   2021-10-18 13:43:05 +0800
categories: blog
typora-copy-images-to: ../asserts
typora-root-url: ../
---

网上查到的方案好几种，其实大部分都过时了。我用的是`方案C`，简单又明了。他们都无一例外的没有讲那一串`乱码`从哪里来。那个是从`Google search console`而来。每个网站不一样，要去获取自己的。拿到`google-site-verification`之后可以根据以下方案来填写。


# 方案A
```html
<head>
  <meta charset="utf-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  {%- seo -%}
  <link rel="stylesheet" href="{{ "/assets/css/style.css" | relative_url }}">
  {%- feed_meta -%}
  {%- if jekyll.environment == 'production' and site.google_analytics -%}
    {%- include google-analytics.html -%}
  {%- endif -%}
  <meta name="google-site-verification" content="P5JvIrpAzGuAYMCBT3_-1TEpWsUUoQAaYK3B6hgaauA" />
</head>
```
from: [Make your Jekyll Github Pages appear on Google search result (2 steps)][1]

# 方案B
```conf
google_site_verification: onQcXpAvtHBrUI5LlroHNE_FP0b2qvFyPq7VZw36iEY
```
from: [jekyll github repo code][2]

# 方案C
```conf
webmaster_verifications:
  google: 1234
  bing: 1234
  alexa: 1234
  yandex: 1234
  baidu: 1234
```
from: [jekyll seo tag usage][3]


[1]: https://victor2code.github.io/blog/2019/07/04/jekyll-github-pages-appear-on-Google.html
[2]: https://github.com/jekyll/jekyll/blob/master/docs/_config.yml
[3]: http://jekyll.github.io/jekyll-seo-tag/usage

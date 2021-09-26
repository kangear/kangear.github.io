---
layout: post
title:  "Add Disqus to Jekyll Minima Theme Simplified"
date:   2021-09-26 23:07:05 +0800
categories: jekyll update
typora-copy-images-to: ../asserts
typora-root-url: ../
---

像添加`Google Analytics`一样，添加`Disqus`仅需要一行代码。如下：
```conf
# Disqus Comments
disqus:
    # Leave shortname blank to disable comments site-wide.
    # Disable comments for any post by adding `comments: false` to that post's YAML Front Matter.
    shortname: kangear
```
但是有一点，`shortname`一定要找准。不是`userid`，登录之后进入`admin`，点击`your site`，然后是网页地址的一部分。如下图所示：

![有帮助的截图](/assets/disqus_shortname.jpg)

还需要注意一点，`url`一定要和`_config.yml`中的一致。就这样一行代码就可以了。


像需要自己写`_include/disqus.html`之类的方法都是过时的。比如如下这些
1. [How do I use disqus comments in github pages blog (Markdown)?][1]
2. [Add Disqus to Jekyll Minima Theme Simplified - 2020][2]

[1]: https://stackoverflow.com/a/50775934/2193455
[2]: https://cuda-chen.github.io/blogging/2020/03/28/add-Disqus-to-Jekyll-Minima-theme-simplified.html
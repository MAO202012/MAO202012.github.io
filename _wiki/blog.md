---
layout: post
title: 博客
categories: Cat
description: My Favorites and the description.
keywords: Favorites
comments: false
---
转载自 https://huangzhongde.cn/post/2020-02-20-hugo-comments-plugin-valine/

https://lovehxy.com/blog/post/hugo%E6%B7%BB%E5%8A%A0Valine%E8%AF%84%E8%AE%BA%E7%B3%BB%E7%BB%9F/

官网：https://valine.js.org

修改配置文件

```

vim config.toml
  [params.valine]
    enable = true
    appId = 'Your appId'
    appKey = 'Your appKey'
    notify = false  # mail notifier , https://github.com/xCss/Valine/wiki
    verify = false # Verification code
    avatar = 'mm'
    placeholder = '说点什么吧...'
    visitor = true
    
```

添加html代码

```

mkdir layouts/partials
vim layouts/partials/comments.html
  <!-- valine -->
  {{- if .Site.Params.valine.enable -}}
  <!-- id 将作为查询条件 -->
  
  <div id="vcomments"></div>
  <script src="//cdn1.lncld.net/static/js/3.0.4/av-min.js"></script>
  <script src='//unpkg.com/valine/dist/Valine.min.js'></script>

  <script type="text/javascript">
    new Valine({
        el: '#vcomments' ,
        appId: '{{ .Site.Params.valine.appId }}',
        appKey: '{{ .Site.Params.valine.appKey }}',
        notify: '{{ .Site.Params.valine.notify }}', 
        verify: '{{ .Site.Params.valine.verify }}', 
        avatar:'{{ .Site.Params.valine.avatar }}', 
        placeholder: '{{ .Site.Params.valine.placeholder }}',
        visitor: '{{ .Site.Params.valine.visitor }}'
    });
  </script>
  {{- end -}}
  
 ``` 
 
js在国内的源用不了，建议挂梯子把官网的源拷贝下来，然后自己建源

另外引入mathjax的源的方法为：

```

  <script type="text/x-mathjax-config">
    MathJax.Hub.Config({
        tex2jax: {
        skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
        inlineMath: [['$','$']]
        }
    });
</script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

```

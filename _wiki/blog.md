---
layout: post
title: 博客
categories: Cat
description: My Favorites and the description.
keywords: Favorites
comments: false
---

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
          <span id="{{ .RelPermalink }}" class="leancloud_visitors" data-flag-title="{{ .Title }}">
          <span class="post-meta-item-text">文章阅读量 </span>
          <span class="leancloud-visitors-count"><i class="leancloud-visitors-count"></i></span>次
          <p></p>
        </span>
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
 
转载自 https://huangzhongde.cn/post/2020-02-20-hugo-comments-plugin-valine/

https://lovehxy.com/blog/post/hugo%E6%B7%BB%E5%8A%A0Valine%E8%AF%84%E8%AE%BA%E7%B3%BB%E7%BB%9F/

js在国内的源用不了，建议挂梯子把官网的源拷贝下来，然后自己建源

## 把b站视频嵌入博客

https://www.it520.org/2018/12/27/iframe-bilibili-youtube/

解决办法如下：
增加CSS样式如下：
```
.meta-media {
  position: relative;
  margin-bottom: 30px;
  float: left;
  width: 100%;
  height: 0;
  padding-bottom: 75%;
}
.video {
  position: absolute;
  width: 100%;
  height: 100%;
  left: 0;
  top: 0;
}
```
CSS
调用iframe时增加DIV块meta-media，并给iframe加class 为video,如下：
```
<div class="meta-media"><iframe src="//player.bilibili.com/player.html?aid=14841794&cid=24183753&page=1" frameborder="no" scrolling="yes" allowfullscreen="allowfullscreen" high_quality="1" framespacing="1" class="video" > </iframe></div>
HTML
```
这样两步就解决了！

原理： meta-media元素赋值了一个0值的高度和一个百分比的 bottom padding， 这个百分比的bottom padding 百分比是和容器宽度的百分比,这就得到了一个固定的宽比率。但是为了让这个iframe显示在这个0高度的meta-media里面，你需要设置meta-media定位为relative，并将div里面的iframe的定位设置成absolute.

## 图片自适应大小

写页面的时候经常会遇到需要图片 自适应 容器大小这样的情况：
```
<style>

div{width:400px;height:400px;border:1px solid #000; }

img{width:100%;height:100%;}

</style>
```
不管容器有多大，只要将img的宽高设置成100%（这里的100%是相对于父级宽高而言）就能自适应容器大小。

那是不是就这这么简单完事儿了呢？如果你不介意图片被放大后可能出现失真的话也的确是这样就ok了。 
假如你介意 图片放大后会失真，我们可以改进上面的代码，只需要将img的样式简单修改.
```
img{max-width:100%;max-height:100%;}

 ```

max-width:100%和width:100%的区别在于,max-width是相对于img自身的尺寸而言的。意思是图片最大宽度为自身尺寸的宽，在这里就是100px。而width的100%我们上面已经说过了是相对于父级宽度的，所以为了不让图片被放大后失真我们可以设置img的最大宽度为自身尺寸大小，更通俗的讲就是只允许缩小不允许放大img。

具体情况中是选择width:100%还是max-width:100%还是依据个人的需求而定，另外在响应式设计中这个问题稍微会复杂一点。

 

图片适应手机端  要控制的是装图片的容器宽度
```
 img{
display: block;(可不加 banner可以用)
height: auto;
max-width: 100%;（或者width：100%）
}
```
将以上标签加入之后保存，再用手机打开即是自适应网页了。

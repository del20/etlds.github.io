---
layout: post
title:  "我就是说说而已"
date:   2016-08-31 11:23:57 -0400
categories: live
comments: true
---
第一篇博客大家都好像喜欢定下些目标，许下些承诺，一定要坚持写博客，一定要完成什么什么指标之类的。我就不是这么一个人，我就爱随性，我就是懒惰。所以，我定下了一下几个目标。

1. 坚持写下博客。系统地记录一下自己学到的。以跟别人分享的方式分享技术细节，哲学思想。
    1. 用 python 刷题，然后写下学习到的东西。本来是想学 scala 的，听闻他牛B，大数据都爱用。但是 LeetCode 没有 scala 的 compiler，所以改用 python。但是用过 ruby 的我，怎么都觉得 python 语法很不自然，我还是喜欢 ruby。
    2. 本来想学 spark。上了几节 edX 上的课，感觉自己在学怎么用数据库，没啥意思，工作上也没用到，学了就忘，还是缓一缓，等工作需要到了再学。
    3. 看了好多好的 ruby on rails 的 talk。对怎么 refactor 一个有一定规模的 rails 项目产生兴趣。老实说我觉得技术面试，很应该考一轮代码重构。这种东西不是刷题能刷出来的。
2. 学习摄影。看到人家 500px 上的图片，心真的痒痒的。但是我又是一个穷屌丝，没钱买好机器，好镜头，就只能靠软实力了。
3. 学习爵士钢琴。不需要即兴，给我一首流行歌，能改编得像似那么样子就行。

我觉得就这样吧，反正写多了也做不到。

在说说建博客的事，medium，简书，Blogger，都建了账号，都试了。但是作为一个 hacker，不用 jekyll + github 好像不太像样。最后还是花了半天时间学了怎么搭建这个 etlds.github.io 的博客。本来还想装个 theme，让页面看起来帅一点，不过后来想一想，hacker 的精神不就是 DIY 吗？干嘛装别人写的 theme，自己搞！ 然后在想一想，纯文本不是才够 hacker 吗？ 所有到最后就默认的 minima 了，还蛮耐看的。

半天下来感叹程序员的生涯就是这么的痛苦并快乐，一个简单的博客，列一下你用到的东西，git, ruby, ruby gem, markdown, liquid, html, sass, coffeescript... 当然我是说你如果想做得很好的话了。技术日新月异，如果是无脑地不停学习，到头来其实什么都没学到，因为你一年前学的，明年将会过时。所以我觉得应该学习的是技术当中的哲学，精神，把一个东西弄深了，自然当中的道理会投射到其他心的技术上。T-shape skill set 是很有道理的。

{% if page.comments %}
<div id="disqus_thread"></div>
<script>

/**
 *  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
 *  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables */
/*
var disqus_config = function () {
    this.page.url = PAGE_URL;  // Replace PAGE_URL with your page's canonical URL variable
    this.page.identifier = PAGE_IDENTIFIER; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
};
*/
(function() { // DON'T EDIT BELOW THIS LINE
    var d = document, s = d.createElement('script');
    s.src = '//etlds.disqus.com/embed.js';
    s.setAttribute('data-timestamp', +new Date());
    (d.head || d.body).appendChild(s);
})();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
{% endif %}

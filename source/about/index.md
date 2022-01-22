---
title: about
date: 2022--12 22:14:36
keywords: 关于
description: 关于我的一点点介绍
comments: false
photos: https://gitee.com/ljv0606/cdn/raw/master/img/b7.webp
---
{% raw %}
<!-- 因为vue和botui更新导至bug,现将对话移至js下的botui中配置 -->
<div class="entry-content">
  <div class="moe-mashiro" style="text-align:center; font-size: 40px; margin-bottom: 20px;">[咳咳，简单介绍一下我]</div>
  <div id="hello-mashiro" class="popcontainer" style="min-height: 300px; padding: 2px 6px 4px; background-color: rgba(236, 225, 221, 0.29); border-radius: 10px;">
    <center>
    <p>
    </p>
    <h4>
    与&nbsp;<ruby>
    Cici&nbsp;<rp>（</rp>
    <rt>
    大可爱</rt>
    <rp>
    ）</rp>
    </ruby>
    对话中...</h4>
    <p>
    </p>
    </center>
    <bot-ui></botui>
  </div>
</div>
<script src="/js/botui.js"></script>
<script>
bot_ui_ini()
</script>
{% endraw %}
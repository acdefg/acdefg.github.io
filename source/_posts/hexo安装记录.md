---
title: Hexo安装记录
author: Cici
avatar: https://gitee.com/ljv0606/cdn/raw/master/img/表情1.jpg
authorLink: /about
authorAbout: 小菜本菜
categories: 博客
comments: true
date: 2022-01-20 12:08:05
tags: web
keywords: hexo| sakura
description: hexo中sakura主题安装
photos: https://gitee.com/ljv0606/cdn/raw/master/img/authorweb.webp
---

### 环境配置

参考： <https://blog.csdn.net/sinat_37781304/article/details/82729029#t2>

简单列一下:

#### git环境（对于整个大环境）

`sudo apt-get install git`对于整个大环境，就是可以在根目录安装<br>
同步github

```
git config --global user.name "yourname"
git config --global user.email "youremail"
```

检查

```
git config user.name 
git config user.email
```

生成公匙，并查看

```
ssh-keygen -t rsa -C "youremail"
gedit ~/.ssh/id_rsa.pub
```

github后台添加公匙（gitee也可以用这个）

```
ssh -T git@github.com
ssh -T git@gitee.com
```

#### git deploy

(这个先不安，要先安hexo环境，后面还会写一遍，放在这里是因为我每次建新的blog的时候hexo已经配置过了，只用在新文件夹安装一遍这个)

```
npm install hexo-deployer-git --save
```

#### hexo环境（对于整个大环境）

```
sudo apt-get install nodejs
sudo apt-get install npm
npm install -g hexo-cli
```

检查

```
node -v
npm -v
hexo -v
```

### 初始化一个blog文件夹

```
hexo init myblog //myblog随便取
cd myblog 
npm install
npm install hexo-deployer-git --save //git deply
```

1. 换theme
2. 改confi
3. 调试
    ```
    hexo g
    hexo server
    ```
    最彻底的编译
    ```
    hexo cl //hexo clean
    hexo g  //hexo generate
    hexo s  //hexo server
    ```
    方便，但是用的时候不如上一个配置的彻底
    ```
    hexo cl & hexo g & hexo s
    ```
    没有改confi，重启本地服务器调试
    ```
    hexo s -g
    ```
4. 上传`hexo d`
   ```
    deploy:
        type: git
        message: generate my blog
        repository:
            github: git@github.com:acdefg/acdefg.github.io.git
            gitee: git@gitee.com:ljv0606/ljv0606.git
        branch: master
   ```
5. 备份`hexo b` 只在主题sakura中看见作者配置了，其他主题不知道能不能用（查了一下属于hexo的一个插件，安装一下就可以用了：backup）
   ```
    backup:
        type: git
        message: backup my blog
        repository:
            github: git@github.com:acdefg/acdefg.github.io.git,backup
   ```
### sakura主题
参考链接：
主题作者写的文档：https://docs.hojun.cn/sakura/docs/#/home<br>
作者自己的博客：https://2heng.xin/<br>
同主题大佬的博客：https://flymc.cc/Sakura/<br>

#### fontaware动态效果
这里可根据自己的需要进行修改，不需要的可以删除或者#注释掉，path: /xxx/ 所在目录为\Blog\source\xxx\，
fa: fa-xxx 为图标，可在Font-Awesome官网中搜索到，如游戏机图标为 fa-gamepad。
faa-xxxxx 为鼠标悬浮在图标上的动态效果，如 faa-shake 为左右摇晃，faa-vertical 垂直摇晃，可根据自己喜好修改，在后续添加顶栏菜单项时也可以自行使用。

#### 更新主题出现的问题
更换主题后上传一直不成功，然后才发现更换了文件夹，新配置的hexo的各个配件的版本都特别低<br>
更新语句:
check1：有指示怎么安装
```
npm install -g npm-check 
npm-check 
```
check2：按照以下步骤无脑安装
```
npm install -g npm-check-updates
ncu -u
npm update
npm install
```
两种check各有千秋，以下是特定版本的安装
```
npm install --save hexo@5.0.0
```

浏览器缓存也会影响页面更新显示，一般可以用更换一个浏览器来检测是不是这个问题<br>
按`f12`或者`ctrl+shift+c`打开开发者模式，在网络中禁用缓存（disable cache）

#### 标题那里的动态特效

这个特效我看大佬原博客上面有,但是大佬发的这个hexo主题下载下来并没有，我又基本上没有接触过前端代码，但是呜呜呜真的很想要，所以就只能硬刚了<br>
![左上角logo](https://gitee.com/ljv0606/cdn/raw/master/mdimg/blogicon.png)

{% fb_img https://gitee.com/ljv0606/cdn/raw/master/mdimg/blogicon.png logo图 %}

首先打开大佬博客的网站源码，然后再baidu一下代码，这样这样，那样那样，就成了<br>
先把元素的定义加上在header.ejs里，这是改后的代码，改前的的没了，按没改的地方搜一下就好了

```
    <div class="site-branding">
      <span class="site-title">
        <span class="logolink moe-mashiro">
          <a href=<%= theme.url %>> 
            <ruby>
              <span class="sakuraso"><%= theme.prefixName %></span>
              <span class="no">の</span>
              <span class="shironeko"><%= theme.siteName %></span>
            </ruby> 
          </a>
        </span>
      </span>
    </div>
```
改得地方`<a>`里面的：
```
          <a href=<%= theme.url %>> 
            <ruby>
              <span class="sakuraso"><%= theme.prefixName %></span>
              <span class="no">の</span>
              <span class="shironeko"><%= theme.siteName %></span>
            </ruby> 
          </a>
```
然后style.css里面找sakuraso，对了为了方便我把原来的sakurasono全改成sakuraso查找替换麻，也就三个
```
.logolink.moe-mashiro .sakuraso, .logolink.moe-mashiro .no {
    font-size:25px;
    border-radius:9px;
    padding-bottom:2px;
    padding-top:5px
}
.logolink a:hover .no {
    -webkit-animation: spin 1s linear infinite;/*鼠标hover时，i图标旋转,infinite表示动画无限循环*/
    animation: spin 1s linear infinite;    
}
/*定义动画*/
@-webkit-keyframes spin { /*兼容性写法。spin是关键帧的动画名称*/
from { /*动画起始状态*/
    -webkit-transform: rotate(0deg);
}
to { /*动画结束状态*/
    -webkit-transform: rotate(360deg);
}
}
@keyframes spin {
from {
    transform: rotate(0deg);
}
to {
    transform: rotate(360deg);
}
}
.logolink a:hover .no {
    -webkit-animation: spin 1s linear infinite;/*鼠标hover时，i图标旋转,infinite表示动画无限循环*/
    animation: spin 1s linear infinite;    
}
```
这个改的原来的，加了个`logolink.moe-mashiro .no`,其他的就都是新加的
```
.logolink.moe-mashiro .sakuraso, .logolink.moe-mashiro .no {
    font-size:25px;
    border-radius:9px;
    padding-bottom:2px;
    padding-top:5px
}
```
参考博客：https://blog.csdn.net/erdouzhang/article/details/71402747
其他还有一些实现旋转的代码好像都不行，我觉得应该是元素类型的原因（假装就是这样）

---
title: 安装julp的一些坑
author: Cici
avatar: https://gitee.com/ljv0606/cdn/raw/master/img/头像1.jpg
authorLink: /about
authorAbout: 小菜本菜
authorDesc: 小菜本菜
categories: 技术
comments: true
date: 2022-01-20 12:08:05
tags: issue
keywords: julp | hexo
description: 安装julp网上的教程编译错误
photos: https://gitee.com/ljv0606/cdn/raw/master/img/b6.webp
---
## 一些坑
### 记录一些记下来的
#### julp代码压缩
网上关于julp的下载和运行，我找的代码跑半天跑不通，一边翻译错误报告，一边上stack overflow总算给它改对了。想了想可能看的教程是好几年前的了吧，在语法上出现了一些不合现在规则的问题。
主要问题集中在julpfile文件上

#### 附上原文
https://qianling.pw/hexo-optimization/

1. julpfile.mjs后缀的更改
2. 代码内容

```
import gulp from 'gulp';
import minifycss from 'gulp-minify-css';
import uglify from 'gulp-uglify';
import htmlmin from 'gulp-htmlmin';
import htmlclean from 'gulp-htmlclean';
import imagemin from 'gulp-imagemin';

// 压缩html文件
gulp.task('minify-html',async function() {
  return gulp.src('./public/**/*.html')
  .pipe(htmlclean())
  .pipe(htmlmin({
  removeComments: true,
  minifyJS: true,
  minifyCSS: true,
  minifyURLs: true,
  }))
  .pipe(gulp.dest('./public'))
});
// 压缩css文件
gulp.task('minify-css',async function() {
  return gulp.src('./public/**/*.css')
  .pipe(minifycss())
  .pipe(gulp.dest('./public'));
});
// 压缩js文件
gulp.task('minify-js',async function() {
  return gulp.src(['./public/**/.js','!./public/js/**/*min.js'])
  .pipe(uglify())
  .pipe(gulp.dest('./public'));
});
// 压缩 public/images 目录内图片
gulp.task('minify-images', async function() {
  gulp.src('./public/images/**/*.*')
  .pipe(imagemin({
     optimizationLevel: 5, //类型：Number  默认：3  取值范围：0-7（优化等级）
     progressive: true, //类型：Boolean 默认：false 无损压缩jpg图片
     interlaced: false, //类型：Boolean 默认：false 隔行扫描gif进行渲染
     multipass: false, //类型：Boolean 默认：false 多次优化svg直到完全优化
  }))
  .pipe(gulp.dest('./public/uploads'));
});
// 默认任务 gulp 4.0 适用的方式
gulp.task('default', gulp.parallel('minify-html', 'minify-css', 'minify-js', 'minify-images')
 //build the website
 );
```

由于我的确不太懂写这个文件用的语法，也只是按照错误提示改了一些，不能保证改得内容的准确性，反正我的julp是能正常使用了

之前遇到的一些懒得写了，之后的问题应该会持续更新，弃坑就当我没说过
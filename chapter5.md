使用 Gulp 编译 LESS
================

请务必理解如下章节后阅读此章节：

1. [安装 Node 和 Gulp](chapter1.md)
2. [使用 Gulp 压缩 JS](chapter2.md)

----------

> Less 是一门 CSS 预处理语言，它扩充了 CSS 语言，增加了诸如变量、混合（mixin）、函数等功能，让 CSS 更易维护。


安装
---

```
npm install gulp-less
```

基本用法
-------

你可以 [下载所有示例代码](https://github.com/nimojs/gulp-book/archive/master.zip) - [或在线查看代码](https://github.com/nimojs/gulp-book/tree/master/demo/chapter5)

```
// 获取 gulp
var gulp = require('gulp');
// 获取 gulp-less 模块
var less = require('gulp-less');

// 编译less
// 在命令行输入 gulp images 启动此任务
gulp.task('less', function () {
    // 1. 找到 less 文件
    gulp.src('less/**.less')
    // 2. 编译为css
        .pipe(less())
    // 3. 另存文件
        .pipe(gulp.dest('dist/css'));
});

// 在命令行使用 gulp auto 启动此任务
gulp.task('auto', function () {
    // 监听文件修改，当文件被修改则执行 images 任务
    gulp.watch('less/**.less', ['less']);
});

// 使用 gulp.task('default') 定义默认任务
// 在命令行使用 gulp 启动 less 任务和 auto 任务
gulp.task('default', ['less', 'auto']);
```


LESS 代码和编译后的CSS代码
----------

[less/a.less](https://github.com/nimojs/gulp-book/tree/master/demo/chapter5/less/a.less)

```
.less{
	a{
        color:pink;
    }
}
```
[less/import.less](https://github.com/nimojs/gulp-book/tree/master/demo/chapter5/less/import.less)


```
@import "a.less";
.import{
	a{
		color:red;
    }
}
```
[less/a.css](https://github.com/nimojs/gulp-book/tree/master/demo/chapter5/dist/css/a.css)

```
.less a {
  color: pink;
}
```
[less/import.css](https://github.com/nimojs/gulp-book/tree/master/demo/chapter5/dist/css/import.css)

```
.less a {
  color: pink;
}
.import a{
  color: red;
}
```
[阅读下一章节：使用 Gulp 编译 SASS](chapter6.md)
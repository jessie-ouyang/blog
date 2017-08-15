## gulp

1.构建工具

```
指通过简单配置就可以帮我们实现合并、压缩、校验、预处理等一些列人物的软件工具
常见的构站工具包括：Grunt、Gulp、F.I.S、webpack
```

2.gulp简介

- gulp是利用nodejs写的

- gulp是基于流的自动化构建工具

- 网站开发完成之后，要先做项目构建，构建完成之后才可以上线

- 项目构建

  ```html
  1.代码压缩---对html css js进行代码压缩，减少代码的体积
  2.代码混淆 ---js，替换变量名，把有意义的标识符替换成无意义的短的变量
  3.合并文件
  4.将less  sass等自动转换成浏览器支持的css
  ```

  **gulp是管道式工作方式**

3.gulp的安装

- 首先安装全局gulp，如果之前安装过就可以省略此步骤

  ```
  npm install gulp -g
  全局gulp按照的插件，可以在任意的地方使用
  本地安装的插件，只能在当前项目中使用
  ```

- 本地按照，在项目目录中

  ```
  npm install gulp --save
  ```



4.gulp的使用

- 在项目目录中新建一个gulpfile.js文件

  ```
  创建点开头的文件名的文件有2种方式
  1.用命令行  touch .gulpfile.js
  2.写.gulpfile.再回车
  ```

- 在这个文件中写在构建代码

  ```
  在gulpfile.js中写构建代码
  var gulp = require("gulp");----这个gulp对象可以配合插件进行构建工作
  ```

- 创建任务（依然是在gulpfile.js文件中书写）

  ```
  gulp是以任务的形式来执行每一项构建化工作
  调用gulp对象的task方法来创建任务
   task（）方法有2个参数：参数1--任务名称；参数2---回调函数，执行该任务的时候要做的事情
  ```

  ```javascript
  gulp.task("yscss",function(){
    
  })
  ```

- 执行任务

  ```
  用cmd或者git 等其他命令工具，执行gulp yscss 那么yscss这个任务就会被执行
  ```


5.一些常见任务

- 压缩css   用gulp-cssmin插件

  ```
  var cssmin = require("gulp-cssmin")
  gulp.task("yscss",function(){
    //用来压缩css
    gulp.src("需要压缩的文件路径")
    .pipe(cssmin());
    pipe(gulp.dest("压缩好后最后要放入的目录"))
  })
  ```

  **需要利用gulp.css-min插件，才能执行对css的压缩工作**

  **gulp.dest("")最后将压缩好的放置到哪里，通过这个方法实现**

  **gulp.pipe()管道方法，给设置什么关卡**


- 压缩js

  ```
  var gulp = require("gulp");
  var uglify = requier("gulp-uglify");----gulp-uglify是一个模块
  gulp.task("ysjs",function(){
    gulp.src("需要压缩的js文件的路径")
    .pipe(ugligy())
    .pipe(gulp.dest("要放置的路径"))
  })
  ```

- 合并文件

  ```
  var gulp = require("gulp");
  var contat = require("gulp-contat");
  gulp.task("contatFile",function(){
    gulp.src([文件1，文件2.。。。。])
    .pipe(contat("all.js"))-------------合并之后的文件名
    .pipe(uglify())---------------------合并之后对文件再进行压缩混淆
    .pipe(gulp.dest("要放置的路径"));
  })
  ```

- 压缩html文件

  ```
  gulp-htmlmin  插件
  var gulp = require("gulp");
  var htmlmin = require("gulp-htmlmin");
  gulp.task("htmlmin",function(){
    gulp.src("要压缩的文件")
    .pipe(htmlmin({ ---------------参数要是一个对象最一些简单的配置
      removeComments:true,--------清楚HTML注释
      collapseWhitespace:true,-------压缩html
      collapseBooleanAttributes:true,-----省略布尔属性的值
      removeEmptyAttributes:true,---------删除script的
      minfyJs:true,
      minfyCss:true
    }))
    .gulp.src("要压缩文件的路径")
    .pipe(gulp.dest("要放置的路径"))
  })
  ```

- 将sass转换为css

  ```
  var gulp = require("gulp");
  var sass =reuqire.("gulp-sass");
  gulp.task("sass2css",function(){
    gulp.src("sass文件的路径")
    .pipe(sass())
    .pipe(cssmin())
    .pipe(gulp.dest("要放置的路径"))
  })
  ```

- 将less转换为css

  ```
  var gulp = require("gulp");
  var less = require("gulp-less");
  gulp.task("less2css",function(){
    gulp.src("less文件的路径")
    .pipe(less())
    .pipe(cssmin())
    .pipe(gulp.desk("要放置的路径"))
  })
  ```

- 文件监视

  ```
  gulp对象提供一个watch方法，用于监视指定文件的变化，一旦改动，就执行指定的任务
  var gulp = require("gulp");
  gulp.task("watchCss",function(){
  //监视指定的css文件，可以使用通配符，一旦文件发生变化，就自动执行yscss任务
    gulp.watch("要监视的文件"，[“yscss"])
  })
  watch（）方法的第2个按时，还可以是一个回调，当文件发生变化以后，就执行这个回调
  ```

- 压缩图片---一般不建议使用

  ```
  方式和sass  less一样
  ```

  ​




### 将经过代码构建后的代码上传到服务器，进行上线

- git init

- git add

- git commit -m xxxx

- 将文件从本地仓库上传到远程服务器仓库

  ```

  ```

  ​








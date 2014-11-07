# CSS 风格参考 #


## 目的 ##


- 一致性
- 语义化
- 可读性
- 模块化


## 文档 ##


- **页面编码**

    统一采用 UTF-8 （无 BOM） 编码。

    不添加 `@charset "utf-8";`。


- **代码注释**

    添加必要的注释以提高可读性。

    每个功能模块都必须加注释。


- **代码缩进**

    采用空格作为缩进符，长度为 2。


- **行尾空格**

    必须移除无用的行尾空格。

    > 大部分编辑器都有自动移除尾部空格的功能，比如 Sublime Text。


## 规则（Rule） ##

    规则 === 选择器 {
        声明;
        声明;
    }


- **分行**

    两个规则之间插入一个空行。


## 选择器（Selector） ##


- **命名**

    使用通用且有意义的名字，即从名字上能够看出元素的作用。


- **大小写**

    全部小写，多个单词间用连线符（`-`）连接。


- **分行**

    每个选择器单独一行，选择器后加一空格，空格后的花括号（`{`）不换行。

    多个选择器以逗号（`,`）分隔，在每个逗号后换行。

- **通配符（*）**

    不允许使用通配符选择器。


## 声明（Declaration） ##

    声明 === 属性: 属性值;


- **分行**

    每条声明语句单独一行，必要时可换行。

    两条声明语句之间不空行。


- **分号**

    所有声明都要用分号（`;`）结尾。


## 属性名（Property） ##


- **书写顺序**

    按字母升序排列，忽略浏览器前缀。


- **大小写**

    属性名均小写。


- **缩写**

    尽量采用缩写。如 `font`、`margin`、`padding` 等。


- **冒号**

    属性名后紧跟冒号（`:`），冒号与属性值之间加一个空格。


## 属性值（Value） ##


- **大小写**

    属性值均小写，除部分滤镜、字体名等。


- **引号**

    属性值为若干单词，则要给值加单引号（`'`）。

    省略 URI 外的引号。


- **单位**

    省略 0 后面的单位。


- **颜色值**

    尽量采用 3 个字符，如 `#aabbcc` → `#abc`。


## 其它 ##

- **CSS 预处理器**

    Sass：http://sass-lang.com/


- **格式化**

    Node.js：https://github.com/beautify-web/js-beautify

    Sublime Text：https://github.com/victorporof/Sublime-HTMLPrettify


- **Hacks**

    尽量避免使用 CSS Hack。

    ```
    .bg {
      background-color:#fff;
      background-color:#fff\9;   /* all IE */
      background-color:#fff\0;   /* IE8-IE10 */
      background-color:#fff\9\0; /* IE9-IE10*/
      *background-color:#fff;    /* IE6-IE7 */
      _background-color:#fff;    /* IE6 */
    }

    :root .bg {
      background-color:#fff\0;   /* IE9+opera */
      background-color:#fff \0;  /* IE9 */
    }

    @media screen and (-ms-high-contrast: active), (-ms-high-contrast: none){
      /* IE10 */
    }
    ```


- **协议**

    如果资源同时支持 `http` 与 `https` 访问，省略资源 URL 地址前的协议部分（`https?:`）。


- **校验**

    w3c 的在线校验工具：http://jigsaw.w3.org/css-validator/。


- **闭合浮动**

    ```
    .clearfix:before,
    .clearfix:after {
      clear: both;
      content: ’’;
      display: table;
    }

    .clearfix{ *zoom;}
    ```

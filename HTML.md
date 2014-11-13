# HTML 风格参考 #


## 目的 ##


- 一致性
- 语义化
- 可读性
- 模块化
- 结构表现行为分离


## 文档 ##


- **类型声明**

    必须有文档类型声明，采用 HTML5：`<!DOCTYPE html>`。


- **IE 兼容模式**

    采用该版本浏览器的标准模式进行渲染。

    ```
    <meta http-equiv="X-UA-Compatible" content="IE=Edge">
    ```


- **基础结构**

    必须有完整的基础结构。

    ```
    <!DOCTYPE html>
    <html>
    <head>
      <meta charset="utf-8" />
      <title> ... </title>
    </head>
    <body>
      ...
    </body>
    </html>
    ```


- **页面编码**

    统一采用 UTF-8 （无 BOM） 编码：`<meta charset="utf-8">`。

    必须在 `<title>` 标签前。


- **代码注释**

    添加必要的注释以提高可读性，如：

    ```
    <!-- 模块名称 开始 -->
    <div> ... </div>
    <!-- //模块名称 结束 -->

    <ul>
      <!—- 循环体 开始 -->
      <li> ... </li>
      <!-- //循环体 结束 -->
    </ul>
    ```


- **代码缩进**

    采用空格作为缩进符，长度为 2。


- **大小写**

    标签名、属性名，属性值（除数据外），均小写。

    ```
    <img src="google.png" alt="Google">
    ```


- **行尾空格**

    必须移除无用的行尾空格。

    > 大部分编辑器都有自动移除尾部空格的功能，比如 Sublime Text。


## 标签（Tag） ##


- **嵌套**

    在保持合理的语义化前提下，尽量减少嵌套。


- **闭合**

    所有标签必须闭合。

    ```
    <meta charset="utf-8" />
    <base target="_blank" />
    <br />
    ```

- **h1~6**

    一个页面只能有一个 `h1`，应该将 `h1` 用作主标题（最重要的），其后是 `h2`（次重要的），依此类推。

- **meta**

    声明顺序：`charset`、`x-ua-compatible`、`viewport`、`keywords`、`description`。

    所有 `meta` 标签，位于 `title` 标签前。


- **link**

    对于 CSS，不要设置 `type` 属性。

    书写顺序：`<link rel="" href="" />`。


- **style**

    不要设置 `type` 属性。


- **script**

    对于 JavaScript，不要设置 `type` 属性。


- **img**

    必须设置非空的 `src` 与 `alt`。


- **form**

    必须有 `action` 属性。
    
    对于表单元素（特别是带有用户交互且数据提交的），应包含在 `form` 中。


- **input**

    必须有 `type` 属性。


- **button**

    必须有 `type` 属性。


- **iframe**

    尽量不用 `<iframe>`。


## 属性（Attribute） ##


- **引号**

    属性值始终加双引号。


- **空格**

    等号前后不留空格。

    删除属性间多余的空格，即两个属性之间只能有一个空格。


- **书写顺序**

    ```
    <* title="" id="" class="" tabindex="" accesskey="" style="" ... >
    <img src="" alt="" />
    <a href="" target=""> ... </a>
    <form name="" action="" method=""> ... </form>
    <input type="" name="" data-xxx="" value="" checked />
    ```


## 其它 ##


- **格式化**

    Node.js：https://github.com/beautify-web/js-beautify

    Sublime Text：https://github.com/victorporof/Sublime-HTMLPrettify


- **协议**

    如果资源同时支持 `http` 与 `https` 访问，省略资源 URL 地址前的协议部分（`https?:`）。


- **校验**

    w3c 的在线校验工具：http://validator.w3.org/nu/。


- **特殊符号**

    `<`、`&` 必须转义。

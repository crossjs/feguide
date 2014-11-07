# JSHint 选项 #


以下是对 [JSHint Options](http://jshint.com/docs/options/) 的简注。


## 加强参数（Enforcing Options） ##


本类参数设为 `true`，JSHint 会产生更多告警，所以叫“加强”。


- **bitwise**

    禁用位运算符，如 `^`、`|`、`&` 等。


- **camelcase**

    变量采用驼峰（camelCase）或全大写下划线（UPPER_CASE）风格命名。


- **curly**

    循环和条件语句的代码块，必须包含在花括号（`{}`）中。


- **eqeqeq**

    使用 `===` 和 `!==` 替代 `==` 和 `!=`。


- **es3**

    需要兼容 ECMAScript 3 规范。


- **forin**

    在 `for in` 循环中，必须使用 `hasOwnProperty` 过滤原型链中的属性。


- **freeze**

    禁止修改原生对象（如 `Array`, `Date`等）的原型，包括改写或新增原型方法。


- **immed**

    立即执行函数，必须包含在括号（`()`）中。


- **indent**

    指定代码缩进宽度（空格数）。


- **latedef**

    变量必须先声明再使用。


- **newcap**

    构造函数名首字母必须大写。


- **noarg**

    禁止使用 `arguments.caller` 和 `arguments.callee`。


- **noempty**

    禁止出现空的代码块，不包括空函数。


- **nonbsp**

    禁止不换行空格（`&nbsp;`）。


- **nonew**

    禁止使用构造函数时不把结果赋给一个变量。


- **plusplus**

    禁止使用 `++` 和 `--`。


- **quotemark**

    统一使用单引号（`single`）或双引号（`double`），或保持一致性（`true`）。


- **undef**

    禁止使用未定义的变量。


- **unused**

    禁止定义未使用的变量或函参，但允许未使用的函参后跟随已使用的函参。另有可选项：`strict`（检查全部）、`var`（仅检查变量，不检查函参）


- **strict**

    强制使用 ECMAScript 5 的严格模式，即在函数开头处加入 `'use strict';`。


- **maxparams**

    函数参数数量，即最多允许定义多少个参数。


- **maxdepth**

    代码嵌套深度，即最多允许代码嵌套多少层。


- **maxstatement**

    每个函数允许的最大语句数。


- **maxcomplexity**

    单个文件允许的最大循环复杂度。


- **maxlen**

    一行中允许的最大字符数。


## 放松参数（Relaxing Options） ##


本类参数设为 `true`，JSHint 会产生更少告警，所以叫“放松”。


- **asi**

    允许省略分号。


- **boss**

    允许在 `if`，`for`，`while` 等条件语句中使用赋值。

    不建议开启。必要时可在赋值语句外多包一层括号以通过校验，如： `for (var i = 0, person; (person = people[i]); i++) {}`。


- **debug**

    允许 `debugger` 语句。


- **eqnull**

    允许 `==null`。


- **esnext**

    允许使用 ECMAScript 6 特性。


- **evil**

    允许使用 `eval`。


- **expr**

    允许应该出现赋值或函数调用的地方使用表达式。

    ```
    function test(n) {
        n || (n = 1);
    }
    ```


- **funcscope**

    允许在控制体内定义变量而在外部使用。

    ```
    function test() {
        if (true) {
            var x = 0;
        }

        x += 1; // Default: 'x' used out of scope.
                // No warning when funcscope:true
    }
    ```


- **globalstrict**

    允许全局严格模式，即在非函数内部使用 `'use strict';`。


- **iterator**

    允许 `__iterator__`。


- **lastsemic**

    允许单行控制块省略分号。

    ```
    var name = (function() { return 'Anton' }());
    ```


- **laxbreak**

    允许不安全的行中断（与 `laxcomma` 配合使用）。

- **laxcomma**

    允许逗号开头的编码样式。

    ```
    var obj = {
        name: 'Anton'
      , handle: 'valueof'
      , role: 'SW Engineer'
    };
    ```

- **loopfunc**

    允许在循环中定义函数。

    在循环中定义函数经常会导致错误：

    ```
    var nums = [];

    for (var i = 0; i < 10; i++) {
        nums[i] = function (j) {
            return i + j;
        };
    }

    nums[0](2); // Prints 12 instead of 2
    ```

    修改的方法是使用闭包：

    ```
    var nums = [];

    for (var i = 0; i < 10; i++) {
        (function (i) {
            nums[i] = function (j) {
                return i + j;
            };
        }(i));
    }
    ```


- **maxerr**

    JSHint 中断扫描前允许的最大错误数。默认 50。


- **moz**

    允许使用 Mozilla JavaScript 扩展。


- **multistr**

    允许多行字符串。


- **notypeof**

    允许无效的 typeof 操作值。

    ```
    // 'fuction' instead of 'function'
    if (typeof a == "fuction") { // Invalid typeof value 'fuction'
        /* ... */
    }
    ```


- **proto**

    允许 `__proto__`。


- **scripturl**

    允许（在 URL 中）使用 `javascript:;`。


- **shadow**

    允许变量shadow

    ```
    function test() {
        var x = 10;

        if (true) {
            var x = 20;
        }

        return x;
    }
    ```


- **sub**

    允许 `person['name']`。

    JSHint 推荐使用 `person.name ` 代替 `person['name']`。


- **supernew**

    允许 `new function() { ... }` 和 `new Object`;

    此结构有时用于创建单例：

    ```
    var singleton = new function() {
        var privateVar;

        this.publicMethod  = function () {}
        this.publicMethod2 = function () {}
    };
    ```


- **validthis**

    允许严格模式下在非构造函数中使用 `this`。


- **noyield**

    允许发生器中没有 `yield` 语句


## 环境参数（Enviroments） ##


预定义一些全局变量，如node等，没什么好理解的。


- **browser**

    包含浏览器的全局变量，包括 `document`、`navigator`、以及 HTML5 的 `FileReader` 等，但不包括 `alert` 与 `console` 等。


- **couch**

    包含由 `CouchDB` 引入的全局变量。


- **devel**

    包含 `alert` 和 `console` 等。


- **dojo**

    包含由 `Dojo Toolkit` 引入的全局变量。


- **jquery**

    包含由 `jQuery` 库引入的全局变量。


- **mootools**

    包含由 `MooTools` 框架引入的全局变量。


- **node**

    告诉 JSHint 代码运行在 Node.js 环境。


- **nonstandard**

    包含非标准但广泛采用的全局变量，如 `escape` 与 `unescape`。


- **phantom**

    告诉 JSHint 代码运行在 PhantomJS 环境。


- **prototypejs**

    包含由 `Prototype` 框架引入的全局变量。


- **rhino**

    告诉 JSHint 代码运行在 Rhino 环境。


- **worker**

    告诉 JSHint 代码运行在 Web Worker。


- **wsh**

    告诉 JSHint 这是 `Windows Script Host` 脚本。


- **yui**

    包含由 `YUI` 框架引入的全局变量。

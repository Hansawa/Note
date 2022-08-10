1. 关键字
   
   1. const：声明常量，该常量不能被二次声明，作用域为局部
   
   2. let：声明变量，作用域为局部

2. (...args) => {}：匿名函数，其中 ...args 意为可传入不定数量的参数

3. 变量加不加 () 意思都是一样的
   
   ```js
   variable === (variable) // 返回 true
   ```

4. {} 不表示函数作用域时，表示一个对象，其中的 property 为一个个键值对

5. 匿名函数
   
   ```js
   // 单独定义的匿名函数，注意前后有括号
   (function (){
       function_body
   })// 使用时只需在后面添加括号
   
   // 箭头函数（匿名函数的一种）的使用
   functionName = parameter => function_body_only_one_expression
   // 函数体只能为一条表达式
   functionName(a) // 返回函数运行的结果
   
   // 多箭头函数的使用
   functionName = para1 => para2 => function_body
   functionName(a) // 返回 para2 => function_body，此时第一个参数的值为 a
   functionName(a)(b) // 返回函数运行的结果
   // 用处：可以不用同时设置函数的多个参数
   functionName = para1 => para2 => function_body
   // 其他程序段，获得 a
   func = functionName(a) // 将第一个参数设置成 a，返回第一个参数为 a 的第二个匿名函数
   // 其他程序段，获得 b
   func(b) // 将第二个参数设置成 b，返回函数运行的结果
   ```

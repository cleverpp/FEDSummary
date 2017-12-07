## JSON.stringfy()
1. 非数组对象的属性不能保证以特定的顺序出现在序列化后的字符串中。
2. 布尔值、数字、字符串的包装对象在序列化过程中会自动转换成对应的原始值。
3. undefined、任意的函数以及 symbol 值，在序列化过程中会被忽略（出现在非数组对象的属性值中时）或者被转换成 null（出现在数组中时）。
4. 所有以 symbol 为属性键的属性都会被完全忽略掉，即便 replacer 参数中强制指定包含了它们。
5. 不可枚举的属性会被忽略

举例：
```
var data=[1,'2',true,null,{a:'a',b:undefined},Object];
JSON.stringify(data);
// "[1,"2",true,null,{"a":"a"},null]"
```

## 箭头函数
1. 箭头函数没有自己的this，箭头函数体内的this是定义时所在的对象，而不是使用时所在的对象。所以，箭头函数的this是固定的。
2. 不可以当作构造函数，也就是说，不可以使用new命令，否则会抛出一个错误。
3. 不可以使用arguments对象，该对象在函数体内不存在。如果要用，可以用 rest 参数代替。
4. 如果箭头函数在其他函数的内部，它也将共享该函数的arguments变量。
5. 除了this，以下三个变量在箭头函数之中也是不存在的，指向外层函数的对应变量：arguments、super、new.target。
6. 不可以使用yield命令，因此箭头函数不能用作 Generator 函数。
7. 由于箭头函数没有自己的this，所以当然也就不能用call()、apply()、bind()这些方法去改变this的指向。
```
// ES6
function foo() {
  setTimeout(() => {
    console.log('id:', this.id);
  }, 100);
}

// ES5
function foo() {
  var _this = this;

  setTimeout(function () {
    console.log('id:', _this.id);
  }, 100);
}
```

## 变量的解构赋值
1. 如果解构不成功，变量的值就等于undefined。
2. 只要某种数据结构具有 Iterator 接口，都可以采用数组形式的解构赋值
3. 解构赋值允许指定默认值,ES6 内部使用严格相等运算符（===），判断一个位置是否有值。所以，如果一个数组成员不严格等于undefined，默认值是不会生效的。
举例：
```
let [a, [b=1], c] = [1, [null] ]; 
console.log(a,b,c);
// 1,null,undefined
```

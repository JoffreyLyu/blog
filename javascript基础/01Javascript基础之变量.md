## 01JavaScript基础之变量

**前言**

众所周知JavaScript数据类型包含两种：

- 基础类型
- 引用类型

这两种类型作为变量的值时，分别有以下不同：

- 访问方式
- 复制变量值
- 参数传递



### 一、访问的方式

- **基础类型（按值访问）**

  可以操作保存在变量种实际的值

- **引用类型 （按引用访问）**

  引用类型的值是保存在内存中的对象，由于JavaScript不允许直接访问内存的位置，操作对象时，实际是在操作对象的引用而不是实际对象

如下图所示：



![](C:\Users\Administrator\Desktop\blog\javascript基础\img\01-1.png)

### 二、复制变量值

- **基础类型**

基础类型复制值时，会在变量对象中创建一个新值，然后把该值复制到新变量分配的位置上，两个变量相互独立互不影响，例如：

```javascript
var num1 = 5
var num2 = num1
```

如图所示：

![](C:\Users\Administrator\Desktop\blog\javascript基础\img\01-2.png)

- **引用类型**

  应用类型复制值时会同样将变量对象中的值复制一份放到新变量分配的空间中，不同的是该值的副本是一个指针，复制操作结束后，会指向堆内存中的同一个对象，通过其中一个变量改变对象，会同时影响到另一个变量，例如:

  ```javascript
  var obj1 = new Object();
  var obj2 = obj1;
  obj1.name = "tom";
  alert(obj2.name); // tom
  ```

  内存过程如图所示：

  ![](C:\Users\Administrator\Desktop\blog\javascript基础\img\01-3.png)

  

### 三、传递参数

ECMAScript中的所有函数的参数都是按值传递的。**可以理解为把函数外的参数复制给函数内部的参数，就跟复制变量值一样。**

根据第二点，基础类型复制，操作时相互独立的，不会影响函数外，但当向参数传递引用类型时，会把这个值在内存中的地址复制给一个局部变量，这个局部变量变化会影响到函数外。例如：

```javascript
var obj = new Object();
obj.name = "jack";
function f(obj) {
	obj.name = "tom"
}
f();
alert(obj.name); // tom
```


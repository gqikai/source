---
title: JavaScript变量提升
date: 2016-06-17 17:59:27
tags:
- JS
---

变量声明会被提升到顶部 实现不会


两种：

```javascript
var fn = function(){}只会提升声明
function fn(){}变量和实现都会提升
```
```javascript
//在全局对象中声明两个全局函数,反模式
function foo() {
    alert("global foo");
}

function bar() {
    alert("global bar");
}

//定义全局变量
var v = "global var";

function hoistMe() {
    alert(typeof foo); //function
    alert(typeof bar); //undefined
    alert(v); //undefined

    //为什么bar函数和变量v是未定义而不是全局变量中定义的相应的函数变量呢？
    //因为函数里面定义了同名的函数和变量，无论在函数的任何位置定义这些函数和
    //和变量，它们都将被提升到函数的最顶部。

    foo(); //local foo
    bar(); //报错，缺少对象

    //函数声明，变量foo以及其实现被提升到hoistMe函数顶部
    function foo() {
        alert("local foo");
    }

    //函数表达式,仅变量bar被提升到函数顶部，实现没有被提升
    var bar = function () {
        alert("local bar");
    };

    //定义局部变量
    var v = "local";
}
```
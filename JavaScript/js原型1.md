# JS原型的深入理解 
## 一、关于JS原型的理解先明确几个概念 
1. JS中所有事物都是用对象封装的，
    - 普通对象是对象  
      ```javascript
      var commonObj ={name ='kingbox'}
      ```
    - 基础类型数据是对象。
      ```javascript
      var num =3.14;
      var bol = false;
      var str ='kingbox';
      ```
      为什么基本类型也是对象？ 因为基本类型也有__proto__属性,基本类型能够通过原型链获取到Object原型定义的方法。
    - 函数、日期、数组都是对象。
      ```javascript
      var fuc =function(){};
      var date = new Date();
      var arr = ['a','b','c'];
      ```
2. 所有的对象都是函数创建的
    - 函数本身也是函数创建的，只不过函数的的创建函数是Function，一个Native函数。    
    对一个变量赋值，该值要么是已经存在的变量，要么就是新创建的对象。关于对象的创建，js有两种基本的创建方式-字面量和构造函数。   
      ```javascript
      //字面量方式创建对象
      var Person = {};//相当于var Person = new Object();
      var Person = {
      name:'Nike';
      age:29;  
      }

      //构造函数方式创建对象
      var Person = new Object();
      Person.name = 'Nike';
      Person.age = 29;
      ```    
      字面量创建不过是一种语法糖，解释器会把字面量转化成构造函数创建，其实对象的创建只有调用构造函数创建一种方式。  
      所有函数都可以在前面添加new 当做构造函数使用。那么问题来了，new 到底是怎么使用构造函数的呢。
    - new的工作机理   
    在研究new的工作机理前，需要了解一下function对象的结构。
      ```javascript
      function Person(){}
      ```   
      Person函数的成员情况如下
      ```
      ƒ Person () {}
        arguments:null
        caller:null
        length:0
        name:'Person'
        prototype:{constructor: ƒ}
          constructor:ƒ Person () {}
          __proto__:Object
        [[FunctionLocation]]:@ e:\Jswork\KingboxtestProto.js:1
        [[Scopes]]:Scopes[1]
        __proto__:function () { [native code] }
      ```
      所有函数都有一个属性——prototype，这个属性是一个对象，对象中有constructor，这个constructor是用来指向函数对象本身的。new

    

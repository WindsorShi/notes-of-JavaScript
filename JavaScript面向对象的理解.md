# JavaScript面向对象思想的理解
###1、JavaScript是基于原型（prototype）的面向对象方式  
  在这种方式中对象（object）则是依靠构造器（constructor）利用原型（prototype）构造出来的：比如  
  工厂造一辆车，工人和机器 ( 相当于 constructor) 利用各种零部件如发动机，轮胎，方向盘 ( 相当于 prototype 的各个属性 ) 将汽车构造出来。  
 （1）原型方式中的*构造器* (constructor) 和*原型* (prototype) 本身也是其他对象通过原型方式构造出来的**对象**。  
 （2）对象的行为、状态都属于对象本身，并且能够一起被继承。   
 （3）除内建对象 (build-in object) 外，不允许全局对象、方法或者属性的存在，也没有静态概念。  
      **所有语言元素 (primitive) 必须依赖对象存在**。    
      但由于函数式语言的特点，语言元素所依赖的对象是随着运行时上下文 (context) 变化而变化的，    
      具体体现在 *this 指针的变化*。
  
###2、JSON(JavaScript Object Notation)是ECMAScript设计出的数据结构  
      这种数据交互格式的结构可以脱离语言。
  （1） 6种基本数据类型和JSON 构造语法就能基本实现面向对象编程  
  （2）开发者可以随意地用**字面式声明（literal notation）方式**来构造一个对象，并对其不存在的属性直接赋值，  
       或者用 delete 将属性删除 ( 注：JS 中的 delete 关键字用于删除对象属性）   
           var person = {  
               name: “张三”,   
               age: 26,   
               gender: “男”,   
               eat: function( stuff ) {   
               alert( “我在吃” + stuff );   
              }   
             };   
               person.height = 176;   
               delete person[ “age” ];  

###3、ECMAScript允许通过构造器（constructor）创建对象。每个构造器实际上是一个函数（function）对象,该函数对象  
  含有一个“prototype”属性用于实现基于原型的继承（prototype-based inheritance）和共享属性（shared properties）。
   
 // 构造器 Person 本身是一个函数对象  
 function Person() {   
// 此处可做一些初始化工作  
 }   
// 它有一个名叫 prototype 的属性  
 Person.prototype = {   
    name: “张三”,   
    age: 26,   
    gender: “男”,   
    eat: function( stuff ) {   
        alert( “我在吃” + stuff );   
    }   
 }   
// 使用 new 关键字构造对象  
 var p = new Person();    
 
###4、每个由构造器创建的对象拥有一个指向构造器 prototype 属性值的隐式引用（implicit reference），  
      这个引用称之为原型（prototype）。   
      进一步，每个原型可以拥有指向自己原型的隐式引用（即该原型的原型），  
      如此下去，这就是所谓的原型链（prototype chain）
 ![原型链](http://blog.jobbole.com/wp-content/uploads/sites/2/2013/04/image001.png "原型链")
 
###5、基于原型的继承方式，虽然实现了代码复用，但其行文松散且不够流畅，可阅读性差，  
       不利于实现扩展和对源代码进行有效地组织管理。    
       不得不承认，类式继承方式在语言实现上更具健壮性，且在构建可复用代码和组织架构程序方面具有明显的优势。
       使用Simple Inheritance库提供的 extend 方法声明类非常简单
 
 
 

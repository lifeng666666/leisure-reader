
# 6/20 
 - JavaScript实现Base64编码转换
 - JavaScript移动端/Android/i生成base64
 - JavaScript上传图片那些安卓手机图片竖向摆放，需要旋转90度  http://www.lifeng666.top/webapp/shangchuang.html
 - 上传图片转为base64格式预览并压缩图片（不兼容IE9以下浏览器，兼容移动端ios,android）
 - 利用canvas中toDataURL()将图片转为dataURL(base64)的方法详解
 - JavaScript移动端/Android/i生成base64
 - 安卓、ios上传图片图片预览旋转问题
 - JavaScript在移动端使用缓存
 - HTML5 和移动端 WebView 缓存机制解析与实战 https://blog.csdn.net/csdnvr/article/details/80130153
 - http://aniublog.com/archives/567
 - DataURL, Blob, File, Image之间的关系与转换
 - 移动端使用localStorage缓存Js和css文的方法(web开发)
 - h5缓存---application应用 h5缓存 /HTML5应用程序缓存Application Cache
 - app嵌入的H5页面的数据埋点总结
 - js监听返回事件 原理：在页面中我们可以使用javascript window history，后退到前面页面，但是由于安全原因javascript不允许修改history里已有的url链接，但可以使用pushState方法往history里增加url链接，并且提供popstate事件监测从history栈里弹出url。既然有提供popstate事件监测，那么我们就可以进行监听
----

    $(function(){
          pushHistory();
          window.addEventListener("popstate", function(e) {
              alert("我监听到了浏览器的返回按钮事件啦");//根据自己的需求实现自己的功能
          }, false);
          function pushHistory() {
              var state = {
                  title: "title",
                  url: "#"
              };
              window.history.pushState(state, "title", "#");
          }
      });
    
    if(window.history && window.history.pushState) {
      $(window).on('popstate', function() {
       var hashLocation = location.hash;
       var hashSplit = hashLocation.split("#!/");
       var hashName = hashSplit[1];
       if(hashName !== '') {
        var hash = window.location.hash;
        if(hash === '') {
         alert("你点击了返回键");
        }
       }
      });
      window.history.pushState('forward', null, './#forward');
     }
 ---   
 
 # 6/21
 - 安卓手机的弹出输入框的bug解决办法？
 - 缓存处理的方法
 - 监听关闭页面事件等
 - 学会用vue做H5爷儿们项目等
 - 好好学习吧兄弟！
 # 6/22 
 - https://www.cnblogs.com/walls/p/6298102.html   解释文件缓存等说明，举例：微信一些页面缓存
 - rem布局：屏幕所以的东西能跟着屏幕而变化，可以自适应！
  所有的尺寸使用rem，只用改动html的fontSize大小（根节点的字体大小）
  如：
  
  ---
  
    屏幕大小   字体               html的fontSize               
    320px     14px                   32px               14/32=0.4375rem                14px
    460px     20.125px               46px               20.125/46=0.4375rem            20.125px
   
   ---
  
  - iscrolljs库，下拉刷新、懒加载等
    hammerjs
    
    ---
         click = touchstart+touchend
    ---
  
  - 原生的websocket
  
  - es6学习： 可以在这   http://jspang.com/posts/2019/01/20/es6.html 学习es6呢！！！ google已经支持ES6了， 有些低版本的浏览器还是不支持ES6的语法  Webpack自动编译
    1、使用Babel把ES6编译成ES5 （可以吧npm--》cnpm，速度更快些）
    
    2、npm init -y 一个项目 ‘-y’是省去了回车确定东西
    
    3、npm install -g babel-cli  安装babel转换的脚手架工具
    
    4、babel src/index.js -o dist/index.js 将文件要编译的文件编译到指定的文件  虽然已经编译了，但还是不能编译成es5语法，还要下载插件
    
    5、npm install --save-dev babel-preset-es2015 babel-cli 
    
    6、babel src/index.js -o dist/index.js 这就可以运行把es6语法转es5
    
    7、我们可以把 babel src/index.js -o dist/index.js 这运行做成webpack一样，将"build":"babel src/index.js -o dist/index.js"加入到package.js文件的script中，在运行转es5就可以直接以cnpm run build了
    
 
 # 7/22
    
    JavaScript常用继承方式主要分为(7种)：原型链继承、构造函数继承、组合继承、原型式继承、寄生式继承、寄生组合继承以及继承多个对象。

1：原型链继承(核心：将父类的实例作为子类的原型)
基本概念：重写原型对象，赋予一个新的对象的实例。基本思想就是让一个原型对象指向另一个父类的实例。

function Super() {
    //基本数据类型
    this.text = 'Hello';
}
Super.prototype.getSuperText = function() {
    return this.text;
}
function Sub() {
    this.subText = 'Word';
}

Sub.prototype = new Super();

const instance = new Sub();
console.log(instance);
特点：非常纯粹的继承关系，实例是子类的实例，也是父类的实例。父类新增原型方法或属性，子类都能访问到。

优点：简单易于操作

缺点：对引用类型数据操作会互相（多个实例之间）影响

function Super() {
    //复杂对象，也就是引用类型
    this.value = [1, 2, 3, 4];
}
Super.prototype.getSuperValue = function() {
    return this.value;
}
function Sub() {
    this.subText = 'Word';
}

Sub.prototype = new Super();

const instance1 = new Sub();
const instance2 = new Sub();

instance1.value.push(5);
console.log(instance2.value);

// (5) [1, 2, 3, 4, 5]
2：构造函数继承
//定义构造函数
function Super(){
    this.value = [1, 2, 3, 4];
}
//新增属性getSuperValue
Super.prototype.getSuperValue = function() {
    return this.value;
}
//sub每次执行都要重新调用
function Sub(){
    Super.call(this);
}

const instance1 = new Sub();
instance1.value.push(5);
console.log(instance1.value);
// (5) [1, 2, 3, 4, 5]

const instance2 = new Sub();
console.log(instance2.value);
// (4) [1, 2, 3, 4]
构造函数的特点：（对引用数据类型没有影响）上面的代码输出instance1是1,2,3,4,5，instance2是1,2,3,4。这是因为sub每次在执行时都是重新调用了一个super.call()，而且构造函数在构建对象的过程中，每次都是创建了一个新的object，因此每次调用sub都会执行一遍super，每次执行时都会有申请一个新的内存空间，所以得到的两个value值是不一样互不影响的。

缺点：在整个构造函数的基础过程中，上面的代码并没有使用proto和prototype的属性，没有使用的话那么原型链就没有接上。所以说，构造函数基础只能继承父类的实例属性和方法，不能继承原型链上的属性和方法。

3：组合继承
通过调用父类构造，继承父类的属性并保留传参的优点，然后通过将父类实例作为子类原型，实现函数复用。

保留了构造函数继承与原型链继承的优点。但是执行了两次Person，属性重复了。

function Person(name) {
    this.name = name;
    this.value = ["head", "body", "legs"];
}
Person.prototype.getName = function() {
    return this.name;
};

// 构造函数继承
function Teacher(name, school){
    // 执行又一次Person
    Person.call(this, name);
    this.school = school;
}

// 原型链继承
// 执行一次Person
Teacher.prototype = new Person(); 
const Eric = new Teacher("Eric",27);
Eric.getName();
// 输出：Eric



// prototype构造器指回自己 
Teacher.prototype.constructor = Teacher;

Teacher.prototype.getSchool = function() {
    return this.school;
};
特点：既可以继承实例属性和方法，也可以继承原型属性和方法。既是子类的实例也是父类的实例，不存在引用属性共享的问题。可以传参，函数可复用。

缺点：调用两次父类构造函数，生成了两份实例。

4：原型式继承
借助原型可以基于已有的对象创建新的对象，同时还不必因此创建自定义类型。

原理：（本质）利用一个空对象作为一个中介。

const lakers = {
    name: "lakers",
    value: ["Micheal", "Wade", "Kobe"]
};

const lakers1 = Object.create(lakers);
const lakers2 = Object.create(lakers);

lakers1.value.push('Fish');
console.log(lakers);
模拟Object.create()

object.create()原理：用一个函数包装一个对象，然后返回这个函数的调用，这个函数就变成了一个可以随意添增属性的实例或对象。

Object.prototype.create = function(obj) {
    function Fun() {}
    Fun.prototype = obj;
    return new Fun();
}
缺点有两点：第一点是无法传递参数，第二点是引用类型存在变量的污染。

5：寄生式继承
寄生式继承的思路与寄生构造函数和工厂模式类似，即创建一个仅用于封装继承过程的函数。

目的：在原型式继承的基础上，寄生增加了一些新的方法和属性。

它的特点同原型式继承一样，也是无法传递参数，而且引用的数据类型也容易存在样式污染。

Object.createNew()

Object.prototype.createNew = function(obj){
    var newObj = Object.create(obj);
    //获取长度等于一个function
    newObj.getLength = function(){ ... };
    return newObj;
}
6：寄生组合继承
目的：为了解决数据重复拷贝两遍的问题。

Super只执行一次。

//定义Super构造函数
function Super(name) {
  this.name = name;
  this.value = ["Hello", "Word"];
}
//在super的原型链添加一个getName
Super.prototype.getName = function() {
  return this.name;
};
//定义Sub
function Sub(name, age) {
  //调用构造函数继承
  Super.call(this, name);
  this.age = age;
}

let prototype = Object.create(Super.prototype);
prototype.constructor = Sub;
Sub.prototype = prototype;

Sub.prototype.getAge = function(){
  return this.age;
}

const instance1 = new Sub("Eric", 23);
const instance2 = new Sub("Vico", 23);
instance1.value.push("!");
instance2.value.push("!!");
7：继承多个对象
借助原型式继承Object.create拿到SuperClass，也就是父类，拿到父类的prototype之后把它赋给ClassOne，再然后我们将ClassTwo的prototype使用一个Object.assign，一个对象的拷贝，把它拷贝到ClassOne里面来，然后最后ClassOne.prototype.constructor等于ClassOne。

也就是使用一个Class.assign把所有我们想要继承的父类的prototype全部组合到一起完成一个拷贝，之后再赋给对象。

function 

ClassOne.prototype = Object.create(SuperClass.prototype);

Object.assign(ClassOne.prototype, ClassTwo.prototype);

ClassOne.prototype.constructor = ClassOne;
    
   

# 学习
平时学习的记录
# 2019/6/11
https://www.cnblogs.com/ccblogs/p/5261292.html，多Tabs的横向滚动插件（支持Zepto和jQuery）
，https://www.helloweba.net/javascript/374.html，基于Zepto的内容滑动插件：zepto.hwSlider.js

使用hammer.js实现移动端webAPP手势滑动切换页面
，基于zepto.js的移动端H5单页面跟随手指滑动切换控件pageSlider
http://www.jq22.com/jquery-pluginsTabs-1-jq
前端库，常用插件等可以玩这里找 http://www.jq22.com/jquery-plugins%E9%AA%8C%E8%AF%81-1-jq

JavaScript生成随机的验证码，pc、移动端图片上传的方法，图片生成的框架，canvas生成图片的使用等，常用的正则表达式的记录，常用js方法等
-----
(function() {
    var verCode = document.getElementById('verCode'),
        Ps = document.getElementsByTagName('p');
    verCode.style.height = '30px';
    var i=0; 
    function randomNum() {
        verCode.style.height = 'auto';
        // var p = document.createElement('p');
        // verCode.appendChild(p);
        // 方法一：
        var randomNum = ('000000' + Math.floor(Math.random() * 999999)).slice(-6);

        // 方法二：随机字符，从数组的尾部选取元素6个数字
        // var randomNum = Math.random().toString().slice(-6);


        // 方法三： 四舍五入取到小数点后六位数，从数组的尾部选取6个元素
        //var randomNum = Math.random().toFixed(6).slice(-6); 

        // 方法四：for循环
        //var randomNum = "";
        // for (var i = 0; i < 6; i++) {
        //   randomNum += Math.floor(Math.random() * 10);
        //}

        // 公共部分    
        verCode.innerHTML += "<p>" + randomNum + "</p>";
        i++;
        if(i>6){
            clearInterval(timer); 
        }
        
    }
    // 公共部分
    var timer = setInterval(randomNum, 1000); 
    
})()

-------

# 6/12 异步加载的几种方式学习
图片上传的方法的使用
templatejs-->art-template.js的使用
js数组的一些操作
移动端图片点击默认预览事件去除
----
$("img").on('click', function(e) {
     e.preventDefault();
});
----

# 6/13
-css、js等文件缓存的添加，
https://blog.csdn.net/qq_29132907/article/details/79390605
-localStorage的黑科技-js和css缓存机制
https://www.jb51.net/article/104745.html

#zeptojs的图片懒加载 picLazyLoad.min.js
http://ons.me/wp-content/uploads/2014/05/picLazyLoad/

-JS实现图片上传多次上传同一张不生效的处理方法
    解决办法, 在删除方法里置空input
    $("#id").find('input').val('');
    拿到input所在的位置, 找到这个input, 然后置空
    还有一种方法是来回切换input的属性
    每次删除图片后, 改变input的type属性
    先变成text, 删除完成后变回file, 方便删除后能继续上传

    $("#inputId").attr('type','text');
    $("#inputId").attr('type','file');
    
 -art-template.js的{{if}}{{/if}}如何使用   
 HTML5在移动端如何加快图片加载速率
 -HTML5的rem布局在手机上页面先缩小在放大的bug如何解决
    
    --
    /*  获取图片的base64码
      * @param {obj}img图片dom对象
       * */
      function getBase64Image(img) {
        let canvas = document.createElement("canvas");
        canvas.width = img.width;
        canvas.height = img.height;
        let ctx = canvas.getContext("2d");
        ctx.drawImage(img, 0, 0, img.width, img.height);  //绘制相同图片
        return canvas.toDataURL("image/png"); //转换成base64数据
      }
    --
    
-H5页面在移动端触发点击事件的时候，被点击的元素会出现背景变黑，闪烁问题，体验非常差！
解决方法如下：
在被点击的元素设置css：
-webkit-tap-highlight-color:transparent;

图片压缩地址：
- https://think2011.net/localResizeIMG/test/index.html，
- https://tinypng.com/

- 移动端怎么加快页面显示速度？
1. 必要页面进行缓存
2. 缓存改动少的资源文件
3. 配置CDN
4. 压缩图片，压缩代码
5. AMD，CMD开发方式，按需加载

- javascript模块化之CommonJS、AMD、CMD、UMD、ES6
- 移动web缓存介绍 
-  移动端网站提升页面加载性能的优化技巧 http://www.mahaixiang.cn/ydseo/1198.html
- JS移动端实现图片上传多次上传同一张不生效的处理方法

# 6/14 
 - 将请求提取到公共部分，这部分可能经常会修改，提取更能快捷修改！
 - 如何引用外部js文件的变量  
 - css3、html5新特性 渐变的使用
 - 欢迎来到php自学网 ： http://www.zixuephp.net/index.html
 - CSS中伪类及伪元素用法详解
 - 模板语法学习
 - span标签中实现换行
 --
     span{
        word-break:normal; 
        width:auto; 
        display:block; 
        white-space:pre-wrap;
        word-wrap : break-word ;
        overflow: hidden ;
    }  
 --
 - JavaScript的MultipartFile 上传图片
 - zepto的fadeIn方法，在显示透明的遮罩层(如opacity: 0.5)时，会把该图层最终的opacity设置为1，这显然不符合我们的预期
   通过css3动画transition的方式来达到显隐的效果
   给遮罩层设置样式
 --
     .mask {
         display: none;
         position: fixed;
         top: 0;
         left: 0;
         width: 100%;
         height: 100%;
         background: rgba(0, 0, 0, .5);
         opacity: 0;
         transition: opacity 1s;
     }
 -- 
  $('.mask').show()会渐变的显示遮罩层(不要使用fadeIn) 
  $('.mask').fadeOut()会渐变的隐藏遮罩层
  - JavaScript使用MultipartFile上传图片的图片如何在本地预览
  
  # 6/15
  - jQuery的MultipartFile上传图片
  - 用AJAX异步提交表单上传多个文件（type=‘file‘）案例
  - ajax使用FormData对象实现批量文件上传（前后端）
  - JavaScript如何向对象添加属性
  - from表单上传图片
  - JavaScript如何把object对象存储到本地
  - JavaScript的判断类型
  - 请问js中得到的一个object对象该怎样保存到本地呢？
---
    function SaveInfoToFile(folder, fileName) {
    var filePath = folder + fileName;
    var fileInfo = "hahahaha";
    var fso = new ActiveXObject("Scripting.FileSystemObject");
    var file = fso.CreateTextFile(filePath, true);
    file.Write(fileInfo);
    file.Close();
}
 
仅限 IE
---
- javascript实现将文件保存到本地方法汇总
---
    <script type="text/javascript"> 
        function saveFile(imgUrl) 
        { 
         var oPop=window.open(imgUrl,"","width=1, height=1, top=5000, left=5000"); 
         for(;oPop.document.readyState != "complete"; ) 
         { 
          if(oPop.document.readyState=="complete")break; 
         } 
         oPop.document.execCommand("SaveAs"); 
         oPop.close(); 
        } 
    </script> 
    </head>
    <body>
        <img src="../mytest.jpg" id="theimage" border="0"> 
        <a href="#" onclick="saveFile(document.getElementById('theimage').src)"> 点击这里下载图片 </a> 
    </body>
    </html>
    
    function SaveAs5(imgURL)
      {
      var Pop = window.open(imgURL,"","width=1, height=1, top=5000, left=5000");
      for(; oPop.document.readyState != "complete"; )
      {
      if (oPop.document.readyState == "complete")break;
      }
      oPop.document.execCommand("SaveAs");
      oPop.close();
      }

    <img src="t_screenshot_17616.jpg" id="DemoImg" border="0" onclick="SaveAs5(this.src)">
    
    
    function SaveAs5(imgURL)
      {
      var Pop = window.open(imgURL,"","width=1, height=1, top=5000, left=5000");
      for(; oPop.document.readyState != "complete"; )
      {
      if (oPop.document.readyState == "complete")break;
      }
      oPop.document.execCommand("SaveAs");
      oPop.close();
      }
 
    <img src="../t_screenshot_17616.jpg" id="DemoImg" border="0"> 
    <a href="#" onclick="SaveAs5(document.getElementById('DemoImg').src)"> 点击这里下载图片 </a> 

    
---
----

    var Type = (function() {
                var type = {};
                var typeArr = ['String', 'Object', 'Number', 'Array','Undefined', 'Function', 'Null', 'Symbol'];
                for (var i = 0; i < typeArr.length; i++) {
                    (function(name) {
                        type['Is' + name] = function(obj) {
                            return Object.prototype.toString.call(obj) == '[object ' + name + ']';
                        }
                    })(typeArr[i]);
                }
                return type;
})();
    调用：
    Type.IsFunction(function() {})      Type.IsObject({})。。。。。

----
- javascript将base64编码的图片数据转换为file并提交
- javaScript把项目本地的图片或者图片的绝对路径转为base64字符串、blob对象在上传  https://www.cnblogs.com/puyongsong/p/6005800.html

- 对象存储
--- 
  function SetCookie(name, value) {
        var key = '';
        var Days = 2;
        var exp = new Date();
        var domain = "";
        exp.setTime(exp.getTime() + Days * 24 * 60 * 60 * 1000);
        if (key == null || key == "") {
            document.cookie = name + "=" + encodeURI(value) + ";expires=" + exp.toGMTString() + ";path=/;domain=" + domain + ";";
        }
        else {
            var nameValue = GetCookie(name);
            if (nameValue == "") {
                document.cookie = name + "=" + key + "=" + encodeURI(value) + ";expires=" + exp.toGMTString() + ";path=/;domain=" + domain + ";";
            }
            else {
                var keyValue = getCookie(name, key);
                if (keyValue != "") {
                    nameValue = nameValue.replace(key + "=" + keyValue, key + "=" + encodeURI(value));
                    document.cookie = name + "=" + nameValue + ";expires=" + exp.toGMTString() + ";path=/;domain=" + domain + ";";
                }
                else {
                    document.cookie = name + "=" + nameValue + "&" + key + "=" + encodeURI(value) + ";expires=" + exp.toGMTString() + ";path=/;" + domain + ";";
                }
            }
        }
    }
 
    function GetCookie(name) {
        var nameValue = "";
        var key = "";
        var arr, reg = new RegExp("(^| )" + name + "=([^;]*)(;|$)");
        if (arr = document.cookie.match(reg)) {
            nameValue = decodeURI(arr[2]);
        }
        if (key != null && key != "") {
            reg = new RegExp("(^| |&)" + key + "=([^(;|&|=)]*)(&|$)");
            if (arr = nameValue.match(reg)) {
                return decodeURI(arr[2]);
            }
            else return "";
        }
        else {
            return nameValue;
        }
    }
---    
    注意：JSON.stringify()中不要忘了“i”,stringify而不是stringfy！ 
    然后取出person的对象你可以用JSON.parse(); 
    person = JSON.parse(localStorage.getItem(“person”));

- js 如何把input的file图片对象如何存储到本地

# 6.17
 - JavaScript的移动端input file点击不能选择图片是什么问题？
 - 移动端H5页面阻止图片和文字被选中
 - 上传图片：https://www.cnblogs.com/hehuiself/p/7099861.html
 - 移动端的坑 https://www.cnblogs.com/baihuaxiu/p/6654496.html
 - JS监听浏览器的返回、后退、上一页按钮的事件方法
 - JavaScript移动端去除历史页面
 - 移动端H5页面跳转重定向
 - JavaScript移动端html文件如何缓存
 - 移动web缓存介绍 http://caibaojian.com/mobile-cache.html
 - 利用HTML5的history.replacestate()修改当前页面的URL
 - JavaScript移动端html的zeptojs懒加载图片 http://ons.me/484.html
 - javascript如何去除跳转的历史记录
 - javascript:window.history.forward(1) JS清除网页历史记录，屏蔽后退按钮
 - 会在window.history新增一条历史记录，如果想清除掉这条记录（不清除的话点击返回会回到上一个hash值的页面），可以使用
window.location.replace(window.location.href.toString().replace(window.location.hash, '')+"#"+"hash的值")
  - JS(javascript)跳转阻止后退到上个页面，没有历史记录  js的window.location.replace('要转向的页面')，这样不会有历史记录
  
# 6.18 
- 显示图片的两种方法：
---  
    <input type="file" id="FileTypeIcon">
           <img src="" class="img" />

    $("#FileTypeIcon").live('change', function () {
           var file = this.files[0];//获取文件信息
            if (window.FileReader)
            {
                var reader = new FileReader();
                reader.readAsDataURL(file);
                //监听文件读取结束后事件    
                reader.onloadend = function (e) {
                    $(".img").attr("src",e.target.result);
                };
            }
    ｝
    
    <input type="file" id="FileTypeIcon">
       <img src="" class="img" />
    $("#FileTypeIcon").live('change', function () {
 
        var objurl = getObjectURL(this.files[0]);
        function getObjectURL(file)
        {
            var url = "";
            if(window.createObjectURL!=undefined)
            {
                url = window.createObjectURL(file);
            }
           else if(window.URL!=undefined)
            {
               url = window.URL.createObjectURL(file);
           }
           else if (window.webkitURL != undefined)
           {
               url = window.webkitURL.createObjectURL(file);
           }
            return url;
        }
        $(".img").attr("src", objurl);
    ｝

 ---
 
 
 - JavaScript移动端获取本地图片文件路径地址、绝对路径
 - https://blog.csdn.net/u011500781/article/details/52301886 前端构建工具gulp的使用教程集合
 - JavaScript的移动端在跳动频繁的页面如何缓存处理
 - 移动端进入页面每一项如何缓存在本地 
 - 前端的页面缓存处理：https://www.cnblogs.com/xpbb/archive/2012/09/15/2685916.html
 - 常见的前端问题https://www.cnblogs.com/LiuJL/p/7744473.html
 - 进入页面如何缓存本地 JavaScript进入页面如何缓存本地 https://www.cnblogs.com/lancee/archive/2012/01/04/2312282.html
 

#  6/19
- 移动端常用alert、confirm、toast等弹窗插件，兼容 jQueryZepto
- 完美身份证正则表达式
- 限制HTML的input只能输入数字、英文、汉字...
- JavaScript如何监听后退的事件？
- 原js监听浏览器后退事件
- JavaScript关闭页面 https://www.cnblogs.com/chuhj/p/7131759.html
- js点击返回跳转到指定页面实现过程
- JavaScript如何重定向页面
- 上传图片 http://www.lifeng666.top/webapp/shangchuang.html
- 移动端图片上传预览，如何使图片横向摆放
- https://blog.csdn.net/hsany330/article/details/52471522 exif.js插件的使用
- 移动端图片上传旋转、压缩问题的方法
- 移动端上传照片 预览（解决iOS等设备照片旋转90度的bug）
- https://developer.mozilla.org/zh-CN/docs/Web/API/FileReader

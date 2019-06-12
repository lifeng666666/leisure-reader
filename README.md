# 学习
平时学习的记录
2019/6/11
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

#6/12 异步加载的几种方式学习
图片上传的方法的使用
templatejs-->art-template.js的使用
js数组的一些操作
移动端图片点击默认预览事件去除
----
$("img").on('click', function(e) {
     e.preventDefault();
});
----
-css、js等文件缓存的添加，
https://blog.csdn.net/qq_29132907/article/details/79390605
-localStorage的黑科技-js和css缓存机制
https://www.jb51.net/article/104745.html

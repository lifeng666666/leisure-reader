
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
 

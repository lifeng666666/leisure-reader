# （javascript）string字符串类型转换为number数字类型
 * Number() 、parseInt()、 parseFloat()、new Number() 、*(/)
 
 *  # [javascript代码优化的8点总结](https://www.jb51.net/article/133862.htm)
# [[移动端]移动端上遇到的各种坑与相对解决方案](https://www.cnblogs.com/baihuaxiu/p/6654496.html)
 * JavaScript真实项目的项目优化
 网络相关
减少http请求数
因为每个完整的http请求都需要经过DNS寻址、与服务器建立连接、发送请求、等待响应、接收数据这样一个消耗时间成本和资源成本的过程。所以，减少http请求数就等于减少时间和资源的开销。我们可以通过以下几项操作来减少http请求数：

合并、压缩js、css文件，这个可以使用webpack等前端自动化构建工具实现。但是对于改动频率不大的文件需单独引入，比如jquery等第三方文件，这是为了避免这些文件的缓存失效又去重新下载。
使用雪碧图(css sprite)，即请求一张大图来替换请求多张图片，然后使用background-position来取得想要展示的图片。
使用base64表示极小或极简单的图片，这种方法将使图片跟随css进行http请求，不会额外开启线程发送http请求（将图片拖入chrome浏览器，查看控制台的sources，可以看到base64编码）。但是用于大图则适得其反，因为会增加解析css的时间。
使用css、iconfont替代图片，原理与3相同，如
loading动画（https://loading.io/css/）

button（https://www.bestcssbuttongenerator.com）

阿里巴巴矢量图标库（https://www.iconfont.cn/collections）

减小资源体积
可以通过以下几个方面进行实施：

gzip压缩
js混淆
css压缩
图片压缩
缓存
可以通过以下几个方面来描述：

DNS缓存
CDN部署与缓存
http缓存
常见的http缓存类型：私有缓存（一般为本地浏览器缓存）和代理缓存。

好处：减少冗余的数据传输、减少网费；减少服务器压力；web缓存减少延迟和网络阻塞，进而减少显示某个资源所用的时间

查阅更多信息：http://blog.poetries.top/FE-Interview-Questions/simply/#_5-3-http-cache%EF%BC%9A%E5%B0%B1%E6%98%AF-http-%E7%BC%93%E5%AD%98

js相关
根据js时间线，通常把js放在文档最下面引入，或使用异步加载/延迟加载，避免js阻塞html和css的加载。

懒执行，就是将某些逻辑延迟到使用时再执行。该技术可用于首屏优化，对于某些耗时逻辑并不需要在首屏就使用的，就可以使用懒执行。懒执行需要唤醒，一般可以通过定时器或者事件的调用来唤醒

使用css而不是js来实现DOM动画

使用快速DOM遍历，document.getElementById()等

渲染相关
减少重排重绘
分离读写操作
将多次改变样式属性的操作合并成一次性操作
懒加载
懒加载就是将不关键的资源延后加载。懒加载的原理是只加载自定义区域（通常是可视区域或即将进入可视区域）内需要加载的东西。

* 移动端的禁止长按复制功能
* JavaScript的代码优化
* 百度网盘的计算机相关书籍： 链接:https://pan.baidu.com/s/1QhlDSMrhS4b0JKwGuf67ag  密码:c4rs
* [JavaScript奇技淫巧, 代码优化, 代码整理收藏, 干货!](https://blog.csdn.net/lyt_angularjs/article/details/80530786)
* [Javascript性能优化（一） - 基本性能优化](https://blog.csdn.net/qq_22230511/article/details/77447412)

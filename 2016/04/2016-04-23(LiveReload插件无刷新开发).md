# LiveReload插件无刷新开发 #

最新版的sublime text 3 plugin - LiveReload + chrome extension - LiveReload组合使用，彻底解放F5，特别适合在多屏幕上的前端开发，下面是我的安装过程(windows平台)：

## 在sublime text 3上安装LiveReload插件

按下`ctrl+shift+p`，输入并选择`Package Control: Install Package`，跳出对话框后，输入`LiveReload`安装该插件。（其实就和安装普通sublime插件的过程一样）。

重新启动sublime，每次重开sublime都需要执行一次下面的过程才生效。

1. ctrl+shift+p 打开包管理器
2. LiveReload: Enable/disable plugins
3. Enable - SimpleReload

这时候它的livereload服务才可以真正使用,可以打开http://localhost:35729/livereload.js?snipver=1以测试,如果livereload服务正常,则会正确显示JS内容,反则之服务没正常启动。
此时也可以在sublime底部看到`xxx has been enabled`的提示。

## 在chrome上安装LiveReload扩展（需要翻墙）

安装方式和普通扩展安装方式相同，安装后启用，此时可看到右上角的LiveReload图标。
![](http://7xksst.com1.z0.glb.clouddn.com/QQ%E5%9B%BE%E7%89%8720160423235554.png)

## 以服务器的方式打开页面

我这里用的是 `http-server`，例如`localhost:3000`，接着点击刚刚安装的chrome插件，中间变为实心黑色圆点表示开始运作了。
![](http://7xksst.com1.z0.glb.clouddn.com/GIF817218271.gif)


以下是演示效果，很爽有木有！

![](http://7xksst.com1.z0.glb.clouddn.com/GIF21212998912.gif)
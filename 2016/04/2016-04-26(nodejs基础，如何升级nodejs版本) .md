# [翻译]nodejs基础，如何升级nodejs版本 #

原文链接：[http://theholmesoffice.com/node-js-fundamentals-how-to-upgrade-the-node-js-version/](http://theholmesoffice.com/node-js-fundamentals-how-to-upgrade-the-node-js-version/)

Node.js的开发非常活跃，其最新的稳定版本也频繁升级。你经常会发现某些模块在你当前的Node.js版本下无法使用，而需要升级。

幸运的是，现在有一个非常简单的方法来管理你的Node.js版本，即Node binary管理模块'n'。

1. 查看机器上目前的Node.js版本。

```
$node -v v0.6.12
```

2. 清除npm缓存。

```
sudo npm cache clean -f  
```

3. 安装'n'模块。

```
sudo npm install -g n  
```

4. 升级到最新的版本（这一步可能要花点时间），也可以指定需要安装的版本。

```
sudo n 0.8.11  
```

也可以向下面这样直接安装最新的稳定版本

```
sudo n stable
```

5. 查看Node.js的版本，确定是否升级成功。

```
$node -v
```

如果第5步显示还是原来的版本，你可能需要重启一下你的机器，或者试试重启终端（译者注）。




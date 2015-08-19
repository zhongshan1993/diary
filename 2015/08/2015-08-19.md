# 用BOM的navigator检测浏览器是否具有某个插件 #

今天在工厂参观的时候，无意中接到了来自网易内推的电话面试，本来以为简历挂了的，但是还是接到了电话，让我受宠若惊，或者说语无伦次。通话期间手机信号也出了问题，这可能让面试官对我的印象更糟糕了。

总结起来，这次的面试主要的问题是基础知识漏洞、心态以及数据结构知识的缺失。从今年四月的实习面试就意识到这个问题了，现在也还没有弥补上。所以接下来的十天，就应该是最关键的时候了，恶补数据结构！恶补基础知识！

扯淡完毕！写今天的技术问题--检测浏览器插件。

针对非IE浏览器：

    <script type="text/javascript">
    	function hasPlugin(name) {
    		name = name.toLowerCase();
    		for (var i = 0; i < navigator.plugins.length; i++) {
    			if (navigator.plugins[i].name.toLowerCase().indexOf(name) != -1) {
    				return true;
    			}
    		}
    		return false;
    	}
    
    	alert(hasPlugin('Flash'));
    </script>


针对IE浏览器，使用专有的ActiveXObject类型：

    <script type="text/javascript">
    	function hasIEPlugin(name) {
    		try {
    			new ActiveXObject(name);
    			return true;
    		} catch(ex) {
    			return false
    		}
    	}
    
    	alert(hasIEPlugin('ShockwaveFlash.ShockwaveFlash'));
    </script>
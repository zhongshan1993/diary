# 跨浏览器获取pageX和pageY #

IE8及更早版本不支持事件对象上的页面坐标，不过使用客户区坐标和滚动信息可以计算出来，这时候需要用到**document.body**（混杂模式）和**document.documentElement**（标准模式）中的 **scrollTop**和**scrollLeft**属性。

计算过程如下：

    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
    <html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
    <head>
    	<meta http-equiv="Content-Type" content="text/html;charset=UTF-8">
    	<title>Document</title>
    	<style type="text/css">
    		body {
    			height: 2000px;
    		}
    	</style>
    </head>
    <body>
    	<script type="text/javascript">
    		function addHandler(target, type, func) {
    			if (target.addEventListener) {
    				target.addEventListener(type, func, false);
    			} else if (target.attachEvent) {
    				target.attachEvent('on'+type, func);
    			} else {
    				target['on'+type] = func;
    			}
    		}
    		var oBody = document.body;
    		addHandler(oBody, 'click', function(ev){
    			var oEvent = ev || event;
    			var pageX = oEvent.pageX;
    			var pageY = oEvent.pageY;
    
    			if (pageX === undefined) {
    				pageX = oEvent.clientX + (document.body.scrollLeft||document.documentElement.scrollLeft);
    				pageY = oEvent.clientY + (document.body.scrollTop||document.documentElement.scrollTop);
    			}
    
    			alert('X:'+pageX+', '+'Y:'+pageY);
    		})
    	</script>
    </body>
    </html>


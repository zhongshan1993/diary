# 运用DIV拖拽实现resize和碰撞检测 #


### Div由拖拽改变大小 ###
[演示demo](http://zhongshan1993.github.io/myDemo/singlePage/drag-changeDivSize.html)

当我们运用html元素"textarea"写一个文本输入框时，浏览器会自动生成以下样式
![](http://7xksst.com1.z0.glb.clouddn.com/QQ截图20150731125810.png)


用鼠标拖动右下角的小三角就可以对文本框的大小进行重新设置，于是我们试着在一个div中实现与上述相似的功能

**先看布局**

    <style>
    	#div1 {
    		width:10px; 
    		height:10px; 
    		background:red; 
    		position:absolute; 
    		z-index:2;
    		bottom:0;
    		right: 0;	
    		cursor: nw-resize;
    		background: url(images/drag_ico.gif);
    	}
    	#div2 {
    		position: relative;
    		width: 200px;
    		height: 150px;
    		background: #ccc;
    	}
    	.box {
    		position: absolute;
    		border: 1px dashed #000;
    	}
    </style>

    
    <div id="div2">
    	<div id="div1"></div>
    </div>

用父元素div2代替“文本框”，用div1代替小三角，这里的定位，为后面的js实现方法打下了基础
![](http://7xksst.com1.z0.glb.clouddn.com/QQ截图20150731130554.png)

**JS的实现方法**

    <script>
    window.onload = function() {
    	var oDiv = document.getElementById('div1');
    	var oDiv2 = document.getElementById('div2');
    		
    	oDiv.onmousedown = function(ev) {
    		var oEvent = ev || event;
    		var disX = oEvent.clientX - oDiv.offsetLeft;
    		var disY = oEvent.clientY - oDiv.offsetTop;
    
    		document.onmousemove = function(ev) {
    			var oEvent = ev || event;
    			oDiv2.style.width = oEvent.clientX - disX + oDiv.offsetWidth + 'px';
    			oDiv2.style.height = oEvent.clientY - disY + oDiv.offsetHeight + 'px';
    			
    		};
    		
    		document.onmouseup = function() {
    			document.onmousemove = null;
    			document.onmouseup = null;
    		};
    
    		return false;
    	};
    };
    </script>

将小三角移动的x轴和y轴长度反应到其父元素的宽高上面，便得到了这样的效果



----------

### 在拖动过程中检测两个div是否有重合 ###

布局并不麻烦，两个div，定宽高、背景颜色即可

[演示demo](http://zhongshan1993.github.io/myDemo/singlePage/drag-testCrash.html)

逆向思维：既然我们要检测div在运动过程中是否重合，那如果知道什么时候不重合，剩下的情况就是重合了，在这里，分析不重合的情况显然比分析重合的情况要容易

如图，当r1<l2, b1<t2, l1>r2, t2>b2，这四个条件只要有任意一个成立，都会导致两个div不重合，这里的t,l,b,r在下面的代码中有详细定义。
![](http://7xksst.com1.z0.glb.clouddn.com/QQ截图20150731132238.png)


    <script>
    window.onload = function() {
    	var oDiv = document.getElementById('div1');
    	var oDiv2 = document.getElementById('div2');
    	
    	oDiv.onmousedown = function(ev) {
    		var oEvent = ev || event;
    		var disX = oEvent.clientX - oDiv.offsetLeft;
    		var disY = oEvent.clientY - oDiv.offsetTop;
    		
    		document.onmousemove = function(ev) {
    			var oEvent = ev || event;
    			
    			oDiv.style.left = oEvent.clientX - disX + 'px';
    			oDiv.style.top = oEvent.clientY - disY + 'px';
    			
    			var l1 = oDiv.offsetLeft;
    			var r1 = l1 + oDiv.offsetWidth;
    			var t1 = oDiv.offsetTop;
    			var b1 = t1 + oDiv.offsetHeight;
    
    			var l2 = oDiv2.offsetLeft;
    			var r2 = l2 + oDiv2.offsetWidth;
    			var t2 = oDiv2.offsetTop;
    			var b2 = t2 + oDiv2.offsetHeight;
    
    			if (r1 < l2 || l1 > r2 || b1 < t2 || t1 > b2) {
    				oDiv2.style.backgroundColor = 'yellow';
    
    			} else {
					// 发生碰撞的时候
    				oDiv2.style.backgroundColor = 'green';
    			}
    		};
    		
    		document.onmouseup = function() {
    			document.onmousemove = null;
    			document.onmouseup = null;
    		};
    	};
    };
    </script>
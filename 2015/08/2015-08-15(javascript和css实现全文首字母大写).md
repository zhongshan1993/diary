# javascript和css实现全文首字母大写 #

**JavaScript**

这里用到正则表达式的单词边界 `\b`,以及replace方法，它的第二个参数可以接受一个匿名函数，实现已匹配的字符串处理。

	<textarea cols="30" rows="10" id="txt1"></textarea>
	<input type="button" value="转化" id="btn"/>
	<textarea cols="30" rows="10" id="txt2"></textarea>

	<script type="text/javascript">
		var oTxt1 = document.getElementById("txt1");
		var oTxt2 = document.getElementById("txt2");
		var oBtn = document.getElementById("btn");

		oBtn.onclick = function() {
			var txt = oTxt1.value;
			var reg = /\b\w+\b/g;
			var str = txt.replace(reg, function(word){
				return (word.substr(0, 1)).toUpperCase() + word.substr(1);
			});
			oTxt2.value = str;
		}
	</script>


**CSS**

即 `text-transform: capitalize`的应用
PS: 看来还得多看书啊…

	<style type="text/css">
		#txt2 {
			text-transform: capitalize;
		}
	</style>
    <body>
    	<textarea cols="30" rows="10" id="txt1"></textarea>
    	<input type="button" value="转化" id="btn"/>
    	<textarea cols="30" rows="10" id="txt2"></textarea>
    
    	<script type="text/javascript">
    		var oTxt1 = document.getElementById("txt1");
    		var oTxt2 = document.getElementById("txt2");
    		var oBtn = document.getElementById("btn");
    
    		oBtn.onclick = function() {
    			oTxt2.value = oTxt1.value;
    		}
    	</script>
    </body>
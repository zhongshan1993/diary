# 利用transform实现平行四边形 #

效果图如下

![](http://i.imgur.com/P7cHSCQ.png)


    
    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
    <html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
    <head>
    	<meta http-equiv="Content-Type" content="text/html;charset=UTF-8">
    	<title>CSS三角形</title>
    	<style type="text/css">
    		
    		.city {
    			display: inline-block;
    			padding: 5px 20px;
    			background: #44a5fc;
    			color: #333;
    			transform: skew(-20deg);
    		}
    		.city div {
    			transform: skew(20deg);
    		}
    	</style>
    </head>
    <body>
    	<div class="city">
    		<div>上海</div>
    	</div>
    </body>
    </html>
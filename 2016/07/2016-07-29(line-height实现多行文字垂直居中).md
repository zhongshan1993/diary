# line-height实现多行文字垂直居中 #

	<!DOCTYPE html>
	<html lang="en">
	<head>
		<meta charset="UTF-8">
		<title>Document</title>
		<style>
			.box {
				font-size: 20px;
				border: 1px solid #ccc;
				line-height: 300px;
			}
			.box span {
				display: inline-block;
				vertical-align: middle;
				line-height: 1.3;
			}
		</style>
	</head>
	<body>
		<div class="box">
			<span>这是多行文字<br>这是多行文字</span>
		</div>
	</body>
	</html>
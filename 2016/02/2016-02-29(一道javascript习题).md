# 一道javascript习题 #

```

<!DOCTYPE html>
<html>
 <head>
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>   
  <script type="text/javascript">  
  function openWindow()
  {
      var st=confirm("你确定要打开窗口吗？");
      if(st==true)
      {
          var sp=prompt("默认网站是","http://www.baidu.com");
          if(sp)
          {
            window.open("http://www.baidu.com","_blank",'width=400px,height=500px,menubar=no,toolbar=no');
          }
          else
          {
              alert("The end");
          }
      }
      else
      {
        alert("The end");
      }
  }
  </script> 
 </head> 
 <body> 
      <input type="button" value="新窗口打开网站" onclick="openWindow()" /> 
 </body>
</html>


```
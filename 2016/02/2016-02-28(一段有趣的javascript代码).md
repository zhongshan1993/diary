# 一段有趣的javascript代码 #

```

<script>
    function add(a) { 
      var temp = function(b) {return add(a + b);} 
      temp.valueOf = temp.toString = function(){return a;}; 
      return temp;
    } 
    var ans = add(1)(2)(3); 
    alert(ans); // 6
</script>

```
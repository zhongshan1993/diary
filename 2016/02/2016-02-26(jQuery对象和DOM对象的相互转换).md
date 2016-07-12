# jQuery对象和DOM对象的相互转换  #

## 把jQuery对象转换为DOM对象 ##

- 借助数组下标来读取

```
    $(function() {
        var $li = $("li"); // 返回jQuery对象
        var li = $li[0]; // 返回DOM对象
        alert(li.innerHTML);
    })
```

- 借助jQuery对象的get()方法

```
    $(function() {
        var $li = $("li"); // 返回jQuery对象
        var li = $li.get(0); // 返回DOM对象
        alert(li.innerHTML);
    })
```

## 把DOM对象转换为jQuery对象 ##
    
```
    $(function(){
        var aLi = document.getElementsByTagName('li');
        var $li = $(aLi[0]);
        alert($li.html()); 
    })
```


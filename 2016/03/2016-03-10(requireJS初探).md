# requireJS初探 #

## index.html ##

```
......
<link rel="stylesheet" href="css/base.css">
<link rel="stylesheet" href="css/window.css">
......
<button id="a">点击</button>
<script src="../bower_components/requirejs/require.js" data-main="js/main"></script>
......

```

## main.js ##

```
// 添加jQuery模块依赖
require.config({
    paths: {
        jquery: 'jquery'
    }
})
require(['jquery', 'window'], function($, w) {
    $('#a').click(function(event) {
        new w.Window().alert("Welcome!", function() {
            alert("You clicked the button!");
        });
    });
});
```

## window.js ##

```
define(['jquery'], function($) {
    function Window(){}

    Window.prototype = {
        alert: function(content, handler){
            var boundingBox = $('<div class="window_boundingBox"></div>');
            boundingBox.appendTo('body');
            boundingBox.html(content);
            var btn = $('<input type="button" value="确定"/>');
            btn.appendTo(boundingBox);
            btn.click(function() {
                handler && handler();
                boundingBox.remove();
            });
        },
        confirm: function(){},
        prompt: function(){}
    };

    return {
        Window: Window
    }
});
```

## base.css ##

```
html, body {
    margin: 0;
    padding: 0;
}
```

## window.css ##

```
.window_boundingBox {
    position: fixed;
    border: 1px solid #000;
    width: 500px;
    height: 300px;
    left: 50%;
    margin-left: -250px;
    top: 100px;
    box-shadow: 0 0 12px rgba(0, 0, 0, 0.5);
}
.window_boundingBox input {
    position: absolute;
    left: 50%;
    bottom: 10px;
    width: 100px;
    margin-left: -50px;
}
```
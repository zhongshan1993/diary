# 浏览器网页截图开源库html2canvas  #

在[月影](http://www.h5jun.com)的博客上接触到这个开源库，感觉很不错，这段时间在忙毕设，日志写的也很少，今天就记录一下这个吧~

```
html2canvas(document.getElementById('tab'), {
    onrendered: function(canvas) {
        // console.log(canvas);
        var img = document.getElementById('img');
        img.src = canvas.toDataURL('image/jpeg');
    }
});
```
# Angular给所有$http请求设置缓存 #

```
angular.module('myApp', [])
.config(function($httpProvider, $cacheFactory) {
    $httpProvider.default.cache = $cacheFactory('lru', {
        capacity: 20
    });
});
```
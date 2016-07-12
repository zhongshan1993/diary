# XMLHttpRequest转化为基于promise的任务 #

```

function get(url) {
    return new Promise(function(resolve, reject) {
        var req = new XMLHttpRequest();

        req.open('GET', url);

        req.onload = function() {
            if (req.status === 200) {
                resolve(req.response);
            } else {
                reject(Error(req.statusText));
            }
        };

        req.error = function() {
            reject(Error("Network error!"));
        };

        req.send();
    });
}

// 执行!
get('test.json').then(function(response) {
    var resObj = JSON.parse(response);
    console.log(resObj["name"]);
}, function(error) {
    console.error("Error!", error);
});


```
---
layout: post
title: js代码片段
keywords: js代码片段
description: js代码片段
category: snippets
---



### 日期格式化
```
Date.prototype.Format = function (fmt) {
    var o = {
        "M+": this.getMonth() + 1, //月份 
        "d+": this.getDate(), //日 
        "h+": this.getHours(), //小时 
        "m+": this.getMinutes(), //分 
        "s+": this.getSeconds(), //秒 
        "q+": Math.floor((this.getMonth() + 3) / 3), //季度 
        "S": this.getMilliseconds() //毫秒 
    };
    if (/(y+)/.test(fmt)) fmt = fmt.replace(RegExp.$1, (this.getFullYear() + "").substr(4 - RegExp.$1.length));
    for (var k in o)
        if (new RegExp("(" + k + ")").test(fmt)) fmt = fmt.replace(RegExp.$1, (RegExp.$1.length == 1) ? (o[k]) : (("00" + o[k]).substr(("" + o[k]).length)));
    return fmt;
}
new Date().Format('yyyy-MM-dd hh:mm:ss')
```



### 鼠标滚轮
```
window.addEventListener('wheel', function(e) {
    if (e.deltaY < 0) {
        console.log('scrolling up');
    }
    if (e.deltaY > 0) {
        console.log('scrolling down');
    }
});
```

### 移动设备检测
```
if (/iPhone|iPad|iPod|Android/i.test(navigator.userAgent)) {     
    //ua正则匹配是否含有某些移动设备的关键词
}

if (/Mobi|Android/i.test(navigator.userAgent)) {
    // 简单粗暴
}

if (/Android|webOS|iPhone|iPad|iPod|BlackBerry|BB|PlayBook|IEMobile|Windows Phone|Kindle|Silk|Opera Mini/i.test(navigator.userAgent)) {
    // 严谨的ua正则判断
}

if (navigator.maxTouchPoints || 'ontouchstart' in document) {
    // 是否支持多点或者触摸事件，我的桌面显示器支持触摸屏怎么办。。。
}

if (window.orientation !== undefined) {
    // 判断设备横竖屏是否支持，但是过时的属性（https://developer.mozilla.org/en-US/docs/Web/API/Window/orientation）
}

https://github.com/matthewhudson/current-device     //device.js
```



### 操作cookie
```
// 设置cookie
function setCookie(name,value,days) {
    var expires = "";
    if (days) {
        var date = new Date();
        date.setTime(date.getTime() + (days*24*60*60*1000));
        expires = "; expires=" + date.toUTCString();
    }
    document.cookie = name + "=" + (value || "")  + expires + "; path=/";
}

//获取cookie
function getCookie(name) {
    var nameEQ = name + "=";
    var ca = document.cookie.split(';');
    for(var i=0;i < ca.length;i++) {
        var c = ca[i];
        while (c.charAt(0)==' ') c = c.substring(1,c.length);
        if (c.indexOf(nameEQ) == 0) return c.substring(nameEQ.length,c.length);
    }
    return null;
}

//销毁cookie
function eraseCookie(name) {   
    document.cookie = name+'=; Max-Age=-99999999;';  
}
```


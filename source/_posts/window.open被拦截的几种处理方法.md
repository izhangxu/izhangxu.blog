title: window.open被拦截的几种处理方法
categories:
  - javascript
date: 2016-12-01 10:45:38
tags:
---
window对象是BOM的顶层(核心)对象，它的属性在众多浏览器中的兼容不大相同，我们常用的window.open()方法就在各个浏览器中表现不同，例如：点击按钮弹出新窗口的需求，在大多数高级浏览器都会拦截弹出的窗口。下面有几种常见的方案：

替代方案：

1、创建a标签代替
{% codeblock lang:javascript %}
var a = document.createElement('a');
a.setAttribute('href', url);
a.setAttribute('target', '_blank');
document.body.appendChild(a);
a.click();
document.body.removeChild(a);
{% endcodeblock %}
2、构建form表单提交
{% codeblock lang:javascript %}
var oForm = document.createElement('form');
oForm.action = 'http://www.fangjiadp.com/beijing/newhouse/index';(需要跳转的链接)
oForm.target = '_blank';
oForm.method = 'get';
document.body.appendChild(oForm);
oForm.submit();
document.body.removeChild(oForm);
{% endcodeblock %}

window.open()防止被拦截：

1、绑定事件执行window.open()不会被拦截
{% codeblock lang:javascript %}
document.body.addEventListener('click', function() {
    window.open('//www.baidu.com', '_blank');
});
{% endcodeblock %}
2、处理ajax回调中被拦截
{% codeblock lang:javascript %}
$('.open').on('click', function() {
    var w = window.open();
    $.ajax({
        type: 'POST',
        url: '/xxx',
        dataType: 'json',
        error: function() {
            w.close();
        },
        success: function(res) {
            w.location = res.url;
        }
    });
});
{% endcodeblock %}
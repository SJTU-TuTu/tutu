---
layout: categories
title: "HIGH爆网址"
permalink: /test/
author_profile: false
---

<html>
<head>
<meta charset="utf-8">
<title>图通道</title>
</head>
<body>

<script type="text/javascript">
     $(document).ready(function() {
       var newVisitor = isNewVisitor();// 如果是新访客
       if(newVisitor === true)
       {
       
	var x = prompt("关注微信公众号“图通道”回复“密码”","");
	while (x!="046046"){
	    alert("密码错误呀！")	    
	    window.close()
	    x = prompt("关注微信公众号“图通道”回复“密码”","");

       // 标记：已经向该访客弹出过消息。30天之内不要再弹
       setCookie("gznotes-visited","true", 5);
       }
     });

     function isNewVisitor() {
     // 从cookie读取“已经向访客提示过消息”的标志位
       var flg = getCookie("gznotes-visited");
        if (flg === "") {
        return true;
        } else {
         return false;
        }
     }
   // 写字段到cookie
     function setCookie(cname, cvalue, exdays) {
       var d = new Date();
       d.setTime(d.getTime() + (exdays*24*60*60*1000));
       var expires = "expires="+d.toUTCString();
       document.cookie = cname + "=" + cvalue + "; " + expires +";path=/";
     }
     // 读cookie
     function getCookie(cname) {
       var name = cname + "=";
       var ca = document.cookie.split(';');
       for(var i=0; i<ca.length; i++) {
          var c = ca[i];
          while (c.charAt(0)==' ') c = c.substring(1);
          if (c.indexOf(name) == 0) return c.substring(name.length,c.length);
        }
        return "";
     }
   </script>

</body>
</html>
  
# 搜索引擎

|[**多吉搜索**](https://www.dogedoge.com/) |[秘迹搜索](https://mijisou.com/)|[DuckDG](https://duckduckgo.com/)|
|---|--- | --- |
|[百度](https://www.baidu.com/) |[必应](https://cn.bing.com/?mkt=zh-CN)|[谷歌](https://www.google.com.hk/webhp?hl=zh-CN&sourceid=cnhp&gws_rd=ssl) |


# 资源下载

|[软件下载](http://a-1.vip/exe/) |[插件下载](https://crxdl.com/)|[脚本下载](https://greasyfork.org/zh-CN)|[吾爱破解](https://www.52pojie.cn/)|
|---|--- | --- |---|
|[美图下载](https://www.logosc.cn/so/)|[模板下载](http://ppt.sotary.com/web/wxapp/index.html)|[破解软件](http://www.dugubest.com/)||
|[电子书ZLibrary](https://1lib.net/)|[电子书Epubee](http://cn.epubee.com/books/)|[电子书Jiumodiary](https://www.jiumodiary.com/)|[电子书kindle](http://www.seo630.com/index.html)|
|





[史上最全]<大秦帝国>第一部+第二部影视资源合集 1080i+720
http://tieba.baidu.com/p/3755692411

nginx的开源
http://tengine.taobao.org/

https://github.com/jquery

工程游戏，小朋友
http://pbskids.org/games/

十个儿童英文学习网站
http://baobao.sohu.com/w/news/407537311.shtml

Sublime Text 2开发你的javascript
http://www.cnblogs.com/xiaopen/archive/2012/05/13/Sublime_Text.html

安装node.js
\#npm install -g mocha
\#npm install -g expect.js

跨平台 移动开发
http://fex.baidu.com/blog/2015/05/cross-mobile/

svg 
教程 http://www.w3school.com.cn/svg/svg_reference.asp
在线编辑 https://github.com/SVG-Edit/svgedit
标准 http://www.w3.org/TR/SVG/
d3_样例 https://github.com/mbostock/d3/wiki/Gallery
d3_API手册 https://github.com/mbostock/d3/wiki/API--%E4%B8%AD%E6%96%87%E6%89%8B%E5%86%8C
d3_教程 https://github.com/mbostock/d3/wiki/Tutorials
微软 https://msdn.microsoft.com/zh-cn/library/gg589526(v=vs.85).aspx

w3规范 http://www.w3.org/TR/tr-technology-stds
w3规范-html http://www.w3.org/TR/2014/REC-html5-20141028/
w3规范-http http://www.w3.org/Protocols/rfc2616/rfc2616.txt



<html xmlns:svg="http://www.w3.org/2000/svg">
<head>svg sample</head>

<body>


<svg width="720" height="120">
</svg>


<script src="./d3/d3.js"></script>
<script>

    var svg = d3.select("svg");
    var circle = svg.selectAll("circle")
            .data([1, 50, 3, 4]);
    var circleEnter = circle.enter().append("circle");
    circleEnter.attr("cy", 60);
    circleEnter.attr("cx", function(d, i) { return i * 100 + 30; });
    circleEnter.attr("r", function(d, i) { return Math.sqrt(d*i); });

    var t = setTimeout("fn_timeOut()", 1000);

    var count = 0;

    function fn_timeOut() {
        var body1 = d3.select("body");
        var label1 = body1.append("label");
        label1.text("count="+(++count));
        var div1 = label1.append("br");
        t = setTimeout("fn_timeOut()", 1000);
    }

</script>



</body>
</html>

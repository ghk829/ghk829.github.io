---
layout: post
title:  "JavaScript Basic 1"
date:   2018-10-16
excerpt: "Just about everything you'll need to style in the theme: headings, paragraphs, blockquotes, tables, code blocks, and more."
tag:
- javascript 
comments: false
---

# Javascript의 자료형
{: .notice}

{% highlight javascript %}
# primitive type
var bool = true;
var num = 1.1;
var str = "hello";

# reference type
var arr = [1,2,3];
var obj = {'a':1};

# other
var nul = null;
var undefi = undefined;

{% endhighlight %}

여기서 중요한 것은 기본 자료형 조차 객체처럼 사용할 수 있다는 것.
*각 기본 자료형도 객체 내부의 property 및 method를 갖고 있다.*



```mermaid

graph TD
A((Object)) -- prototype --> B((모든 객체))

```
<script>
setTimeout(function() { 
		$(function(){
        var element = document.querySelector(".language-mermaid");

        var insertSvg = function(svgCode, bindFunctions){
            element.innerHTML = svgCode;
        };

        var graphDefinition = element.textContent;
        var graph = mermaid.mermaidAPI.render('graphDiv', graphDefinition, insertSvg);
    });
}, 1500)
</script>

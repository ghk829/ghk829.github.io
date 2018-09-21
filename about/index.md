---
layout: page
title: Who is Ki?
tags: [about, Jekyll, theme, moon]
date: 2018-09-21
comments: false
---
    
<center><h2>The best man</h2></center>

## Game
* The legend of Zelda, The Breath of The Wild
* Mario Odessay
* Hollow Night
* FIFA 18, difficulty : Legend
* Startcraft 1
* Uncharted 4

## Language
<h3 class="title" style="font-size:30px;">
{% if site.java %}<i class="devicon-java-plain" style="margin-left:20px;"></i>{% endif %}
{% if site.python %}<i class="devicon-python-plain" style="margin-left:20px;"></i>{% endif %}
{% if site.javascript %}<i class="devicon-javascript-plain" style="margin-left:20px;"></i>{% endif %}
{% if site.cplusplus %}<i class="devicon-cplusplus-plain" style="margin-left:20px;"></i>{% endif %}
</h3>

## Movie
* The Dark Knight
* How I Met Your Mother
* Oh, Captain, My Captain! 

```mermaid

graph LR
A((VueJs)) -- REST --> B((NodeJs))
B --> C(MariaDB/MongoDB)

```
<script>
setTimeout(function() { 
console.log(20);
}, 2000)
</script>
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
}, 3000)
</script>
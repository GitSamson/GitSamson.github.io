---
title: "Dynamic Update SVG"
categories:
  - HTML5
tags:
  - SVG
  - SVG event
  - javascript
  - HTML5
---

```js
<script>

    var id = 0 ;
    var svg=document.getElementById('SVG');
    svg.clientWidth=window.innerWidth;
    svg.clientHeight=window.innerHeight;
     function BackgroundClick(evt) {
            console.log(evt.offsetX,evt.offsetY);
            var rect = document.createElementNS('http://www.w3.org/2000/svg','rect');            rect.setAttribute('id',id);
            id++;
            rect.setAttribute('x',evt.offsetX-25);
            rect.setAttribute('y',evt.offsetY-25);
            rect.setAttribute('width','50');
            rect.setAttribute('height','50');
            rect.setAttribute('fill', "black");
            svg.appendChild(rect);
        }

   $('svg').mousedown(BackgroundClick);
   
</script>

```

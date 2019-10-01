---
title: "Canvas Draggable Elements"
categories:
  - HTML5
tags:
  - Canvas
  - Canvas event
  - javascript
  - HTML5
---

```js
<html>
<body>
<canvas id = "MyCanvas" width="100%" height="100%" stroke='black'>

</canvas>
</body>
<script>
    
// Initialization
var Canvas = document.getElementById('MyCanvas');
var body = document.querySelector('body');
var draw=Canvas.getContext('2d');
Canvas.height=window.innerHeight;
Canvas.width=window.innerWidth; 
d = Canvas.getContext('2d');

// Package Canvas draw function
function Canv(canvas,contentList){
    this.dragging=false;
    this.c = canvas;
    this.list=contentList;
}
Canv.prototype.clear = function(){
    d.clearRect(0, 0, Canvas.width, Canvas.height);
    
}

Canv.prototype.redraw = function(){
    this.clear();
    this.list.forEach(function(j){
    //console.log('c.redraw:',j.selected);
        
        j.draw();
    })
}

Canv.prototype.resetSelect = function(){
    this.list.forEach(function(i){
        i.selected=false;
    })
}

function content(x,y,width,height,id){
    this.x=x;
    this.y=y;
    this.width=width;
    this.height=height;
    this.id=id;
    this.selected=false;
    this.dragging=false;
}

//Content Draw funciton
content.prototype.draw = function(){
    if (this.selected==true) {
        //console.log(this.id,'selected Draw',this.selected);
        
        d.fillStyle = "Grey";
        d.fillRect(this.x, this.y, this.width, this.height);
    }
    d.beginPath();
    d.rect(this.x, this.y, this.width, this.height);
    d.stroke();
}
//---------------------------------------------
var diagram=[];
diagram.push(new content(10, 30, 30, 100,1));
diagram.push(new content(50, 50, 100, 100,2)); 
diagram.push(new content(200,300,50,50,3))

var c = new Canv(d,diagram);
c.redraw();
//Drag EventListener
Canvas.onmousedown = function(e){
    c.clear;    
    //Iteration to find out which one is the actived element
    diagram.forEach(function(i){
        i.draw()
        if (d.isPointInPath(e.pageX, e.pageY)) {
        //from here is the one actived 
        var offsetX = i.x - e.pageX;
        var offsetY = i.y - e.pageY;
        i.dragging=true;
        i.selected = true;        
        i.draw()
        Canvas.addEventListener('mousemove',function(j){
            
            if(i.dragging==true){
                // this.i=i;
                i.x = j.pageX + offsetX;
                i.y = j.pageY + offsetY;
                c.redraw();
            }
        })
        Canvas.addEventListener('mouseup', function () {
                i.dragging=false;
            })
        }else{
            i.selected = false;
        }
        c.redraw();
    });
}
</script>
</html>

```

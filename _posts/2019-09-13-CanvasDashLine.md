---
title: "Canvas Set Dash Line type"
categories:
  - HTML5
tags:
  - Canvas
  - Canvas event
  - javascript
  - HTML5
  - Dash Line
---

How to set up dash line type in Canvas?

```js

var canvas = document.querySelector("Canvas");
var D =  canvas.getContent("2d");
D.setLineDash([6,6]) //set Dash Line type
D.rect(20,20,80,80);


D.setLineDash([]);//set back to solid line type
D.rect(80,80,100,100);

```

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
    this.Board = canvas;
    this.list=contentList;
}
Canv.prototype.clear = function(){
    d.clearRect(0, 0, Canvas.width, Canvas.height);
    
}

Canv.prototype.redraw = function(){
    this.clear();
    this.list.forEach(function(j){
    //console.log('Board.redraw:',j.selected);
        
        j.draw();
    })
}

Canv.prototype.resetSelect = function(){
    this.list.forEach(function(i){
        i.selected=false;
    })
}
Canv.prototype.selectList = function(){
    var s = [];
    this.list.forEach(function(i){
        if(i.selected){
            s.push(i);
        }
    })
    return(s);
}

function content(x,y,width,height,id){
    this.x=x;
    this.y=y;
    this.width=width;
    this.height=height;
    this.id=id;
    this.selected=false;
    this.dragging=false;
    this.dashline=false;
}

//Content Draw funciton
content.prototype.draw = function(){
    if (this.selected==true) {
        //console.log(this.id,'selected Draw',this.selected);
        
        d.fillStyle = "Grey";
        d.fillRect(this.x, this.y, this.width, this.height);
    }
    if(this.dashline){
        d.setLineDash([6,6]);
    }

    d.beginPath();
    d.rect(this.x, this.y, this.width, this.height);
    d.stroke();
    d.setLineDash([]);
}



//---------------------------------------------


var diagram=[];
diagram.push(new content(10, 30, 30, 100,1));
diagram.push(new content(50, 50, 100, 100,2)); 
diagram.push(new content(200,300,50,50,3))

var selectBox=null;
var Board = new Canv(d,diagram);
Board.redraw();
//Drag EventListener

//==============================================================
//Draggable function
Canvas.addEventListener('mousedown',function(e){
    var mousedown = {x : e.pageX , y : e.pageY };
    Board.clear;  
    var NoSelected=true; //detect is anything selected

    var selectedList = Board.selectList();
    

    //Iteration to find out which one is the actived element
    diagram.forEach(function(i){
        i.draw()
        if (d.isPointInPath(e.pageX, e.pageY)) {

        NoSelected=false;
        //from here is the one actived 
        var mouseOffset={x:e.pageX, y:e.pageY};
        var mousemove={x:e.pageX,y:e.pageY}
        Board.dragging=true;
        i.selected = true; 
        selectedList = Board.selectList(); //refresh selected list

        i.draw()

        Canvas.addEventListener('mousemove',function(j){
            
            if(Board.dragging==true){
                
                mouseOffset.x=j.pageX-mousemove.x;
                mouseOffset.y=j.pageY-mousemove.y;
                mousemove.x=j.pageX;
                mousemove.y=j.pageY;
                console.log(mouseOffset.x,mouseOffset.y);
                selectedList.forEach(function(z){
                    z.x = z.x+mouseOffset.x;
                    z.y = z.y+mouseOffset.y;
                    Board.redraw();
                })

                
            }
        })
        Canvas.addEventListener('mouseup', function () {
                Board.dragging=false;
                selectedList=[];
            })
        }
        Board.redraw();
    });

//=======================================================================
//Selct box function
    if(NoSelected){
        selectBox=new content(mousedown.x,mousedown.y,0,0,0);//instance select box content 
        selectBox.dashline=true;
        selectBox.draw();
        Board.resetSelect();

        //refresh mousemove EventListener
        Canvas.addEventListener('mousemove',function(e){
            if(selectBox!=null){
                selectBox.width = e.pageX-mousedown.x;
                selectBox.height = e.pageY-mousedown.y;
                //## forEach find inSelctBox element
                diagram.forEach(function(i){
                    if((mousedown.x<i.x)&&(e.pageX>i.x+i.width)&& (mousedown.y<i.y) && (e.pageY>i.y+i.height)){
                        i.selected=true;
                        console.log(i.id);
                        
                    }else{
                        i.selected=false;
                    }
                })


                Board.redraw();
                selectBox.draw();
            }
            
        })
        //referesh mouseup EventListener
        Canvas.addEventListener('mouseup',function(e){
            selectBox=null;
            Board.redraw();
        })
    }

//===========================================================================
});


</script>
</html>

```

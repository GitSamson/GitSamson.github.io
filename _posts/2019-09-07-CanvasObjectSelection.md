

# [demon](https://gitsamson.github.io/BatteryEditor/Test/ClickAndSelect.html)


# Selectable Canvas element

Main idea is get mouse position, Redraw all the path to check whether mouse position is on the Path by using isPointInPath function.

## Attention:

But isPointInPath function can only check last diagram draw.
To fulfill intention need to redraw all the path.

# How to do it :

- Content for paths 
- addEeventListener for click 
- redraw all paths
- index system 

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

var content=[
    {x:10, y:30, width:30, height:100},
    {x:50, y:50, width:100, height:100},
    
];

// Click Eventlistener:
Canvas.addEventListener('click',function(e){
    DetectandUpdate(e.pageX,e.pageY);
})
function DetectandUpdate(x,y){
    content.forEach(function(list){
        d.beginPath();
        d.rect(list.x,list.y,list.width,list.height);
        d.stroke();
        if(d.isPointInPath(x,y)){
            d.fillStyle='grey'
            d.fillRect(list.x,list.y,list.width,list.height);
        }
    })   
}
</script>
</html>

```
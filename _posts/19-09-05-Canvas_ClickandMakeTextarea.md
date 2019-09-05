```js
<html>
<body>
<canvas id = "MyCanvas" width="100%" height="100%" stroke='black'>

</canvas>
</body>


<script>
var Canvas = document.getElementById('MyCanvas');
var body = document.querySelector('body');
var draw=Canvas.getContext('2d');
Canvas.height=window.innerHeight;
Canvas.width=window.innerWidth;

Canvas.addEventListener('click',function(e){
    if (document.querySelector('textarea') != null) {
        var lastText = document.querySelector('textarea');
        draw.font = '15px Calibri'
        draw.fillText(lastText.value, lastText.getAttribute('x'), lastText.getAttribute('y'));
        body.removeChild(lastText);
        
    }
    var x=e.pageX, 
        y=e.pageY;
    var text= document.createElement('textarea');
    text.value='hey';
    text.style['position']='absolute';
    text.setAttribute('x',x);
    text.setAttribute('y', y);
    text.style['top']=y+'px';
    text.style['left']=x+'px';
    text.style['margin']='0';
    text.style['font-size']='15px';
    text.style['font-family']='Calibri';
    text.style['border']='0';
    text.style['outline']='none';
    text.style['whiteSpace']='pre-wrap';
    
    body.appendChild(text);

   
})
</script>


</html>
```

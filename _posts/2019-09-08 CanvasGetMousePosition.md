---
title: "Get mouse position on Canvas"
categories:
  - HTML5
tags:
  - Canvas
  - Canvas event
  - javascript
  - HTML5
---

![diagram](https://i.stack.imgur.com/4C3no.png)

# There are three types of get position of mouse. 

- ScreenX/Y (Systemt Mouse Position)
- PageX/Y (Content Position ignore scroll)
- ClientX/Y (Browser Position)

```js

Canvas.addEventListener('click',function(e){
var MousePosition_X = e.PageX;
var MousePosition_Y = e.PageY;

})

```

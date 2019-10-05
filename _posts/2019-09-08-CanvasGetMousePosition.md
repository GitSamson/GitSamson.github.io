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
![link](https://blog.csdn.net/qq_17616169/article/details/72833044)

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
# How to make canvas full screen?
dont forget body have margin and padding too.
So you need to add this in <body>:
```html
  <body style="margin:0;padding:0">
```

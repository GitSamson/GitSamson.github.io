---
title: "Javascript Dynamic Properties"
categories:
  - HTML5
tags:
  - Dynamic Properties
  - DefineProperties
  - javascript
  - HTML5
  - Object.defineProperties
---

In javascript how to get properties by access instance properties?

```js 
<html>
<body>
</body>
<script>

function book (e){
  this.x = e;

}
Object.defineProperties(book.prototype,{
  _bookname:{
    writable : true,
    value : 'value'
  },
  bookname:{
    get:function(){return 'book'+this.x;}
  },
  year:{
    get: function(){
      return 2019;
    }
  }
})

function shelf(b){
  this.b = b;
}
shelf.prototype.get= {
  book: function(){return b.bookname}
}
Object.defineProperties(shelf.prototype,{
  bookname:{
    get:function(){
      return this.b.bookname+"shelf";
    }
  }

})

test = new book('fromheaven');
testshelf = new shelf (test);
console.log('book.bookname : ',book.bookname);
console.log("instace.property : ",test.x)
console.log('instance.definedProperty :',test.bookname);
console.log(testshelf.bookname)
console.log(test.year);

// console.log(book.year);



</script>
</html>
```

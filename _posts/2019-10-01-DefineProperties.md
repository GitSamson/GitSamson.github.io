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

  function book () {
    this.name;
    this.edition=12;
  };
  Object.defineProperties(book, {
    // _year: {
    //   value: 2004,
    //   writable: true // << writable
    // },
    edition: {
      value: 12,
      writable: true // << writable
    },
    year: {
      get: function () {
        // << missing return
        return this._year;
      },
      set: function (value) {

        if (value > 2004) {
          this._year = value;
          this.edition = this.edition + value - 2004;
        }
      }
    }
  });
  book.year = 2016; // << here you used this instead of book
  console.log(book.edition);


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

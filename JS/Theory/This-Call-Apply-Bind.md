* Use .bind() when you want that function to later be called with a certain context, useful in events.

* Use .call() or .apply() when you want to invoke the function immediately, and modify the context.

* Eg.  
```
var obj = {
  x: 81,
  getX: function() {
    return this.x;
  }
};

var obj1 = {
    x: 90
};
console.log(obj.getX.call(obj1)); // 90
console.log(obj.getX.apply(obj1)); // 90
console.log(obj.getX.bind(obj1)); // returns getX function.
```

* Read https://tylermcginnis.com/this-keyword-call-apply-bind-javascript/  
to understand this operator.

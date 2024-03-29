Let’s look carefully at what’s going on in the call speedy.eat("apple").

The method speedy.eat is found in the prototype (=hamster), then executed with this=speedy (the object before the dot).

Then this.stomach.push() needs to find stomach property and call push on it. It looks for stomach in this (=speedy), but nothing found.

Then it follows the prototype chain and finds stomach in hamster.

Then it calls push on it, adding the food into the stomach of the prototype.

So all hamsters share a single stomach!

Both for lazy.stomach.push(...) and speedy.stomach.push(), the property stomach is found in the prototype (as it’s not in the object itself), then the new data is pushed into it.

Please note that such thing doesn’t happen in case of a simple assignment this.stomach=:

```
let hamster = {
  stomach: [],

  eat(food) {
    // assign to this.stomach instead of this.stomach.push
    this.stomach = [food];
  }
};

let speedy = {
   __proto__: hamster
};

let lazy = {
  __proto__: hamster
};

// Speedy one found the food
speedy.eat("apple");
alert( speedy.stomach ); // apple

// Lazy one's stomach is empty
alert( lazy.stomach ); // <nothing>
```

Now all works fine, because this.stomach= does not perform a lookup of stomach. The value is written directly into this object.

Also we can totally avoid the problem by making sure that each hamster has their own stomach:

```
let hamster = {
  stomach: [],

  eat(food) {
    this.stomach.push(food);
  }
};

let speedy = {
  __proto__: hamster,
  stomach: []
};

let lazy = {
  __proto__: hamster,
  stomach: []
};

// Speedy one found the food
speedy.eat("apple");
alert( speedy.stomach ); // apple

// Lazy one's stomach is empty
alert( lazy.stomach ); // <nothing>
```
As a common solution, all properties that describe the state of a particular object, like stomach above, should be written into that object. That prevents such problems.

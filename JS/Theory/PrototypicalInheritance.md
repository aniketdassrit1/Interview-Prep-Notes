### Prototypical Inheritance

* Inheritance refers to an object’s ability to access methods and other properties from another object. Objects can inherit things from other objects. Inheritance in JavaScript works through something called prototypes and this form of inheritance is often called prototypical inheritance.

* When we want to read a property from object, and it’s missing, JavaScript automatically takes it from the prototype.

* Eg. 
``` 
    let animal = {
        eats: true
    };

    let rabbit = {
        jumps: true
    };
    
    rabbit.__proto__ = animal; // (*)
    
    // we can find both properties in rabbit now:
    alert( rabbit.eats ); // true (**)
    alert( rabbit.jumps ); // true
```
* ##### Difference between `__proto__` and `prototype`?
  
`__proto__` is the property of a class instance and `prototype` is the property of class constructor.  
Eg.  
```
function iPhone() {}; // constructor
// a method for recognizing faces
iPhone.prototype.faceID = function() {};
// a method for taking 4k video
iPhone.prototype.video = function() {};

var newPhone = new iPhone(); // an iPhone 11
console.log(newPhone.prototype) // undefined
``` 
* ##### The value of this
```
// animal has methods
let animal = {
  walk() {
    if (!this.isSleeping) {
      alert(`I walk`);
    }
  },
  sleep() {
    this.isSleeping = true;
  }
};

let rabbit = {
  name: "White Rabbit",
  __proto__: animal
};

// modifies rabbit.isSleeping
rabbit.sleep();

alert(rabbit.isSleeping); // true
alert(animal.isSleeping); // undefined (no such property in the prototype)
```
**this** in each method call would be the corresponding object, evaluated at the call-time (before dot), not animal. So when we write data into this, it is stored into these objects.
* ##### hasOwnProperty
    * This function only check the property of the object not the inherited property.
    * This method is declared under Object.prototype.hasOwnProperty.

* ##### Differential prototype
    In this model, the methods are not copied from the parent to child. But instead there is a link between the children and their parent object.


* The arguments object is a special construct available inside all function calls. It represents the list of arguments that were passed in when invoking the function.  

* The arguments object is a local variable available within all non-arrow functions.

* The arguments object behaves like an array, but it is not an actual array. It does not have Array in its prototype chain and it does not respond to any array methods, e.g. arguments.sort() raises a TypeError.  

* Convert arguments object to a real Array.  
  **ES5 way**
  ```
  var args = Array.prototype.slice.call(arguments);  
  
  // Using an array literal is shorter than above   
     but allocates an empty array  
  
  var args = [].slice.call(arguments); 
  ```
  **ES6 way**
  ```
  let args = Array.from(arguments);  
  
  // or  
  
  let args = [...arguments];
  ```
* Type of arguments
    ```
    console.log(typeof arguments); // 'object'
    console.log(typeof arguments[0]); // returns the type   
                                         of the first argument 
    ```

* Separate out string, number and boolean
```
var x = [1,2,3, '1', '2', true, false];
var y = {
'number':[],
'string': [],
'boolean': [] 
}
```
Solution: 
```
 for(var i=0; i<x.length; i++) {
    switch(typeof x[i]) {
        case 'number':
            y['number'].push(x[i]);
            break;
        case 'string':
            y['string'].push(x[i]);
            break;
        default:
            y['boolean'].push(x[i]);
            break;
    }
```
```
var x = [1,2,3,4,5];
for(var i=1; i<5; i++) {
 if(x[i] === 3) continue;
	console.log(x[i]);
}
```

* Generics
* Decorator
* Interceptor
* Guard
* File upload
* Interface
* Attribute directive
* async pipe
* @Input and @Output
* Promise and observables
* Lazy loading
* What do you think of angular and react?
* How to create a multilingual website?
* AOT and JIT


```
function myConcat(seperator) {
    let args = Array.prototype.slice.call(arguments, 1);
    return args.join(seperator); 
}
```

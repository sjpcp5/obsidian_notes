# Javascript Conditional Operators
#Javascript Conditional Operators

## Checking if a an array holds [data], is null, or it exist
- Optional chaining ( ?. ) checks existence of array/data
``` 
let theArray = [{key:value}, 37, "Amber Jones", true]
theArray?.length ? true : false
```
- Nullish coalescing operator ( ?? ) evaluates if true on the left side otherwise returns whats on the left
```
let kikiArray = [{key:'value'}, 37, "Amber Jones", true]
kikiArray.[0].key ?? 'no key property '
// returns 'value'
```

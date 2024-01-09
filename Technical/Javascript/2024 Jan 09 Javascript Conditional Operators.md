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

## Creating a typescript Not Empty Array 
- [Written by Luca Del Puppo](https://dev.to/this-is-learning/typescript-readonlynotemptyarray-2id7)
- This read only type does not exist in typescript definitions but it can defined like so below
```
type NotEmptyArray<T> = [T, ...T[]];
```
*Note ( ...[] ) the three dots are a spread operator/syntax similar to using a 'for loop' iterating new values into an Array using array.push() or using Map to add new values to an object without erasing the existing values in the object*

- This type inherits all the characteristics of the array type and it adds another rule to it. It must have one item.
```
const array: NotEmptyArray<string> = ['apple']
```

- What if your using methods to remove values from an array and it becomes empty?
- This type prevents all the arrays' mutations 
```
type ReadOnlyNotEmptyArray<T> = Re
```
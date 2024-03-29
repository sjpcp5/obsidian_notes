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
- [I paraphrase this topic from an article written by Luca Del Puppo](https://dev.to/this-is-learning/typescript-readonlynotemptyarray-2id7) 
- This read only type does not exist in typescript definitions but it can defined like so below. It uses a [rest parameter](https://www.typescriptlang.org/docs/handbook/2/mapped-types.html#key-remapping-via-as) to assign the array type `Array<T>` or `T[]` instead of the `any` , which using `any` is not advisable. This kind of type would be defined as Mapped Type. 
```
type NotEmptyArray<T> = [T, ...T[]];
```
*Note ( ...[] ) the three dots are a spread operator/syntax similar to using a 'for loop' iterating new values into an Array using array.push() or using Map to add new values to an object without erasing the existing values in the object*

- This type inherits all the characteristics of the array type and it adds another rule to it. It must have one item.
```
const array: NotEmptyArray<string> = ['apple']
```

- What if your using methods to remove values from an array and it becomes empty?
- This type prevents all the arrays' mutations using the [Readonly modifier](https://www.typescriptlang.org/docs/handbook/2/objects.html#readonly-properties) which converts it to a  [Read-only array](https://www.typescriptlang.org/docs/handbook/2/objects.html#the-readonlyarray-type)
```
type ReadOnlyNotEmptyArray<T> = Readonly<NotEmptyArray<T>>;
```

- How to convert an Array to a Not Empty Array. 
- Using a user-defined [type guard](https://www.typescriptlang.org/docs/handbook/advanced-types.html) or a generic type function like below. This checks if an array has at least an element and if it respects the type assigned to it. It uses `as` to pass on the assigned data type to the array.   
```
function isNotEmptyArray<T>(as: T[]): as is NotEmptyArray<T> {
	return as.length > 0;
}
```
# TypeScript 5.5 Features

- <https://www.youtube.com/watch?v=FhT87_CqPug>

## Array Filter Fixes

```bash
const array = [1, 2, null, 3];

const numbers = array.filter(elem => elem != null);

numbers.forEach(number => {
    console.log(number + 2)
})
```

## Object Key Inference Fixes

type ObjType = Record<string, number | boolean>

```bash
function printNumber(obj: ObjType, key: string) {
    if (typeof obj[key] === 'number') {
        console.log(obj[key] + 1)
    }
}
```

## Regular Expression Features

## Set Methods

```bash
const fruits = new Set(["apples", "pears", "oranges"]);
const oranges = new Set(["oranges"]);

console.log(fruits.union(oranges))
console.log(fruits.intersection(oranges))
console.log(fruits.difference(oranges))
```

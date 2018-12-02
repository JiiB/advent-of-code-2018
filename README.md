# Advent of code 2018

https://adventofcode.com/2018

## Day 1

https://adventofcode.com/2018/day/1

Part 1:

`JavaScript`

```js
const response = await fetch("https://adventofcode.com/2018/day/1/input");
const data = await response.text();

data = data.split(/\n/g).reduce((acc, curVal) => acc + Number(curVal), 0);

console.log(`The result is: ${data}`);
```

Part 2:

```js
const results = {};
let sum = 0;

data = data.split(/\n/g).map(Number);

while (true) {
  for (const item of data) {
    results[sum] = true;
    sum += item;
    if (results[sum]) {
      return sum;
    }
  }
}
```

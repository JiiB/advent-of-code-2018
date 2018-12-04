# Advent of code 2018

https://adventofcode.com/2018

## Day 1

https://adventofcode.com/2018/day/1

Part 1:

`JavaScript`

```js
const response = await fetch("https://adventofcode.com/2018/day/1/input");
const input = await response.text();

input = input.split(/\n/g).reduce((acc, curVal) => acc + Number(curVal), 0);

console.log(`The result is: ${input}`);
```

Part 2:

```js
const results = {};
let sum = 0;

input = input.split(/\n/g).map(Number);

while (true) {
  for (const item of input) {
    results[sum] = true;
    sum += item;
    if (results[sum]) {
      return sum;
    }
  }
}
```

## Day 2

https://adventofcode.com/2018/day/2

Part 1:

`JavaScript`

```js
input = input.split(/\n/g);

const checksumData = {
  doubles: 0,
  tripes: 0
};

const lettersByLineArray = [];

for (const line of input) {
  const lettersByLine = {};
  for (const char of line.split("")) {
    if (!lettersByLine[char]) {
      lettersByLine[char] = 1;
    } else {
      lettersByLine[char]++;
    }
  }
  lettersByLineArray.push(lettersByLine);
}

for (const resItem of lettersByLineArray) {
  if (Object.values(resItem).filter(item => item === 2).length > 0) {
    checksumData.doubles++;
  }

  if (Object.values(resItem).filter(item => item === 3).length > 0) {
    checksumData.tripes++;
  }
}

// checksum result
console.log(
  `Checksum ${checksumData.doubles} * ${
    checksumData.tripes
  } = ${checksumData.doubles * checksumData.tripes}`
);
```

Part 2:

```js
input = input.split(/\n/g);

for (let i = 0; i < input.length; i++) {
  for (let j = i + 1; j < input.length; j++) {
    const line1 = input[i].split("");
    const line2 = input[j].split("");

    const commonLetters = {};
    let counter = 0;

    line1.forEach((letter, index) => {
      if (letter !== line2[index]) {
        counter++;
        commonLetters.letter1 = letter;
        commonLetters.word = line1.join("");
      }
    });

    if (counter === 1) {
      console.log(
        `The solution is: ${commonLetters.word.replace(
          commonLetters.letter1,
          ""
        )}`
      );
    }
  }
}
```

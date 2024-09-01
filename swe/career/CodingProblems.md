# 👨🏻‍💻 Coding Problems and Solutions

### Palindrome

- Given a string, check if it is palindrome
- Return a boolean as a response

JavaScript implementation:

```javascript
function solution(inputString) {
  // Remove non alphanumeric chars and lowercase all letters
  const cleanStr = inputString.toLowerCase().replace(/[^a-z0-9]/g, "");
  // Reverse the cleaned string
  const reversedString = cleanStr.split("").reverse().join("");

  return inputString === reversedString;
}
```

### Find largest product

- Given an array of integers, find the pair of adjacent elements with the largest product, return the product.

JavaScript implementation:

```javascript
function solution(inputArray) {
  let maxProduct = inputArray[0] * inputArray[1];
  for (let i = 1; i < inputArray.length; i++) {
    let product = inputArray[i] * inputArray[i + 1];

    if (product > maxProduct) {
      maxProduct = product;
    }
  }
  return maxProduct;
}
```

### Find consecutive

- Given an array of non-negative integers, arrange them from smallest to largest and find the total amount of additional integers needed to make all integers consecutive.
- I.e. given `[3, 0, 5]` we are missing integers: 1, 2, 4 so the answer should be 3.

JavaScript Implementation:

```javascript
function solution(statues) {
  let statuesNeeded = 0;
  const sortedStatues = statues.sort((a, b) => a - b);
  for (i = 0; i < sortedStatues.length - 1; i++) {
    let difference = sortedStatues[i + 1] - sortedStatues[i];
    statuesNeeded += difference - 1;
  }
  return statuesNeeded;
}
```

### Almost increasing sequence

JavaScript Implementation:

```javascript
function solution(sequence) {
  let count = 0;
  if (sequence.length === 1) return true;
  for (let i = 0; i < sequence.length; i++) {
    if (sequence[i] >= sequence[i + 1]) {
      count++;
      if (count > 1) {
        return false;
      }

      if (
        i > 0 &&
        sequence[i - 1] >= sequence[i + 1] &&
        i + 2 < sequence.length &&
        sequence[i] >= sequence[i + 2]
      ) {
        return false;
      }
    }
  }
  return true;
}
```

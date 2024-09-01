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

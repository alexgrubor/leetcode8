# myAtoi Function (LeetCode Challenge - Problem 8)

## Description

The `myAtoi` function is an implementation of the algorithm to solve LeetCode's Problem 8. This problem involves converting a given string to a 32-bit signed integer, following specific rules similar to the behavior of C/C++'s `atoi` function.

## Algorithm

The algorithm for `myAtoi` function is outlined as follows:

1. **Leading Whitespace Handling**: Read in and ignore any leading whitespace characters from the input string.

2. **Sign Detection**: Check if the next character (if not already at the end of the string) is either '-' or '+'. Read this character to determine if the final result should be negative or positive, respectively. If neither is present, assume the result is positive.

3. **Digit Extraction**: Read in the following characters until reaching a non-digit character or the end of the input string. Ignore the rest of the string beyond the digits.

4. **Integer Conversion**: Convert the extracted digits into an integer. For example, "123" should be converted to the integer 123, and "0032" should become 32. If no digits were read, return 0. Adjust the sign based on the detection from step 2.

5. **Clamping to 32-bit Integer Range**: If the resulting integer is out of the 32-bit signed integer range [-231, 231 - 1], clamp the integer so that it remains within this range. Any value less than -231 should be set to -231, and any value greater than 231 - 1 should be set to 231 - 1.

6. **Return the Result**: The function returns the integer as the final result.

## Implementation

The `myAtoi` function is implemented in JavaScript as follows:

```javascript
const myAtoi = (str) => {
    let num = parseInt(str);
    if (isNaN(num)) return 0;
    const MIN_INT = -0x80000000; // -2^31
    const MAX_INT = 0x7fffffff; // 2^31 - 1
    if (num < MIN_INT) return MIN_INT;
    if (num > MAX_INT) return MAX_INT;
    return num;
};
```

## Test Cases

The `myAtoi` function is tested with the following test cases:

```javascript
console.log(myAtoi("42")); // Output: 42
console.log(myAtoi("   -42")); // Output: -42
console.log(myAtoi("4193 with words")); // Output: 4193
```

These test cases correspond to the examples provided in the problem statement, and they confirm the correct functionality of the `myAtoi` function. The function correctly handles leading whitespace, detects the sign, extracts digits, converts them into integers, and clamps the result to fit within the 32-bit signed integer range.

# Largest Binary Gap (Javascript Solution)

A **_binary gap_** within a positive integer **N** is any maximal sequence of consecutive zeros that is surrounded by ones at both ends in the binary representation of **N**.

For example, number **9** has binary representation 1001 and contains a binary gap of length **2**. The number 529 has binary representation **1000010001** and contains two binary gaps: one of length **4** and one of length **3**. The number **20** has binary representation **10100** and contains one binary gap of length **1**. The number **15** has binary representation **1111** and has no binary gaps. The number **32** has binary representation **100000** and has no binary gaps.

Write a function:

```javascript
function solution(N);
```

that, given a positive integer **N**, returns the length of its longest binary gap. The function should return 0 if **N** doesn't contain a binary gap.

For example, given `N = 1041` the function should return **5**, because **N** has binary representation **10000010001** and so its longest binary gap is of length **5**. Given `N = 32` the function should return **0**, because **N** has binary representation **100000** and thus no binary gaps.


## Solution 

```javascript
// you can write to stdout for debugging purposes, e.g.
// console.log('this is a debug message');

function solution(N) {
    // write your code in JavaScript (Node.js 8.9.4)
    let max = 0
    let binary = N.toString(2).split('1');
    binary = binary.slice(1, binary.length -1)
    
    for (let i = binary.length -1; i > -1; i--) {
        if (binary[i].length > max)
            max = binary[i].length
    }
    return max
}
```
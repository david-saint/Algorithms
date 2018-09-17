# Diagonal Difference

Given a square matrix, calculate the absolute difference between the sums of its diagonals.

For example, the square matrix  is shown below:

```javascript
[
  [1, 2, 3],
  [4, 5, 6],
  [9, 8, 7]
]
```  
The left-to-right diagonal = `1 + 5 + 7 = 13`. The right to left diagonal = `3 + 5 + 9 = 17`. Their absolute difference is `|13 - 17| = 4`.

### Function description

Make a _diagonalDifference_ function in the editor below. It must return an integer representing the absolute diagonal difference.

_diagonalDifference_ takes the following parameter:
 * arr: an array of integers.

### Constraints

 * `-100 <= arr[i][j] <= 100`

### Output Format

Print the absolute difference between the sums of the matrix's two diagonals as a single integer.


## Solution

I first attempted the question in javascript.

```javascript
// Complete the diagonalDifference function below.
function diagonalDifference(arr) {

  let c = arr.length - 1; // store the array length - 1 to avoid calling it 
  let ld = [0, 0]; // The left diagonal [ sum, iterator ]
  let rd = [0, 0] // The right diagonal [ sum, iterator ]

  for (let i = 0; i <= c; i++) {
      // left diagonal is adding it
      ld[0] += arr[i][ld[1]];
      ld[1] += 1;
      // right diagonal is adding it
      rd[0] += arr[i][c - rd[1]];
      rd[1] += 1;
  }

  return Math.abs(ld[0] - rd[0]);
}
```
What's happening in the for loop? It goes through the n x n matrix row by row. On the **_ith_** row, the ld's iterator would be the column to get from there. Then increase the iterator. The same was done for the right iterator.

It worked but I wasn't still satisfied with the complexity of the algo, so I optimized it in python.

```python
# Complete the diagonalDifference function below.
def diagonalDifference(arr):
    sum = 0
    arrcount = len(arr)
    for i in range(0, arrcount):
        sum += (arr[i][i] - arr[i][(arrcount-1) -i])
    
    return abs(sum);
```

For each row I get the mirrored element and subtract them. For example :
```javascript
[
  [1, 2, 3],
  [4, 5, 6],
  [9, 8, 7]
]
``` 
On the first loop I get **1 - 3**, the second loop I get **5 - 5**, and the third loop I get **7 - 9**. While summing it up int the sum variable to get **sum = -2 + 0 + (-2)**. Therefore **sum = abs(-4) = 4**
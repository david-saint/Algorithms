# Kaprekar's Constant

Have the function 
```javascript
KaprekarsConstant(num)
```
take the num parameter being passed which will be a 4-digit number with *at least two distinct digits*. 

Your program should perform the following routine on the number:

1. Arrange the digits in descending order and in ascending order (adding zeroes to fit it to a 4-digit number)
2. Subtract the smaller number from the bigger number.
3. Then repeat the previous step.

Performing this routine will always cause you to reach a fixed number: **6174**. Then performing the routine on **6174** will always give you **6174** **(7641 - 1467 = 6174)**. 

Your program should return the number of times this routine must be performed until **6174** is reached. 

For example: if num is **3524** your program should return **3** because of the following steps: 
1. **5432 - 2345 = 3087**
2. **8730 - 0378 = 8352**
3. **8532 - 2358 = 6174**. 


## Solution

I first created a Padding function to convert **1-3** digit numbers to 4-digit numbers.

```javascript
function pad(num) {
  if (num < 10)
    return '000'+num;

  if (num < 100)
    return '00'+num;

  if (num < 1000)
    return '0'+num;

  return num;
}
```

Then I created the Kaprekars function

```javascript
function KaprekarsConstant(num) {

  let min = [...pad(num).toString()].sort().join('');
  let max = [...min].sort().reverse().join('');
  let inc = 1;

  while ((parseInt(max) - parseInt(min)) != 6174)
  {
    let ans = parseInt(max) - parseInt(min);

    min = [...pad(ans).toString()].sort().join('');
    max = [...min].sort().reverse().join('');
    inc += 1;
  }

  return inc;
}
```
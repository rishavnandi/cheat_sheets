# Bitwise Operators

| Operator | Function            |  Remarks   |
| -------- | ------------------- | --- |
| &        | Bitwise AND         |     |
| \|       | Bitwise OR          |     |
| ^        | Bitwise XOR         |  Use XOR 3 times to swap two numbers, n^n is 0 and 0^n is n   |
| ~        | Bitwise Inverse     |     |
| >>       | Bitwise Right Shift | >> 1 is equivalent to dividing by 2    |
| <<       | Bitwise Left Shift  | << 1 is equivalent to multiplying by 2    |

- Using bitwise operators in loops instead of usual multiplication and division by 2 gives much better time complexity ([[Time Complexity]])
-   To find i bit left shift bit by i places then use &
-   To set a bit left shift bit by i places then use |
-   To clear a bit left shift bit by i places then use ~ to invert then use &
-   To find number of bits to change to convert a to b use ^
-   To find number of set bits use n & (n-1)
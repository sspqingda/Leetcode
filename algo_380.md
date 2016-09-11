#338. Counting Bits  QuestionEditorial Solution  My Submissions
```
Total Accepted: 44181
Total Submissions: 75641
Difficulty: Medium
Given a non negative integer number num. For every numbers i in the range 0 ≤ i ≤ num calculate the number of 1's in their binary representation and return them as an array.

Example:
For num = 5 you should return [0,1,1,2,1,2].

Follow up:

It is very easy to come up with a solution with run time O(n*sizeof(integer)). But can you do it in linear time O(n) /possibly in a single pass?
Space complexity should be O(n).
Can you do it like a boss? Do it without using any builtin function like __builtin_popcount in c++ or in any other language.

```

```
```i&(i-1) drops the lowest set bit. 
For example: i = 14, its binary representation is 1110, so i-1 is 1101, i&(i-1) = 1100, 
the number of "1" in its binary representation decrease one, so ret[i] = ret[i&(i-1)] + 1.
```java
public class Solution {
    public int[] countBits(int num) {
        int[] ret = new int[num + 1];
        for (int i = 1; i <= num; ++i)
            ret[i] = ret[i&(i-1)] + 1;
        return ret;
    }
}
```
```

```java
public class Solution {
    public int[] countBits(int num) {
        int[] f = new int[num + 1];
        for (int i=1; i<=num; i++) f[i] = f[i >> 1] + (i & 1);
        return f;
    }
}
```

```java
public class Solution {
    public int[] countBits(int num) {
        int[] ret = new int[num + 1];
        for (int i = 1; i <= num; ++i)
            ret[i] = ret[(i - (i & (-i)))] + 1;
        return ret;
```

For the the first solution : f[i] = f[i >> 1] + (i & 1) .
This is more straight-forward. Right shit by 1 bit,
compare to previously, the number of set bit would either reduce by 1(when number is odd) or
no change(when number is even), that is why we add ( i & 1 ) which reflects whether the number is even or odd.
For the second solution: ret[(i - (i & (-i)))] + 1 .
This is more interesting, we first isolate the right-most set bit and then deduct the number represented by it
from our number i(ex. by deduction : 11 0100 -> 11 0000).
We can tell for sure, we definitely lose 1 set bit by the deduction so we just add 1 back.
```

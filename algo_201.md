#201. Bitwise AND of Numbers Range  QuestionEditorial Solution  My Submissions
```
Total Accepted: 42466
Total Submissions: 131470
Difficulty: Medium
Given a range [m, n] where 0 <= m <= n <= 2147483647, return the bitwise AND of all numbers in this range, inclusive.

For example, given the range [5, 7], you should return 4.
```

```java
public class Solution {
    public int rangeBitwiseAnd(int m, int n) {
        int r=Integer.MAX_VALUE;
        while((m&r)!=(n&r))  r=r<<1;
        return n&r;
    }
}
```

```java

public class Solution {
    public int rangeBitwiseAnd(int m, int n) {
        if(m==0) return 0;
        int movefactor = 1;
        while(m!=n)
        {
            m>>=1;
            n>>=1;
            movefactor <<=1;
        }
        return m*movefactor;
    }
}
```

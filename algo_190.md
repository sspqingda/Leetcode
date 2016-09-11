
#190. Reverse Bits  QuestionEditorial Solution  My Submissions

```

Reverse bits of a given 32 bits unsigned integer.

For example, given input 43261596 (represented in binary as 00000010100101000001111010011100), return 964176192 (represented in binary as 00111001011110000010100101000000).


```

```java
public class Solution {
    // you need treat n as an unsigned value
    public int reverseBits(int n) {
        int res =0;
        for(int i =0 ;i<32;i++)
        {
            int c = (n>>(32-i)&1)<<i;
            res |= c;
        }
        return res;
    }
}
```


```java

public class Solution {
    // you need treat n as an unsigned value
    int[] tb = {0,8,4,12,2,10,6,14,1,9,5,13,3,11,7,15};

    public int reverseBits(int n) {
        
        int res = 0;
        int cur = 0;
        
        for(int i = 0;i<8;i++)
        {
            res<<=4;
            cur  = n&0xF;
            res |=tb[cur];
            n>>=4;
        }
        
        return res;
    }

```

#318. Maximum Product of Word Lengths  QuestionEditorial Solution  My Submissions
```
Total Accepted: 32630
Total Submissions: 79345
Difficulty: Medium
Given a string array words, find the maximum value of length(word[i]) * length(word[j]) where the two words do not share common letters. You may assume that each word will contain only lower case letters. If no such two words exist, return 0.

Example 1:
Given ["abcw", "baz", "foo", "bar", "xtfn", "abcdef"]
Return 16
The two words can be "abcw", "xtfn".

Example 2:
Given ["a", "ab", "abc", "d", "cd", "bcd", "abcd"]
Return 4
The two words can be "ab", "cd".

Example 3:
Given ["a", "aa", "aaa", "aaaa"]
Return 0
No such pair of words.

Credits:
Special thanks to @dietpepsi for adding this problem and creating all test cases.

Subscribe to see which companies asked this question

```


```java
public class Solution {
    public int maxProduct(String[] words) {
        int[] nums = new int[words.length];
        for(int i = 0;i<words.length;i++)
        {
       
            for(int z =0;z<words[i].length();z++)
            {
                nums[i] |=(1<<(words[i].charAt(z)-'a'));
                
            }
           
        }
        
        int res = 0;
        for(int j =0;j<words.length;j++)
        {
            for(int k = j+1; k<words.length;k++)
            {
                if((nums[j]&nums[k])==0){
                    res= Math.max(res,words[j].length()*words[k].length());
                }
            }
        }
        return res;
    }
}
```



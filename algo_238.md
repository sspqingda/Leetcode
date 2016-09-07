```
238. Product of Array Except Self  QuestionEditorial Solution  My Submissions
Total Accepted: 60391
Total Submissions: 133992
Difficulty: Medium
Given an array of n integers where n > 1, nums, return an array output such that output[i] is equal to the product of all the elements of nums except nums[i].

Solve it without division and in O(n).

For example, given [1,2,3,4], return [24,12,8,6].

Follow up:
Could you solve it with constant space complexity? (Note: The output array does not count as extra space for the purpose of space complexity analysis.)

Subscribe to see which companies asked this question
```


``` java
public class Solution {
    public int[] productExceptSelf(int[] nums) {
        int[] result = new int[nums.length];
        for (int i = 0; i < result.length; i++) result[i] = 1;
        int left = 1, right = 1;
        for (int i = 0, j = nums.length - 1; i < nums.length - 1; i++, j--) {
            left *= nums[i];
            right *= nums[j];
            result[i + 1] *= left;
            result[j - 1] *= right;
        }
        return result;

    }
}
```
```java

public class Solution {
    public int[] productExceptSelf(int[] nums) {
        int len = nums.length;
        int[] result = new int[len];
        result[len-1] = 1;
        for(int i =len-2;i>=0;i-- )
        {
            result[i] = result[i+1]*nums[i+1];   
        }
        int left =1;
        for(int i= 0;i<len;i++)
        {
            result[i] *=left;
            left*=nums[i];
        }
        return result;
    }
}
```

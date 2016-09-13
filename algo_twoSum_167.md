```
Given an array of integers that is already sorted in ascending order, find two numbers such that they add up to a specific target number.

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2. Please note that your returned answers (both index1 and index2) are not zero-based.

You may assume that each input would have exactly one solution.

Input: numbers={2, 7, 11, 15}, target=9
Output: index1=1, index2=2
```
```java

public class Solution {
    public int[] twoSum(int[] numbers, int target) {
        int start = 0, end = numbers.length-1;
        int[] res = new int[2];
        while(start< end)
        {
            int sum = numbers[start] + numbers[end];
            if(sum == target ) 
            {
                res[0] = start+1;
                res[1] = end+1;
                break;
            }
            else if (sum < target) start++;
            else end--;
            
        }
        
        return res;
        
    }
}
```

```java

public class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer,Integer> map = new HashMap<Integer,Integer>();
        int[] result = new int[2];
        for (int i =0;i<nums.length;i++)
        {
            if(map.containsKey(target-nums[i]))
            {
                result[0] = map.get(target-nums[i]);
                result[1] = i;
            }
            else
            {
                map.put(nums[i],i);
            }
        }
        
        return result;
        
    }
}

```

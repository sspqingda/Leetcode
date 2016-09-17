#349. Intersection of Two Arrays  QuestionEditorial Solution  My Submissions
```
Difficulty: Easy
Given two arrays, write a function to compute their intersection.

Example:
Given nums1 = [1, 2, 2, 1], nums2 = [2, 2], return [2].

Note:
Each element in the result must be unique.
The result can be in any order.
```
```java
public class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        Set<Integer> res = new HashSet<Integer>();
        Set<Integer> temp = new HashSet<Integer>();
        for(int n: nums1)
        {
            temp.add(n);
        }
        for(int num: nums2)
        {
            if(temp.contains(num))
            {
                res.add(num);
            }
        }
        int[] ret = new int[res.size()];
        int i =0;
        for(int x : res)
        {
            ret[i++] =x;
        }
       return ret;
    }
}
```

```java
public class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        Arrays.sort(nums1);
        Arrays.sort(nums2);
        HashSet<Integer> set = new HashSet<Integer>();
        int i = 0, j=0;
        while(i<nums1.length && j< nums2.length)
        {
            if(nums1[i]<nums2[j]) i++;
            else if(nums1[i]>nums2[j]) j++;
            else
            {
                set.add(nums1[i]);
                i++;
                j++;
            }
        }
        
        int[] res = new int[set.size()];
        int k=0;
        for(int s: set)
        {
            res[k++]=s;
        }
        return res;
    }
}
```

```java
public class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        Arrays.sort(nums1);
        HashSet<Integer> set = new HashSet<Integer>();
        for(int n: nums2)
        {
            if(binarySearch(nums1,0,nums1.length-1,n)!=-1)  set.add(n);
        }
        
        int i =0;
        int[] res = new int[set.size()];
        for(int x:set)
        {
            res[i++]=x;
        }
        return res;
    }
    
    private int  binarySearch(int[] nums,int low, int high, int target)
    {
        while(low<=high)
        {
            int mid = low+(high-low)/2;
            if(nums[mid] == target)  return mid;
            else if(nums[mid]< target) low = mid+1;
            else  high = mid-1;
        }
        
        return -1;
    }
}
```

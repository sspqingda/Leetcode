#3. Longest Substring Without Repeating Characters
```
Given a string, find the length of the longest substring without repeating characters.

Examples:

Given "abcabcbb", the answer is "abc", which the length is 3.

Given "bbbbb", the answer is "b", with the length of 1.

Given "pwwkew", the answer is "wke", with the length of 3. Note that the answer must be a substring, "pwke" is a subsequence and not a substring.

Subscribe to see which companies asked this question
```
```java
public class Solution {
    public int lengthOfLongestSubstring(String s) {
        HashMap<Character,Integer> map = new HashMap<Character,Integer>();
        int max  =0;
        int i = 0;
        while(i<s.length())
        {
            char c = s.charAt(i);
            if(!map.containsKey(c)) map.put(c,i);
            else
            {
                int cur_len = map.size();
                Iterator it = map.entrySet().iterator();
                while (it.hasNext()) {
                    Map.Entry pair = (Map.Entry)it.next();
                    if((int)pair.getValue() < map.get(c)) it.remove(); // avoids a ConcurrentModificationException
                }
                max = (max<cur_len)?cur_len:max;
                map.put(c,i);
            }
            i++;
        }
        if( i==s.length()) max = (max>map.size())?max:map.size();
        
        return max;
        
    }
}
```

```java
public class Solution {
   
    public int lengthOfLongestSubstring(String s) 
    {  
        int N = s.length();
        int maxLen = 0;
        HashMap<Character,Integer> map = new HashMap<Character,Integer>();
        int start =0,end =0;
        for(;end<N;end++)
        {
            char cur = s.charAt(end);
            if(map.containsKey(cur) && start <= map.get(cur))
            {
                maxLen = Math.max(end -start,maxLen);
                start = map.get(cur) +1;
            }
            
            map.put(cur,end);
        }
        maxLen = Math.max(end-start, maxLen);
        return maxLen;
    }  
  
   
}
```

```java
public class Solution {
   
    public int lengthOfLongestSubstring(String s) 
    {  
        int N = s.length();
        int maxLen = 0;
        
        int start =0,end =0;
        for(;end<N;end++)
        {
            char cur = s.charAt(end);
            for(int i = start ; i<end;i++)
            {
                if(s.charAt(i) == s.charAt(end))
                {
                    maxLen = Math.max(end-start,maxLen);
                    start = i+1;
                }
            }
        }
        maxLen = Math.max(end-start, maxLen);
        return maxLen;
    }  
  
   
}
```

```java
public class Solution {
   
    public int lengthOfLongestSubstring(String s) 
    {  
        int maxlen = 0;
        int start = 0, end =0;
        for(;end<s.length();end++)
        {
            for(int i = start;i<end;i++)
            {
                if(s.charAt(i) == s.charAt(end)) 
                {
                    maxlen = (maxlen>end-start)? maxlen:(end-start);
                    start = i+1;
                    break;
                }
            }
        }
        maxlen = (maxlen>end-start)? maxlen:(end-start);
        return maxlen;
    }  
    
}
```

## Problem Statement

Given two strings, `s` and `t`, return `true` if `t` is an anagram of `s`, and `false` otherwise.
## Example Cases

- **Example 1**:
    - Input: `s = "anagram"`, `t = "nagaram"`
    - Output: `true`
    
- **Example 2**:    
    - Input: `s = "rat"`, `t = "car"`
    - Output: `false`
## Solution Approaches

There are several methods to solve this problem:

## Hash Array Method ( Character Count Array )

```java
class Solution {
    public boolean isAnagram(String s, String t) {
        int[] alphabet = new int[26];
        for (char c : s.toCharArray()) {
            alphabet[c - 'a']++;
        }
        for(char c : t.toCharArray()){
            alphabet[c - 'a']--;
        }
        for(int i=0;i<26;i++){
            if (alphabet[i] != 0){return false;}
        }
        return true; 
    }
}
```




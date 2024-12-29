
The problem **LeetCode 242: Valid Anagram** requires determining if one string is an anagram of another. An anagram is defined as a word or phrase formed by rearranging the letters of another, using all original letters exactly once.
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

1. **Length Check**:
    
    - If the lengths of `s` and `t` are not equal, return `false` immediately since they cannot be anagrams.
    
2. **Character Counting**:
    
    - Utilize a hash table (or a Counter from the `collections` module in Python) to count occurrences of each character in the first string `s`.
    - For each character in the second string `t`, decrement its count in the hash table.
    - If any count goes below zero, it indicates that `t` has more occurrences of that character than `s`, and thus return `false`.
    
3. **Final Verification**:
    
    - If all counts are zero after processing both strings, return `true`, confirming that `t` is an anagram of `s`.


## Tutorial Videos:

mandarin Chinese: https://www.bilibili.com/video/BV1YG411p7BA/

## Hash Array Approach - Java

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


## Hash Array Approach - Python

```python
    """
    LeetCode 242 - Valid Anagram
    Time Complexity: O(n) where n is the length of the strings
    Space Complexity: O(1) since we use fixed size array of 26 characters
    
    Approach:
    1. First check if lengths are different - if so, they can't be anagrams
    2. Use a fixed-size array of 26 positions (one for each lowercase letter)
    3. Increment counts for first string, decrement for second string
    4. If all counts are zero at the end, strings are anagrams
    
    Example:
    s = "anagram", t = "nagaram"
    - Create array of size 26, initialized to 0
    - For 'a' in s: array[0]++
    - For 'n' in s: array[13]++
    - etc...
    - Then decrement for each char in t
    - If array is all zeros at end, they're anagrams
    """

class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        # If lengths are different, they can't be anagrams
        if len(s) != len(t) :
            return False;
            
        # Create array of 26 zeros (one for each lowercase letter)
        hash = [0]*26
		
		# Process both strings in single pass
		# Increment count for char in s (a = 0, b = 1, etc)
        for i in range (0,len(s)):
            hash[ord(s[i])-ord('a')] +=1
        # Decrement count for char in t
        for i in range (0,len(t)):
            hash[ord(t[i])-ord('a')] -=1
            
	    # Check if all counts are zero
        return all( anyHash==0  for anyHash in hash)
```

## Problem Statement

You are given an array of strings `words`. Your task is to identify all characters that appear in every string within this array, and return them in an array format. The order of characters in the output can be arbitrary.

## Example Cases

- **Example 1**:
    - Input: `words = ["bella","label","roller"]`
    - Output: `["e","l","l"]`
    
- **Example 2**:
    - Input: `words = ["cool","lock","cook"]`
    - Output: `["c","o"]`
    

## Solution Approaches

There are several efficient methods to solve this problem:

## Hash Array Method ( Character Count Array )

based on [[242 Valid Anagram]]

```java
class Solution {
    public List<String> commonChars(String[] words) {

        List<String> result = new ArrayList<>();
        int[] alphabet = new int[26];
        alphabet = counter(words[0]);

        for (String s :  words ){
            int[] alphabetCur = counter(s);
            for(int j=0;j<26;j++){
                alphabet[j]=Math.min(alphabet[j],alphabetCur[j]);
            }
        }
        
        for(int i=0;i<26;i++){
            while(alphabet[i] != 0){
                    result.add(Character.toString((char) (i + 'a')));
                    alphabet[i]--;    
            }
        }
        return result;
    }

    private  int[] counter(String s){
        int[] alphabet = new int[26];
        for (char c : s.toCharArray()) {
            alphabet[c - 'a']++;
        }
        return alphabet;
    }
}
```





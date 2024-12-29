LeetCode 1002, titled **Find Common Characters**, requires you to identify characters that appear in every string of a given list, including duplicates. Below is a concise overview of the problem, the approach to solve it, and an example implementation.

processing Order 242-1002
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

1. **Character Frequency Count**:
    
    - Start by counting the frequency of each character in the first word.
    - For each subsequent word, update the counts to keep only the minimum occurrences of each character found so far.
2. **Constructing Result**:
    - Build the result list based on the final counts after processing all words.

## Approach Video

English Video: https://www.youtube.com/watch?v=QEESBA2Q_88

## Hash Array Approach - Java

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

## Hash Array Approach - Python


```python
class Solution:

    def commonChars(self, words: List[str]) -> List[str]:

        # Initialize result with infinity for each character
        result = [float('inf')] * 26

        # Count characters in the first word
        for c in words[0]:
            count = [0] * 26
            for c in words[0]:
                index = ord(c) - ord('a')
                count[index] += 1
            for j in range(26):
                result[j] = min(result[j], count[j])

        # Count characters in subsequent words
        for i in range(1, len(words)):
            cur_count = [0] * 26
            for c in words[i]:
                index = ord(c) - ord('a')
                cur_count[index] += 1
            for j in range(26):
                result[j] = min(result[j], cur_count[j])

        # Construct output based on result counts
        output = []
        for i in range(26):
            if result[i] > 0 and result[i] != float('inf'):
                output.extend([chr(i + ord('a'))] * result[i])


        return output
```
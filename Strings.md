# # Reverse Words in a String

## My Initial Approach:

```cpp
class Solution {
public:
    string reverseWords(string str) {
        // Check for empty string
        if(str.length()==0){
            return str;
        }
        
        // Trim leading and trailing spaces
        int start = 0, end = str.length();
        while(start < end && isspace(str[start])){
            start++;
        }
        while(end > start && isspace(str[end-1])){
            end--;
        }
        str = str.substr(start, end-start);
        
        // Process spaces between words
        string s = "";
        int i = 0;
        while(i < str.length()){
            if(str[i] != ' ' && str[i+1] == ' ') {
                s += str[i];
            }
            if(str[i] != ' ' && str[i+1] != ' ') {
                s += str[i];
            }
            else if(str[i] == ' ' && str[i+1] != ' ') {
                s += ' ';
            }
            i++;
        }

        // Reverse the processed string
        reverse(s.begin(), s.end());

        // Reverse individual words
        char* star = &s[0];
        for(char &c : s) {
            if(c == ' ') {
                reverse(star, &c);
                star = &c + 1;
            }
        }
        reverse(star, &s[s.length()]);
        
        return s;
    }
};
```
# Approach:
- 1. Take two variable and track the ocuurance of first and last character. This is to remove the spaces at the starting and ending of the string;
- 2.After getting the position make a substr to store the trimmed string.
- 3.Next up is to deal with the space in between so for that make a new string named s and iterate over the substr previously made and store the correct string(with only necessery spaces)
- 4.Reverse the String s.
- 5.now identify and reverse the words.

**Time Complexity:O(n)**

## Optimized Approach:

```cpp
class Solution {
public:
    string reverseWords(string str) {
        int n = str.length();
        int start = 0;
        
        // Remove leading spaces
        while (start < n && str[start] == ' ')
            start++;
        
        // Reverse the entire string
        reverse(str.begin() + start, str.end());
        
        // Reverse individual words
        int s = start;
        for (int e = start; e < n; e++) {
            if (str[e] == ' ') {
                reverse(str.begin() + s, str.begin() + e);
                s = e + 1; // Move to the start of the next word
            }
        }
        
        // Reverse the last word
        reverse(str.begin() + s, str.end());
        
        // Remove extra spaces
        int j = 0;
        for (int i = start; i < n; i++) {
            if (str[i] != ' ' || (i > 0 && str[i - 1] != ' '))
                str[j++] = str[i];
        }
        str.resize(j);
        
        return str;
    }
};
```
### Approach:
- 1.Trimming Leading Spaces:
The start variable is used to keep track of the index where non-space characters start in the string. We iterate through the string until we find the first non-space character.


- 2.Reversing the Entire String:
Once leading spaces are trimmed, we reverse the entire string using the reverse function from the C++ standard library, applied to the substring starting from start to the end of the string. This effectively places the words in the correct order while also reversing them.

- 3.Reversing Individual Words:
We iterate through the string again, tracking the start (s) and end (e) indices of each word. When we encounter a space character, we reverse the word bounded by s and e - 1 using the reverse function. Then, we update s to point to the start of the next word.

- 4.Removing Extra Spaces:
After reversing the words, we remove any extra spaces in the string. We iterate through the string, copying non-space characters to their correct positions. We skip copying consecutive space characters, ensuring that only one space character remains between words.

- 5.String Resizing:
After removing extra spaces, we resize the string to remove any excess characters that might have remained after copying the non-space characters.
These optimizations streamline the process, avoiding unnecessary string manipulations and making the code more efficient. Overall, the time complexity remains O(n).

**Time Complexity:O(n)**

**Visualization:**

Original String: "  hello   world  "

1. Trim Leading Spaces:
   Start: "  hello   world  "
          ^

2. Reverse Entire String:
   "  dlrow   olleh  "

3. Reverse Individual Words:
   After reversing "dlrow" and "olleh":
   "  world   hello  "

4. Remove Extra Spaces:
   After removing extra spaces:
   " world hello "

Final Result: "world hello"

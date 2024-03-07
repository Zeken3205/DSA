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
1. Take two variable and track the ocuurance of first and last character. This is to remove the spaces at the starting and ending of the string;
2.After getting the position make a substr to store the trimmed string.
3.Next up is to deal with the space in between so for that make a new string named s and iterate over the substr previously made and store the correct string(with only necessery spaces)
4.Reverse the String s.
5.now identify and reverse the words.

###Time Complexity:O(n)



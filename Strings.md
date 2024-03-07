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


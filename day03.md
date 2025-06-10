```cpp
class Solution {
public:
    string longestPalindrome(string s) {
        if (s.empty()) return "";
        
        string p;
        int plen = 0;

        for (int i = 0; i < s.length(); i++) {
            // Check odd-length palindromes centered at s[i]
            int l = i, r = i;
            while (l >= 0 && r < s.length() && s[l] == s[r]) {
                if (r - l + 1 > plen) {
                    p = s.substr(l, r - l + 1);
                    plen = r - l + 1;
                }
                l--;
                r++;
            }

            // Check even-length palindromes centered between s[i] and s[i+1]
            l = i;
            r = i + 1;
            while (l >= 0 && r < s.length() && s[l] == s[r]) {
                if (r - l + 1 > plen) {
                    p = s.substr(l, r - l + 1);
                    plen = r - l + 1;
                }
                l--;
                r++;
            }
        }

        return p;
    }
};

```

```cpp
class Solution {
public:
    int maxDifference(string s) {
        vector<int> freq(26, 0);

        // Count frequencies
        for (char c : s) {
            freq[c - 'a']++;
        }

        int maxDiff = INT_MIN;
        vector<int> oddFreqs;
        vector<int> evenFreqs;

        // Split odd and even frequencies
        for (int f : freq) {
            if (f == 0) continue;
            if (f % 2 == 0)
                evenFreqs.push_back(f);
            else
                oddFreqs.push_back(f);
        }

        // Find max(odd - even)
        for (int odd : oddFreqs) {
            for (int even : evenFreqs) {
                maxDiff = max(maxDiff, odd - even);
            }
        }

        return maxDiff;
    }
};

```

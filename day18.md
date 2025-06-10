```cpp
class Solution {
public:
    bool checkSubarraySum(vector<int>& nums, int k) {
           std::unordered_map<int, int> remainderMap;
        int cumulativeSum = 0;
        remainderMap[0] = -1; 
        for (int i = 0; i < nums.size(); ++i) {
            cumulativeSum += nums[i];
            int remainder = cumulativeSum % k;
            if (remainderMap.find(remainder) != remainderMap.end()) {
                if (i - remainderMap[remainder] >= 2) {
                    return true;
                }
            } else {
                remainderMap[remainder] = i;
            }
        }
        return false;
    }
};
```

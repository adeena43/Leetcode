```cpp
class Solution {
public:
    vector<vector<int>> divideArray(vector<int>& nums, int k) {
        vector<vector<int>> result;
        sort(nums.begin(), nums.end());

        for (int i = 0; i < nums.size(); i += 3) {
            int a = nums[i];
            int b = nums[i + 1];
            int c = nums[i + 2];
            
            if (c - a > k) {
                return {}; // Cannot form a group with max-min > k
            }
            result.push_back({a, b, c});
        }

        return result;
    }
};

```

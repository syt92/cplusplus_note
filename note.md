# cplusplus note

**如果輸入的字元長度超過指定大小:**

* cin.getline會關閉輸入
* cin.get會將多的字原存放在緩衝區

## leetcode 1

[problem description](https://leetcode.com/problems/two-sum/description/)

```c++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        int nums_size = nums.size();
        std::vector<int> ans;
        for(int i=0; i<nums_size-1; i++)
        {
            for(int j=i+1; j<nums_size; j++)
            {
                 if(nums[i]+nums[j] == target)
                {
                    ans.push_back(i);
                    ans.push_back(j);
                }
            }
        }
        return ans;
    }
};
```

Input: nums = [3,2,4], target = 6, Output: [1,2]</br>
i=0 : j=1, j=2</br>
i=1 : j=2

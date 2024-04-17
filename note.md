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

```c++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> maps;
        int i, tmp;
        //build unordered_map maps
        for(i=0; i<nums.size(); i++)
            maps[nums[i]] = i;
        for(i=0; i<nums.size(); i++)
        {
            tmp = target-nums[i];
            if(maps.count(tmp) && i != maps[tmp])
                break;
        }
        return {i, maps[tmp]};
    }
};
```

2024/4/16 : 但是有個疑問, unordered_map的key能重複嗎?</br>
2024/4/17 : unordered_map裡的key在hash table中都是唯一的</br>

## leetcode 169

```c++
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        unordered_map<int, int> maps;
        int nums_size = nums.size();
        int i;
        for(i=0; i<nums_size; i++)//
            maps[nums[i]] = 0;//
        for(i=0; i<nums_size; i++)
        {
            if(maps.count(nums[i]))
                maps[nums[i]]++;
        }
        nums_size = nums_size/2;
        int max_key;
        for(auto it = maps.begin(); it != maps.end(); it++)
        {
            if(it->second > nums_size)
            {
                max_key = it->first;
                break;
            }
        }
        return max_key;
    }
};
```
2024/4/17 : 為什麼把初始化maps那段拿掉會跑不過, 難道沒有初始化maps成功?</br>

2024/4/17 : 如何歷遍maps的成員, 型別是什麼?</br>
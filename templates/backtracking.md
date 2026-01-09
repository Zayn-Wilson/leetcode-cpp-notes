# 回溯算法模板

## 核心思想

回溯 = 递归 + 撤销选择

```
做选择 -> 递归 -> 撤销选择
```

## 通用模板

```cpp
void backtrack(path, choices) {
    if (end_condition) {
        result.push_back(path);
        return;
    }
    
    for (choice : choices) {
        path.push_back(choice);
        backtrack(path, choices);
        path.pop_back();
    }
}
```

## 示例：全排列

```cpp
class Solution {
public:
    vector<vector<int>> result;
    
    vector<vector<int>> permute(vector<int>& nums) {
        vector<int> path;
        vector<bool> used(nums.size(), false);
        backtrack(nums, path, used);
        return result;
    }
    
    void backtrack(vector<int>& nums, vector<int>& path, vector<bool>& used) {
        if (path.size() == nums.size()) {
            result.push_back(path);
            return;
        }
        
        for (int i = 0; i < nums.size(); i++) {
            if (used[i]) continue;
            
            path.push_back(nums[i]);
            used[i] = true;
            backtrack(nums, path, used);
            path.pop_back();
            used[i] = false;
        }
    }
};
```

## 常见变体

| 问题类型 | 递归起点 | 是否可重复 |
|---------|---------|----------|
| 排列 | 0 | 用 used 数组 |
| 组合 | start | i + 1 |
| 子集 | start | i + 1 |
| 可重复组合 | start | i |
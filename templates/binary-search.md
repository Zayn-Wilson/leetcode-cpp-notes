# 二分查找模板

## 模板一：标准二分（查找精确值）

```cpp
int binarySearch(vector<int>& nums, int target) {
    int left = 0, right = nums.size() - 1;
    
    while (left <= right) {
        int mid = left + (right - left) / 2;  // 防止溢出
        
        if (nums[mid] == target) {
            return mid;
        } else if (nums[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    return -1;  // 未找到
}
```

## 模板二：查找左边界（第一个 >= target 的位置）

```cpp
int lowerBound(vector<int>& nums, int target) {
    int left = 0, right = nums.size();
    
    while (left < right) {
        int mid = left + (right - left) / 2;
        
        if (nums[mid] < target) {
            left = mid + 1;
        } else {
            right = mid;
        }
    }
    
    return left;  // 返回第一个 >= target 的位置
}
```

## 模板三：查找右边界（最后一个 <= target 的位置）

```cpp
int upperBound(vector<int>& nums, int target) {
    int left = 0, right = nums.size();
    
    while (left < right) {
        int mid = left + (right - left) / 2;
        
        if (nums[mid] <= target) {
            left = mid + 1;
        } else {
            right = mid;
        }
    }
    
    return left - 1;  // 返回最后一个 <= target 的位置
}
```

## 使用场景

1. **有序数组查找**：直接使用模板一
2. **查找插入位置**：使用模板二
3. **查找第一个/最后一个等于 target 的位置**：使用模板二/三
4. **旋转数组查找**：需要判断哪半边有序
5. **查找峰值**：根据单调性判断方向

## 注意事项

- `mid = left + (right - left) / 2` 防止整数溢出
- 注意边界条件：`left <= right` vs `left < right`
- 注意返回值：`left` vs `right` vs `mid`
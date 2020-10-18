## 剑指offer 03.数组中重复的数字

### 题目描述

找出数组中重复的数字。

在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。

**示例1**

> 输入：[2, 3, 1, 0, 2, 5, 3]
> 输出：2 或 3 

**限制**

> 2 <= n <= 100000

### 解决方案

#### 1. 使用集合set

将数组中的元素逐一加入到集合set中，若某元素加入失败，说明该元素值重复，则返回该值；否则，返回-1。

```Java
class Solution {    
	public int findRepeatNumber(int[] nums) {
        Set<Integer> set = new HashSet<>();
        for (int num : nums) {
            if (!set.add(num))
                return num;
        }
        return -1;
    }
}
```

#### 2. 排序后查找

将数组排序，如果存在相邻的两个元素相等，则返回该元素的值；否则，返回-1。

```Java
class Solution {
	public int findRepeatNumber(int[] nums) {
		Arrays.sort(nums);
		for (int i = 1; i < nums.length; i++) {
			if (nums[i] == nums[i - 1])
				return nums[i];
		}
		return -1;
	}
}
```

#### 3. 临时数组

将数组的值对应于临时数组temp的下标，临时数组temp的值表示下标在数组中出现的次数，当临时数组temp某项的值大于1时，返回下标；否则，返回-1。

```Java
class Solution {
    public int findRepeatNumber(int[] nums) {
        int length = nums.length;
        int[] temp = new int[length];
        for (int i = 0; i < length; i++) {
            temp[nums[i]]++;
            if (temp[nums[i]] > 1)
                return nums[i];
        }
        return -1;
    }
}
```

#### 4. 数组元素调整位置

遍历数组时，将元素放到值对应的位置上，每次放置时查看该位置是否有正确的元素，如果有，说明值重复，则返回该值；否则，返回-1。

```Java
class Solution {
	public int findRepeatNumber(int[] nums) {
        for (int i = 0; i < nums.length; i++) {
            if (i == nums[i]) {
                continue;
            }
            if (nums[i] == nums[nums[i]]){
                return nums[i];
            }
            int temp = nums[nums[i]];
            nums[nums[i]] = temp;
            nums[i] = temp;
            i--;
        }
        return -1;
    }
}
```








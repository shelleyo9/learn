**快速排序**：分治，类比二叉树的先序遍历，非稳定排序

**时间复杂度**：O(nlogn)

**空间复杂度**：O(logn)，递归需要的栈空间

```c++
/* 快速排序主函数 */
void sort(int[] nums) {
    // 一般要在这用洗牌算法将 nums 数组打乱，
    // 以保证较高的效率，我们暂时省略这个细节
    sort(nums, 0, nums.length - 1);
}

/* 快速排序核心逻辑 */
void sort(int[] nums, int lo, int hi) {
    if (lo >= hi) return;
    // 通过交换元素构建分界点索引 p
    int p = partition(nums, lo, hi);
    // 现在 nums[lo..p-1] 都小于 nums[p]，
    // 且 nums[p+1..hi] 都大于 nums[p]
    sort(nums, lo, p - 1);
    sort(nums, p + 1, hi);
}

int partition(int[] nums, int lo, int hi) {
    if (lo == hi) return lo;
    // 将 nums[lo] 作为默认分界点 pivot
    int pivot = nums[lo];
    // j = hi + 1 因为 while 中会先执行 --
    int i = lo, j = hi + 1;
    while (true) {
        // 保证 nums[lo..i] 都小于 pivot
        while (nums[++i] < pivot) {
            if (i == hi) break;
        }
        // 保证 nums[j..hi] 都大于 pivot
        while (nums[--j] > pivot) {
            if (j == lo) break;
        }
        if (i >= j) break;
        // 如果走到这里，一定有：
        // nums[i] > pivot && nums[j] < pivot
        // 所以需要交换 nums[i] 和 nums[j]，
        // 保证 nums[lo..i] < pivot < nums[j..hi]
        swap(nums, i, j);
    }
    // 将 pivot 值交换到正确的位置
    swap(nums, j, lo);
    // 现在 nums[lo..j-1] < nums[j] < nums[j+1..hi]
    return j;
}

// 交换数组中的两个元素
void swap(int[] nums, int i, int j) {
    int temp = nums[i];
    nums[i] = nums[j];
    nums[j] = temp;
}
```



**快速选择算法**：基于快速排序的变种

时间复杂度：O(nlogn)

空间复杂度：O(logn)，递归需要的栈空间

```c++
int findKthLargest(int[] nums, int k) {
  	int lo=0, hi=nums.size()-1, pivot;
  
    // 注意lo=hi时，也有可能就是最终的pivot
  	while (lo <= hi) {
      	pivot = partition(nums, 0, nums.size()-1);
        if (k == pivot) {
            return nums[spivot];
        } else if (k > pivot) {
            lo = pivot + 1;
        } else {
            hi = pivot -1;
        }
    }
  
    return -1;
}


int partition(vector<int>& nums, int lo, int hi) {
    if (lo == hi) {
        return lo;
    }
    int pivot=lo;
    int i=lo, j=hi+1;

    while (true) {
        while (nums[++i] <= nums[pivot]) {
            if (i == hi) break;
        }
        while (nums[--j] > nums[pivot]) {
            if (j == lo) break;
        }
        if (i >= j) {
            break;
        }
        swap(nums[i], nums[j]);
    }
    swap(nums[pivot], nums[j]);
    return j;
}
```





引申为可以解决数字的自由组合最小值的问题：通过重新定义cmp方法
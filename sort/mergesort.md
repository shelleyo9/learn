**归并排序**：稳定排序，树的后序遍历

**时间复杂度**：

**空间复杂度**：

```c++
void sort(int[] nums) {
    mergeSort(nums, 0, nums.size()-1);
}

void mergeSort(int[] nums, int lo, int hi) {
    if (lo == hi) {
        return;
    }
    int mid = lo + (hi-1o)/2;
    mergeSort(nums, lo, mid);
    mergeSort(nums, mid+1, hi);
    merge(nums, lo, mid, hi);
}

void merge(int[] nums, int lo, int mid, int hi) {
    int i=lo, j=mid+1;
    int[] tmp;
    for (int k=lo; k<=hi; k++) {
        tmp[k] = nums[k];
    }
    
    for (int p=lo; p<=hi; p++) {
        if (i == mid+1) {	// 左边的数组已经扫描完了
            nums[p] = tmp[j++];
        } else if (j == hi+1) {	// 右边的数组已经扫描完了
            nums[p] = tmp[i++];
        } else if (tmp[i] < tmp[j]) {
            nums[p] = tmp[i++];
        } else {
            nums[p] = tmp[j++];
        }
    }
}
```




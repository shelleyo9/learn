快速选择算法：基于快速排序的变种



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

int partition(int[] nums, int lo, int hi) {
  	int i=lo+1, j=hi;	// 注意i从pivot+1开始遍历
  	int pivot = lo;
  
  	while (true) {
        // 注意
        // 1、i的上界是hi的开区间，因为该判断条件是用来判断是否要进行++的操作，如果i已经到了hi了话，不管后面的第二个条件是否满足，都不需要再进行++的操作了
        // 2、前后两个条件的执行顺序放置，防止索引越界
        // 3、如果有重复元素，后面2个while有一个需要考虑到
      	while (i < hi && nums[i] <= pivot) {	
          	i++;
        }
      	while (j > lo && nums[j] > pivot) {	// 注意j的下界是lo
          	j--;
        }
      	if (j <= i) {
          	break;
        }
      	swap(nums, i, j);
    }
  	swap(nums, lo, j);	// 将pivot放到合适的位置，即>所有i遍历的位置，<所有j遍历的位置
  
  	return j;
}

void swap(int[]nums, int i, int j) {
  	int tmp = nums[i];
  	nums[i] = nums[j];
  	nums[j] = tmp;
}
```


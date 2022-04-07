快速选择算法：基于快速排序的变种



```c++
int findKthLargest(int[] nums, int k) {
  	int lo=0, hi=nums.size()-1, pivot;
  
  	while (lo <= hi) {
      	pivot = partition(nums, 0, nums.size()-1);
        if (k == pivot) {
      		return nums[pivot];
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
  	int pivot = nums[lo];
  
  	while (i <= j) {
      	while (i < hi && nums[i] < pivot) {	// 注意i的上界是hi
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


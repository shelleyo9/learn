**堆排序**：

**时间复杂度**：

**空间复杂度**：

```
```





二叉堆：在数组中存储一棵完全二叉树，通过数组索引快速进行树节点的遍历

```c++
class MaxBinaryStack {
    vector<int> num;
    int N=0;	// 为了操作一致，第0个元素作为dummy item
public:
    MaxBinaryStack(int n): num(n) {}

    void print() {
        for (int x:num) {
            cout << x << ",";
        }
        cout << endl;
    }

    bool full() {
        return N==num.size()?true:false;
    }

    int max() {
        return num[1];
    }

    void insert(int k) {
        num[++N] = k;
      	swim(N);
    }

    int delMax() {
        int ret = num[1];
      	swap(1, N);
      	N--;
      	sink(1);
      	return ret;
    }

    void swim(int i) {
        while (i>1 && less(parent(i), i)) {	// 注意截止条件是i还有父节点
            swap(i, parent(i));
            i = parent(i);
        }
    }

    void sink(int i) {
        while (left(i) <= N) {
          	int older = left(i);
          	if (right(i) <= N && less(left(i), right(i))) {	// 注意右节点的边界条件判断
              	older = right(i);
            }
          	if (less(older, i)) {
              	break;
            }
          	swap(i, older);
          	i = older;
        }
    }

    void swap(int a, int b) {
        int tmp = num[a];
        num[a] = num[b];
        num[b] = tmp;
    }

    int less(int a, int b) {
        return true?num[a]<num[b]:false;
    }

    int left(int k) {
        return k*2;
    }

    int right(int k) {
        return k*2+1;
    }

    int parent(int k) {
        return k/2;
    }
};
```


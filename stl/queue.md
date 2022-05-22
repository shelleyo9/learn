### queue：FIFO队列

```c++
#include <iostream>
#include <queue>

int main ()
{
	queue<int> myQueue;
    
    // insert an element
    myQueue.push(77);
    myQueue.push(16);

    // access the "oldest" the "latest" element in queue
    myQueue.front() -= myQueue.back();    // 77-16=61
    
    // remove the first element in queue
    myQueue.pop();
    
	return 0;
}
```



### priority_queue：优先级队列

```c++
#include <iostream>
#include <priority_queue>

static bool cmp(pair<int, vector<int>>& m, pair<int, vector<int>>& n) {
    return m.first > n.first;
}

int main ()
{
    // user-defined sort
	priority_queue<pair<int, vector<int>>, vector<pair<int, vector<int>>>, decltype(&cmp)> pq(cmp);
    
    // insert an element
    pq.push(10);
    pq.push(20);
    pq.push(15);

    // access the highest priority element in queue
    cout << "mypq.top() is now " << pq.top() << '\n';
    
    // remove the highest priority element
    pq.pop();
    
	return 0;
}
```


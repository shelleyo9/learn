

```c++
#include <iostream>
#include <queue>

int main ()
{
	queue<int> myQueue;
    
    // insert an element
    myQueue.push(77);
    myQueue.push(16);

    // access the first element in queue
    myQueue.front() -= myQueue.back();    // 77-16=61
    
    // remove the first element in queue
    myQueue.pop();
    
	return 0;
}
```


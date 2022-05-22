### deque 双端队列

```c++
#include <iostream>
#include <deque>

int main ()
{
    deque<int> mydeque;
    int sum (0);

    // add an element from back
    for (int i=1;i<=10;i++) {
    	mydeque.push_back(i);
    }
        
    // add and element into front
    for (int i=1;i<=10;i++) {
        mydeque.push_front(i);
    }

    while (!mydeque.empty())
    {
        sum += mydeque.front();
        // remove the first element in deque
        mydeque.pop_front();
    }
    
    // remove the last element
    mydeque.pop_back();
	return 0;
}
```


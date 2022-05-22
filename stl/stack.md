### stack：FILO栈

```c++
#include <iostream>
#include <stack>

int main ()
{
    stack<int> mystack;

    // insert an element
    for (int i=0; i<5; ++i) mystack.push(i);

    // access the top element in stack, return a REFERENCE
    mystack.top() -= 5;		// 4-5=-1
    
    std::cout << "Popping out elements...";
    while (!mystack.empty())
    {
        cout << ' ' << mystack.top();
        // remove top element
        mystack.pop();
    }
	return 0;
}
```


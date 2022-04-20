

```c++
#include <iostream>

int main ()
{
	std::vector<int> myVector;
    myVector.push_back (100);
    myVector.push_back (200);
    myVector.push_back (300);
    
    // sort vector
    sort(myVector.begin(), myVector.end());
    
	return 0;
}
```


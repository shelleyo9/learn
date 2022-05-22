### vector 动态数组

```c++
#include <iostream>

int main ()
{
	vector<int> myVector;
    // insert an element
    myVector.push_back (100);
    myVector.push_back (200);
    myVector.push_back (300);
    
    // sort vector
    sort(myVector.begin(), myVector.end());					// increasing order by default
    sort(myVector.begin(), myVector.end(), greater<int>())	// decreasing order
    
    // user-defined sort function
    sort(myVector.begin(), myVector.end(), [](vector<int> &u, vector<int> &v){
        if (u[0]==v[0]) {
            return v[1]<u[1];
        }
        return u[0]<v[0];
    });
    
    // reverse vector
    reverse(myVector.begin(), myVector.end());
    
    // init with other container
    deque<int> dq{3,4};
    cout << vector<int>{dq.begin(), dq.end()}
    
	return 0;
}
```


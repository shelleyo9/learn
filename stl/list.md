### list 双向链表



```c++
#include <iostream>
#include <list>

int main ()
{
    list< pair<int,char> > mylist;

    // construct and insert an element in the end
    mylist.emplace_back(10,'a');
    mylist.emplace_back(20,'b');
    mylist.emplace_back(30,'c');
    
    // insert an element in the end
    mylist.push_back(pair<int, char>{7, 's'});
    
    // insert an element in begining
    mylist.push_front(pair<int, char>{9, 'q'});
    
    // remove element
    mylist.pop_back();
    mylist.pop_front();

    cout << "mylist contains:";
    for (auto& x: mylist)
        cout << " (" << x.first << "," << x.second << ")";

    cout << endl;
    return 0;
}
```


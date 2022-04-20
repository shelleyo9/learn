### unordered_set

```c++
#include <iostream>
#include <unordered_set>

int main ()
{
	unordered_set<string> mySet ( {"red","green","blue"} );
    
    // insert elements
    mySet.insert("gray");
    mySet.insert({"purple","green"});
    
    // erase elements
    mySet.erase("blue");
    
    // traverse set
    for (const string& x: mySet) {
        cout << " " << x;
    }
    
    // count elements with a specific key
    for (auto& x: {"hat","sunglasses","suit","t-shirt"}) {
    	if (mySet.count(x)>0)
    		cout << "myset has " << x << endl;
    	else
    		cout << "myset has no " << x << endl;
    }
	return 0;
}
```



### set

>   Sets are containers that store unique elements following a specific order, which implemented as **binary search trees**

```c++
#include <iostream>
#include <set>

int main ()
{
	std::set<int> myset;
    // insert elements
    for (int i=1; i<10; i++) myset.insert(i*10); // 10 20 30 40 50 60 70 80 90

    // find iterator to lower bound which equivalent or less than arg
    itlow=myset.lower_bound (30);                //       ^
    // find iterator to upper bound which large than arg
    itup=myset.upper_bound (60);                 //                   ^

    // erase [first, last)
    myset.erase(itlow,itup);                     // 10 20 70 80 90

    // traverse with iterator
    for (it=myset.begin(); it!=myset.end(); ++it)
        std::cout << ' ' << *it;

	return 0;
}
```


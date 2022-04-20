### unordered_map

```c++
#include <iostream>
#include <unordered_map>

int main ()
{
    unordered_map<string, int> mymap;

    // add new element
    mymap["Bakery"]=1;  
    mymap["Seafood"]=2;    
    mymap["Produce"]=3;   
    mymap["Bakery"]++; 
    
    // traverse map
    for (auto [k,v]: mymap) {
        cout << "k:" << k << ", v:" << v << endl;
    }
    
    // check if a key exists, count() returns either 0 or 1
    if (mymap.count(Bakery) > 0) {
        cout <<  mymap.coun(Bakery) << mymap["Bakery"];	// 1 2
    }
    
	return 0;
}
```


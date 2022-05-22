### string库中常用的方法

```c++
#include <iostream>
#include <string>

int main ()
{
	string str="We think in generalities, but we live in details.";
    
    // copy a string
    string str1(str);
          
    // substr, 2nd param as LENGTH
    string str2 = str.substr (3,5);     // "think"
    
    // erase, 2nd param as LENGTH
    str.erase(3, 6);	// "We in generalities, but we live in details."
    					// now str[3] = "i"
    str.erase(str.begin());	// 删除第一个char
    
    // find str
    size_t pos = str.find("live");      // position of "live" in str
    
    // insert a char
    str2 += " right";					// "think right"
    str2.push_back(" left");			// "think right left"
    
    // reverse
    reverse(str.begin(). str.end());
    
    // sort
    sort(str.begin(), str.end());
    
	// split string to vector
    string s = "scott>=tiger>=mushroom";
    string delimiter = ">=";
    vector<string> res;

    size_t pos = 0;
    string token;
    while ((pos = s.find(delimiter)) != string::npos) {
        token = s.substr(0, pos);
        res.push_back(token);
        s.erase(0, pos + delimiter.length());
    }
    cout << s << endl;
    
	return 0;
}
```


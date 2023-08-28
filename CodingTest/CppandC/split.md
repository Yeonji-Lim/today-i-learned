# stringstream 이용한 split

```cpp
#include <iostream>
#include <string>
#include <vector>
#include <sstream>

...

vector<string> split(string input, char delimiter) {
    vector<string> answer;
    stringstream ss(input);
    string temp;
 
    while (getline(ss, temp, delimiter)) {
        answer.push_back(temp);
    }
 
    return answer;
}
```
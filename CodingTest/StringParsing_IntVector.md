```c++
vector<int> stringToVector(string str) {
	
	vector<int> retv;
	stringstream sstream(str.substr(1, str.size()-2));
	// #include <sstream>
	string numstr;
	
	while(getline(sstream, numstr, ',')) { //delimiter
		retv.push_back(stoi(numstr));
	}
	
	return retv;

}
```

입력 형식 : `[1,2,3,4,5]`
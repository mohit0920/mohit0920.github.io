# C++

## C++ STL

### Vector

```c++
#include <iostream.h>
#include <vector>

int main() {
  vector<int> A = {11, 2,3, 43};
  cout<<A[1]<<endl;
  return 0;
}
```

### Algorithm

```c++
#include <iostream>
#include <vector>
#include <stdio.h>
#include <algorithm>

using namespace std;
int main() {
    vector<int> A = {11, 2,3, 43};
    cout<<A[1]<<endl; //2
    sort(A.begin(), A.end()); //2, 3 , 11, 43 nlogn time complexity
    bool present = binary_search(A.begin(),A.end(), 3); // true
    present = binary_search(A.begin(), A.end(), 4); //false
    A.push_back(100);
    present = binary_search(A.begin(), A.end(), 100); //true
    A.push_back(100);
    A.push_back(100);
    A.push_back(123);
    // 2,3,11,43,100,100,100,123
    return 0;
}
```

Time complexity of sort will be nlogn. Binary Search Will be general binary search. Push back Can be referred to push operatin in stack.

#### iterator in vector

```c++
		vector<int>::iterator itr = lower_bound(A.begin(), A.end(), 100); // >=
    vector<int> :: iterator itr2 = upper_bound(A.begin(), A.end(), 100); // >
    cout<<*itr<<" "<<*itr2<<endl; // 100 123
    cout<<itr2 - itr<<endl; // 4
```

Iterator Can be considered As a pointer, We can use Asterisk(*) sign with iterator to print value.
Lower_bound gives us location or iterator to the value equal to or just greater than that. 
Upper_bound gives us iterator to just greater than that value.
These can be used where we need to count occurance of a value and found value just greater than that. It has the time complexity of LogN. Because it uses binary search in backend. And It only applies to sorted vector.

#### Sort in reverse order

```c++
bool comperator_fxn(int x, int y) {
    return x > y;
}
sort(A.begin(), A.end(), comperator_fxn); //sort in reverse order
```

We need to pass an extra arguement in the sort function, known as comperator function. 

#### Print a vector

##### Using Iterator

```c++
//Print Using iterator.
    vector<int> :: iterator itr3;
    for (itr3 = A.begin(); itr3 != A.end(); itr3++) {
        cout<<*itr3<<"  ";
    } // 123 100 100 100 43 11 3 2
```

##### Smart Way

```c++
for (int x : A) {
  cout<<x<<"  ";
}
```

It works as for x in A, In python. Here any changes in x will not reflect back to vector. If we want that we can use reference here.

```C++
for(int &x: A) {
  x++;
  cout<<x<<" ";
}
```

Using refernce changes can be refelcted back to the vector.

### Sets

```c++
#include <set>
int main() {
    set<int> S;
    S.insert(1);
    S.insert(2);
    S.insert(3);
    S.insert(-10);
    for (int x : S) {
        cout<<x<<" ";
    } // -10 1 2 3
    return 0;
}
```

logn time complexity for insert maintains the elements in increasing order. No need of sorting insertion of repeated elements is not allowed.

##### Methods for set

```c++
    auto itr = S.find(-10);
    if(itr == S.end()) {
        cout<<"Not Present"<<endl;
    }
    auto itr3 = S.lower_bound(2);
    auto itr4 = S.upper_bound(2);
    auto itr5 = S.upper_bound(3);
    cout<<*itr3<<"  "<<*itr4<<endl; // 2  3
    if(itr5 == S.end()) {
        cout<<"Oops! Can't find something like that"<<endl;
    }

```

In vector lower bound and upper bound are external function means these functions are not bundled in class. But in set  this is not the case. Methods are bounded with in the class. So that we need not to pass set as an argument. We can simply call that method.

### Map

```c++
#include <map>
int main() {
    map <int, int> A;
    A[1] = 100;
    A[2] = -1;
    A[3] = 34;
    A[2213223] = 12211;
    cout<<A[2213223]<<endl; //12211
  return 0;
}
```

Map is like sets it take logn time for searching or other operation. And also for add operation means add(key , value) it takes the logn time because it has to keep it in increasing order means it need to use binary serach for everytime to find the correct positon for it. Similarly for erase a key it takes logn time where n is the length of map.

#### Something meaningful with map

```C++
    string name = "Mohit juneja";
    for ( char c : name) {
        cnt[c]++;
    }
    cout<<cnt['a']<<"  "<<cnt['j']<<"  "<<cnt['z']<<endl; // 1 2 0
```

This is a char count program using map. Everthing takes logn time except creating maps because we are creating from a string so it will take time as of the length of the string. 

### Pair

```c++
    pair<int, int> A = {1,2};
    cout<<A.first<<"  "<<A.second<<endl; // 1 2
```

Header file iostream has the definition for pair so no extra header file is needed for that.

### UnorderedMap

```c
#include <iostream>
#include <map>
#include <unordered_map>
using namespace std;
int main() {
  unordered_map <char, int> U;
  map <char, int> M;
  string name = "Mohit juneja";
  for (char c1: name) M[c1]++; // O(nlogn) N = |s|
  for(char c: name) U[c]++; //O(n)
	return 0;
}
```

here char count using map takes O(nlogn) time. while using unorderd map it takes only n time because add(key, value )and erase(key, value) operation in unordered map jus takes O(1) time. because it uses hashing.


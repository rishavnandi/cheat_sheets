# Recursion

> Recursion - A function which calls itself

#### <span style="color:green">Sum of n natural numbers</span>
```cpp
#include <iostream>

using namespace std;

int sum(int n) {
	if (n == 1) {
		return 1;
	}
	
	return n + sum(n-1);
    
}


int main() {
    
    cout << sum(3);

    return 0;
}
```

#### <span style="color:green">a^b using recursion</span>
```cpp
#include <iostream>

using namespace std;

int power(int a, int b) {
	if (b == 0) {
		return 1;
	}
	
	return a * power(a, b-1);
}

int main() {
    
    cout << power(2,3);

    return 0;
}
```

#### <span style="color:green">Number of paths in matrix</span>
```cpp
#include <iostream>

using namespace std;

int count(int n, int m) {
	if (n == 1 || m == 1) {
		return 1;
	}
	
	return count(n-1,m) + count(n,m-1);
    
}


int main() {
    
    cout << count(4,3) ;

    return 0;
}
```

#### <span style="color:yellow">Josephus problem</span>
```cpp
#include <iostream>

using namespace std;

int jos(int n, int k) {
	if (n == 1) {
		return 0;
	}
	
	return (jos(n-1, k) + k) % n;
    
}


int main() {
    
    cout << jos(4,3);

    return 0;
}
```

#### <span style="color:green">Palindrome string</span>
```cpp
#include <iostream>

using namespace std;

bool isPalin(string s, int l, int r) {
	if (l >= r) {
		return true;
	}

	if (s[l] != s[r]) {
		return false;
	}
	
	return isPalin(s, l+1, r-1);
}

int main() {
		
		string s = "racecar";
		int size = s.length();
		cout << isPalin(s,0,size-1);
}
```

#### <span style="color:yellow">Powerset of string</span>
```cpp
#include <iostream>
using namespace std;

void powerSet(string str, int index = 0,
			string curr = "")
{
	int n = str.length();

	if (index == n) {
		cout << curr << endl;
		return;
	}

	powerSet(str, index + 1, curr + str[index]);
	powerSet(str, index + 1, curr);
}

int main()
{
	string str = "abc";
	powerSet(str);
	return 0;
}
```

#### <span style="color:yellow">Print all permutations of a string</span>
```cpp
#include <iostream>
using namespace std;

void permute(string a, int l, int r)
{
	if (l == r)
		cout<<a<<endl;
	else
	{
		for (int i = l; i <= r; i++)
		{

			swap(a[l], a[i]);

			permute(a, l+1, r);

			swap(a[l], a[i]);
		}
	}
}

int main()
{
	string str = "ABC";
	int n = str.size();
	permute(str, 0, n-1);
	return 0;
}
```


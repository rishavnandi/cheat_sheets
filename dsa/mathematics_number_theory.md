# Mathematic's & Number Theory

#### <span style="color:green">Trailing Zeros In Factorial</span>

```cpp
#include <iostream>

using namespace std;

int main()
{
	
	int res = 0;
	int n = 100;
	for (int i = 5; i <= n; i=i*5){
		res = res + n/i;
	}
	cout << res;
	return 0;
}
```


#### <span style="color:green">Sieve Of Eratosthenes</span>
- For an array n it is only required to traverse through √n to check for prime numbers.

```java
package maths;

import java.util.Arrays;

public class MathemacticsForCP {
    public static void main(String[] args){
        
        boolean isPrime[] = seiveOfEratoSthenes(20);
        for(int i = 0; i <= 20; i++){
            System.out.println(i + " " + isPrime[i]);
        }
        
    }
    
    static boolean[] seiveOfEratoSthenes(int n) {
        
        boolean isPrime[] = new boolean[n+1];
        
        Arrays.fill(isPrime, true);
        
        isPrime[0] = false;
        isPrime[1] = false;
        
        for(int i=2; i*i <= n; i++){
            
            for(int j = 2*i; j <= n; j += i){
                isPrime[j] = false;
            }
        }
        
        return isPrime;
    }
}
```

For an array n it is only required to traverse through √n to check for prime numbers.

#### <span style="color:green">GCD</span>
- gcd(a,b) = gcd(a-b,b) when (a<b)
- gcd(a,b) = gcd(b,a%b) while (a%b ≠ 0)

```java
package maths;

public class MathemacticsForCP {
    
    public static void main(String[] args){
        
        System.out.println(gcd(24,60));
        
    }
    
    static int gcd(int a, int b) {
        
        if(b==0) return a;
        
        return gcd(b,a%b);
    }
}
```

#### <span style="color:green">Modulo Arithmetic's</span>

```java
package maths;

public class MathemacticsForCP {
    
    public static void main(String[] args){
        
        System.out.println(fastPower(24,60));
        
    }
    
    static long fastPower(int a, int b, int n) {
        long res = 1;
        
        while (b > 0) {
            
            if ( (b&1) !=0) {
                res = (res % n * a % n) % n;
            }
            
            a = (a % n * a % n) % n;
            b = b >> 1;
        }
        
        return res;
    }
}
```


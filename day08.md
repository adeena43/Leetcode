```cpp
class Solution {
public:
    double myPow(double x, int n) {
        // Base case: x^0 = 1
        if (n == 0) {
            return 1.0;
        }
        
        // Recursive case: x^n = (x^(n/2))^2 if n is even
        //                x^n = x * (x^(n/2))^2 if n is odd
        double half = myPow(x, n / 2);
        
        // If n is even
        if (n % 2 == 0) {
            return half * half;
        } else { // If n is odd
            if (n > 0) {
                return x * half * half;
            } else {
                return (half * half) / x;
            }
        }
    }
};

```

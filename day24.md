```cpp
class Solution {
public:
    const int MOD = 1e9 + 7;
    using ll = long long;

    ll power(ll x, ll y) {
        ll res = 1;
        x %= MOD;
        while (y) {
            if (y & 1) res = res * x % MOD;
            x = x * x % MOD;
            y >>= 1;
        }
        return res;
    }

    ll modinv(ll x) {
        return power(x, MOD - 2);
    }

    ll comb(int n, int k, vector<ll>& fact, vector<ll>& invFact) {
        if (k < 0 || k > n) return 0;
        return fact[n] * invFact[k] % MOD * invFact[n - k] % MOD;
    }

    int countGoodArrays(int n, int m, int k) {
        int g = n - k;
        if (g <= 0) return 0;

        // Precompute factorials
        vector<ll> fact(n + 1), invFact(n + 1);
        fact[0] = 1;
        for (int i = 1; i <= n; ++i) fact[i] = fact[i - 1] * i % MOD;
        invFact[n] = modinv(fact[n]);
        for (int i = n - 1; i >= 0; --i) invFact[i] = invFact[i + 1] * (i + 1) % MOD;

        ll result = comb(n - 1, k, fact, invFact); // Choose k equal positions
        result = result * m % MOD;                 // First group can be any of m
        result = result * power(m - 1, g - 1) % MOD; // Remaining groups must differ

        return result;
    }
};

```

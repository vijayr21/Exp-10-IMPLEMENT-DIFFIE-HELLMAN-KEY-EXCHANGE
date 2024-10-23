# Exp-10-IMPLEMENT-DIFFIE-HELLMAN-KEY-EXCHANGE

**AIM:**

To implement the Diffie-Hellman Key Exchange algorithm using C language.


**ALGORITHM:**

Step 1:
Both Alice and Bob shares the same public keys g and p.


Step 2:
Alice selects a random public key a.


Step 3:
Alice computes his secret key A as g a mod p.

Step 4:
Then Alice sends A to Bob.


Step 5:
Similarly Bob also selects a public key b and computes his secret key as B and sends the same back to
Alice.

Step 6:
Now both of them compute their common secret key as the other one’s secret key power of a mod
p.


**PROGRAM:**

```
#include <stdio.h>

long long int mod_exp(long long int base, long long int exp, long long int mod) {
long long int result = 1;
while (exp > 0) {
// If exp is odd, mulƟply base with result
if (exp % 2 == 1)
result = (result * base) % mod;

// Now exp must be even, so divide by 2 and square the base
exp = exp >> 1; // equivalent to exp = exp / 2
base = (base * base) % mod;
}
return result;
}

int main() {
long long int P, G, a, b, x, y, ka, kb;

prinƞ("\n********* Diffie-Hellman Key Exchange Algorithm **********\n\n");

// Step 1: Agree on public values P (prime number) and G (primiƟve root)
prinƞ("Enter a prime number P: ");
scanf("%lld", &P); // A prime number P is taken
prinƞ("The value of P: %lld\n", P);

prinƞ("Enter a primiƟve root G for P: ");
scanf("%lld", &G); // A primiƟve root G is taken
prinƞ("The value of G: %lld\n\n", G);

// Step 2: Alice selects a private key a
prinƞ("Enter the private key for Alice (a): ");
scanf("%lld", &a);
x = mod_exp(G, a, P); // Alice's public key x = G^a % P
prinƞ("The public key for Alice (x = G^a mod P): %lld\n", x);

// Step 3: Bob selects a private key b
prinƞ("Enter the private key for Bob (b): ");
scanf("%lld", &b);

y = mod_exp(G, b, P); // Bob's public key y = G^b % P
prinƞ("The public key for Bob (y = G^b mod P): %lld\n\n", y);

// Step 4: Exchange public keys and generate the shared secret key
ka = mod_exp(y, a, P); // Alice computes the shared key ka = y^a % P
kb = mod_exp(x, b, P); // Bob computes the shared key kb = x^b % P

// Step 5: Display the shared secret keys (ka and kb should be equal)
prinƞ("Shared secret key for Alice (ka = y^a mod P): %lld\n", ka);
prinƞ("Shared secret key for Bob (kb = x^b mod P): %lld\n", kb);

if (ka == kb) {
prinƞ("\nDiffie-Hellman Key Exchange successful. Both parƟes share the same key.\n");
} else {
prinƞ("\nError: The keys for Alice and Bob do not match.\n");
}

return 0;
}
```


**Output:**

![image](https://github.com/user-attachments/assets/7e29a3b4-304f-4a26-8265-17ca9a6a0f36)


**Result:**


Thus the Diffie-Hellman key exchange algorithm had been successfully implemented using C.

# Quadratic-primes2

#include <stdio.h>
#include <math.h>

int is_prime(int n) {
    if (n < 2) return 0;
    if (n == 2) return 1;
    if (n % 2 == 0) return 0;
    for (int i = 3; i <= sqrt(n); i += 2) {
        if (n % i == 0) return 0;
    }
    return 1;
}

int main() {
    int n;
    scanf("%d", &n);

    int max_primes = 0, max_a = 0, max_b = 0;
    for (int a = -n; a <= n; a++) {
        for (int b = -n; b <= n; b++) {
            int count = 0;
            for (int i = 0; ; i++) {
                int num = i * i + a * i + b;
                if (!is_prime(num)) break;
                count++;
            }
            if (count > max_primes) {
                max_primes = count;
                max_a = a;
                max_b = b;
            }
        }
    }

    printf("%d %d\n", max_a, max_b);
    return 0;
}

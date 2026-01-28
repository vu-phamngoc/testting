# Tìm phần tử trong dãy 3
```
#include <stdio.h>
#include <stdlib.h>

int so_sanh(const void *a, const void *b) {
    long long v1 = *(long long *)a;
    long long v2 = *(long long *)b;
    if (v1 < v2) return -1;
    if (v1 > v2) return 1;
    return 0;
}

void giai_bai_toan() {
    int n;
    if (scanf("%d", &n) != 1) return;

    long long *a = (long long *)malloc(n * sizeof(long long));
    for (int i = 0; i < n; i++) {
        scanf("%lld", &a[i]);
    }

    qsort(a, n, sizeof(long long), so_sanh);

    int t;
    if (scanf("%d", &t) != 1) {
        free(a);
        return;
    }

    while (t--) {
        long long x;
        scanf("%lld", &x);

        int trai = 0;
        int phai = n - 1;
        long long ket_qua = -1;

        while (trai <= phai) {
            int giua = trai + (phai - trai) / 2;
            if (a[giua] <= x) {
                ket_qua = a[giua];
                trai = giua + 1; 
            } else {
                phai = giua - 1;
            }
        }
        printf("%lld\n", ket_qua);
    }

    free(a);
}

int main() {
    giai_bai_toan();
    return 0;
}

```
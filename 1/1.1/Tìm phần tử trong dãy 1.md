# Tìm phần tử trong dãy 1
```
#include <stdio.h>

void giai_bai_toan() {
    long long n, t;
    
    if (scanf("%lld %lld", &n, &t) != 2) return;

    while (t--) {
        long long x;
        scanf("%lld", &x);

        long long trai = 1;
        long long phai = n;
        long long ket_qua = -1;

        while (trai <= phai) {
            long long giua = trai + (phai - trai) / 2;
            long long gia_tri = giua * giua + 1;

            if (gia_tri >= x) {
                ket_qua = gia_tri;
                phai = giua - 1;
            } else {
                trai = giua + 1;
            }
        }
        
        printf("%lld\n", ket_qua);
    }
}

int main() {
    giai_bai_toan();
    return 0;
}

```
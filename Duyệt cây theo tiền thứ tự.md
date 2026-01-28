# Duyệt cây theo tiền thứ tự
```
#include <stdio.h>

int n;
int cay[100000];
int da_in = 0;

void duyet_tien_thu_tu(int vi_tri) {
    if (vi_tri >= n) return;
    if (cay[vi_tri] == -1) return;

    if (da_in) printf(" ");
    printf("%d", cay[vi_tri]);
    da_in = 1;

    duyet_tien_thu_tu(2 * vi_tri + 1);
    duyet_tien_thu_tu(2 * vi_tri + 2);
}

int main() {
    scanf("%d", &n);

    for (int i = 0; i < n; i++) {
        scanf("%d", &cay[i]);
    }

    duyet_tien_thu_tu(0);
    return 0;
}

```
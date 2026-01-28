# Tìm kiếm
```
#include <stdio.h>

void giai_bai_toan() {
    int n;
    int k;
    
    if (scanf("%d %d", &n, &k) != 2) return;

    int ket_qua = -1;
    for (int i = 1; i <= n; i++) {
        int so_hien_tai;
        scanf("%d", &so_hien_tai);
    
        if (so_hien_tai == k) {
            ket_qua = i;
        }
    }
    
    printf("%d\n", ket_qua);
}

int main() {
    giai_bai_toan();
    return 0;
}

```

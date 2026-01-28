# QUEUE - Truy vấn với hàng đợi 
```
#include <stdio.h>

int main() {
    int so_truy_van;
    scanf("%d", &so_truy_van);

    int hang_doi[100000];
    int dau = 0, cuoi = -1, so_phan_tu = 0;

    for (int i = 0; i < so_truy_van; i++) {
        int loai;
        scanf("%d", &loai);

        if (loai == 1) {
            int gia_tri;
            scanf("%d", &gia_tri);
            hang_doi[++cuoi] = gia_tri;
            so_phan_tu++;
        }
        else if (loai == 2) {
            if (so_phan_tu > 0) {
                dau++;
                so_phan_tu--;
            }
        }
        else if (loai == 3) {
            if (so_phan_tu > 0) {
                printf("%d\n", hang_doi[dau]);
            } else {
                printf("Empty!\n");
            }
        }
    }

    return 0;
}

```
# Queue
```
#include <stdio.h>

int main() {
    int so_hanh_dong;
    scanf("%d", &so_hanh_dong);

    int hang_doi[1000];
    int dau = 0, cuoi = -1, so_phan_tu = 0;

    for (int i = 0; i < so_hanh_dong; i++) {
        int loai;
        scanf("%d", &loai);

        if (loai == 1) {
            if (so_phan_tu > 0) {
                dau++;
                so_phan_tu--;
            }
        } else if (loai == 2) {
            int gia_tri;
            scanf("%d", &gia_tri);
            if (so_phan_tu < 1000) {
                cuoi++;
                hang_doi[cuoi] = gia_tri;
                so_phan_tu++;
            }
        }
    }

    while (so_phan_tu > 0) {
        printf("%d", hang_doi[dau]);
        dau++;
        so_phan_tu--;
        if (so_phan_tu > 0) printf(" ");
    }

    return 0;
}

```
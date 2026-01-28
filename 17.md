# Xoá phần tử cây BST trên mảng
```
#include <stdio.h>

int n, gia_tri_xoa;
int cay[800000];

int tim_trai_nhat_ben_phai(int vi_tri) {
    int hien_tai = 2 * vi_tri + 2;
    while (hien_tai < n && cay[hien_tai] != -1) {
        int trai = 2 * hien_tai + 1;
        if (trai < n && cay[trai] != -1)
            hien_tai = trai;
        else
            break;
    }
    return hien_tai;
}

void xoa_bst(int vi_tri) {
    if (vi_tri >= n) return;
    if (cay[vi_tri] == -1) return;

    if (gia_tri_xoa < cay[vi_tri]) {
        xoa_bst(2 * vi_tri + 1);
    }
    else if (gia_tri_xoa > cay[vi_tri]) {
        xoa_bst(2 * vi_tri + 2);
    }
    else {
        int trai = 2 * vi_tri + 1;
        int phai = 2 * vi_tri + 2;

        int co_trai = (trai < n && cay[trai] != -1);
        int co_phai = (phai < n && cay[phai] != -1);

        if (!co_trai && !co_phai) {
            cay[vi_tri] = -1;
        }
        else if (co_trai && !co_phai) {
            cay[vi_tri] = cay[trai];
            cay[trai] = -1;
        }
        else if (!co_trai && co_phai) {
            cay[vi_tri] = cay[phai];
            cay[phai] = -1;
        }
        else {
            int thay_the = tim_trai_nhat_ben_phai(vi_tri);
            cay[vi_tri] = cay[thay_the];
            cay[thay_the] = -1;
        }
    }
}

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
    scanf("%d %d", &n, &gia_tri_xoa);

    for (int i = 0; i < n; i++) {
        scanf("%d", &cay[i]);
    }

    xoa_bst(0);
    duyet_tien_thu_tu(0);
    return 0;
}

```
# Tìm kiếm trên BST
```
#include <stdio.h>

int n, can_tim;
int cay[800000];

int tim_kiem_bst(int vi_tri) {
    if (vi_tri >= n) return 0;
    if (cay[vi_tri] == -1) return 0;

    if (cay[vi_tri] == can_tim) return 1;
    if (can_tim < cay[vi_tri])
        return tim_kiem_bst(2 * vi_tri + 1);
    else
        return tim_kiem_bst(2 * vi_tri + 2);
}

int main() {
    scanf("%d %d", &n, &can_tim);

    for (int i = 0; i < n; i++) {
        scanf("%d", &cay[i]);
    }

    printf("%d", tim_kiem_bst(0));
    return 0;
}

```
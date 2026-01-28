# Chèn thêm phần tử vào cây BST

```
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int gia_tri;
    struct Node* trai;
    struct Node* phai;
};

struct Node* tao_node(int gia_tri) {
    struct Node* node_moi = (struct Node*)malloc(sizeof(struct Node));
    node_moi->gia_tri = gia_tri;
    node_moi->trai = NULL;
    node_moi->phai = NULL;
    return node_moi;
}

struct Node* chen_bst(struct Node* goc, int gia_tri) {
    if (goc == NULL) {
        return tao_node(gia_tri);
    }

    if (gia_tri < goc->gia_tri) {
        goc->trai = chen_bst(goc->trai, gia_tri);
    } else if (gia_tri > goc->gia_tri) {
        goc->phai = chen_bst(goc->phai, gia_tri);
    }
    return goc;
}

int da_in = 0;

void duyet_tien_thu_tu(struct Node* goc) {
    if (goc == NULL) return;

    if (da_in) printf(" ");
    printf("%d", goc->gia_tri);
    da_in = 1;

    duyet_tien_thu_tu(goc->trai);
    duyet_tien_thu_tu(goc->phai);
}

int main() {
    int n;
    scanf("%d", &n);

    struct Node* goc = NULL;

    for (int i = 0; i < n; i++) {
        int x;
        scanf("%d", &x);
        goc = chen_bst(goc, x);
    }

    duyet_tien_thu_tu(goc);
    return 0;
}

```
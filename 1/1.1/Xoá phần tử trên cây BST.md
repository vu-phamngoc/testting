# Xoá phần tử trên cây BST
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
    if (goc == NULL) return tao_node(gia_tri);

    if (gia_tri < goc->gia_tri)
        goc->trai = chen_bst(goc->trai, gia_tri);
    else if (gia_tri > goc->gia_tri)
        goc->phai = chen_bst(goc->phai, gia_tri);

    return goc;
}

struct Node* tim_trai_nhat(struct Node* goc) {
    while (goc->trai != NULL)
        goc = goc->trai;
    return goc;
}

struct Node* xoa_bst(struct Node* goc, int gia_tri_xoa) {
    if (goc == NULL) return NULL;

    if (gia_tri_xoa < goc->gia_tri) {
        goc->trai = xoa_bst(goc->trai, gia_tri_xoa);
    }
    else if (gia_tri_xoa > goc->gia_tri) {
        goc->phai = xoa_bst(goc->phai, gia_tri_xoa);
    }
    else {
        if (goc->trai == NULL) {
            struct Node* temp = goc->phai;
            free(goc);
            return temp;
        }
        else if (goc->phai == NULL) {
            struct Node* temp = goc->trai;
            free(goc);
            return temp;
        }
        else {
            struct Node* thay_the = tim_trai_nhat(goc->phai);
            goc->gia_tri = thay_the->gia_tri;
            goc->phai = xoa_bst(goc->phai, thay_the->gia_tri);
        }
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
    int n, k;
    scanf("%d %d", &n, &k);

    struct Node* goc = NULL;

    for (int i = 0; i < n; i++) {
        int x;
        scanf("%d", &x);
        goc = chen_bst(goc, x);
    }

    goc = xoa_bst(goc, k);
    duyet_tien_thu_tu(goc);

    return 0;
}
```


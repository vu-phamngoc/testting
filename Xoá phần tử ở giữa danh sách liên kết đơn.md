# Xoá phần tử ở giữa danh sách liên kết đơn
```
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

struct Node* addToFront(struct Node* head, int value) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = value;
    newNode->next = head;
    return newNode;
}

struct Node* deleteAfter(struct Node* head, int b) {
    struct Node* current = head;
    while (current != NULL) {
        if (current->data == b && current->next != NULL) {
            struct Node* temp = current->next;
            current->next = temp->next;
            free(temp);
            return head;
        }
        current = current->next;
    }
    return head;
}

void printList(struct Node* head) {
    struct Node* current = head;
    while (current != NULL) {
        printf("%d", current->data);
        if (current->next != NULL) printf(" ");
        current = current->next;
    }
}

int main() {
    int n, m;
    scanf("%d %d", &n, &m);

    struct Node* head = NULL;

    for (int i = 0; i < n; i++) {
        int value;
        scanf("%d", &value);
        head = addToFront(head, value);
    }

    for (int i = 0; i < m; i++) {
        int b;
        scanf("%d", &b);
        head = deleteAfter(head, b);
    }

    printList(head);
    return 0;
}

```
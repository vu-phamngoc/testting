# Thêm phần tử vào giữa danh sách liên kết đơn
```
#include <stdio.h>
#include <stdlib.h>
struct Node {
    int data;
    struct Node* next;
};

struct Node* addAfterOrFront(struct Node* head, int a, int b) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = a;
    newNode->next = NULL;

    if (head == NULL) {
        newNode->next = head;
        return newNode;
    }

    struct Node* current = head;
    while (current != NULL) {
        if (current->data == b) {
            newNode->next = current->next;
            current->next = newNode;
            return head;
        }
        current = current->next;
    }

    newNode->next = head;
    return newNode;
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
    int n;
    scanf("%d", &n);
    struct Node* head = NULL;
    for (int i = 0; i < n; i++) {
        int a, b;
        scanf("%d %d", &a, &b);
        head = addAfterOrFront(head, a, b);
    }
    printList(head);
    return 0;
}

```
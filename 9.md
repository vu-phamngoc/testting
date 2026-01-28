# Xoá phần tử ở đầu danh sách liên kết vòng 
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

    if (head == NULL) {
        newNode->next = newNode;
        return newNode;
    }

    struct Node* temp = head;
    while (temp->next != head) {
        temp = temp->next;
    }

    newNode->next = head;
    temp->next = newNode;
    return newNode;
}

struct Node* deleteFront(struct Node* head) {
    if (head == NULL) return NULL;

    if (head->next == head) {
        free(head);
        return NULL;
    }

    struct Node* temp = head;
    struct Node* last = head;
    while (last->next != head) {
        last = last->next;
    }

    head = head->next;
    last->next = head;
    free(temp);
    return head;
}

void printCircularList(struct Node* head, int n) {
    if (head == NULL) return;

    struct Node* current = head;
    for (int i = 0; i < n; i++) {
        printf("%d", current->data);
        current = current->next;
        if (i < n - 1) printf(" ");
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
        head = deleteFront(head);
    }
    printCircularList(head, n - m);
    return 0;
}

```
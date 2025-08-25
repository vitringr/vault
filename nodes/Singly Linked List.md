---
context:
  - "[[Linked List]]"
  - "[[Data Structure]]"
---

# Singly Linked List

[[Linked List]] where each node points only to the next node.

---

Considered the default linked list structure.

**Unidirectional**: Traversal is unidirectional: `head → tail`

## Implementation

#wip

```c
/*

TODO:
- insert/delete at index
- get node at index
- get list length
- check if list is empty

*/

#include <stdio.h>
#include <stdlib.h>

typedef struct Node Node;
Node *createNode(int data);
void push(Node **head, int data);
void pop(Node **head);
void shift(Node **head);
void unshift(Node **head, int data);
Node *getTail(Node *head);
Node *find(Node *head, int value);
void clearList(Node **head);
void printNode(Node *node);
void printList(Node *head);

struct Node {
  int data;
  struct Node *next;
};

Node *createNode(int data) {
  Node *newNode = (Node *)malloc(sizeof(Node));
  if (newNode == NULL) {
    printf("ERROR: Memory allocation failed!");
    exit(1);
  }

  newNode->data = data;
  newNode->next = NULL;
  return newNode;
}

void push(Node **head, int data) {
  if (*head == NULL) {
    *head = createNode(data);
    return;
  }

  Node *tail = getTail(*head);
  tail->next = createNode(data);
}

void pop(Node **head) {
  if (*head == NULL)
    return;

  if ((*head)->next == NULL) {
    free(*head);
    *head = NULL;
    return;
  }

  Node *current = *head;
  Node *prev = current;

  while (current->next != NULL) {
    prev = current;
    current = current->next;
  };

  prev->next = NULL;
  free(current);
}

void shift(Node **head) {
  if (*head == NULL)
    return;

  if ((*head)->next == NULL) {
    free(*head);
    *head = NULL;
    return;
  }

  Node *next = (*head)->next;
  free(*head);
  *head = next;
}

void unshift(Node **head, int data) {
  if (*head == NULL) {
    *head = createNode(data);
    return;
  }

  Node *newNode = createNode(data);
  newNode->next = *head;

  *head = newNode;
}

Node *getTail(Node *head) {
  if (head == NULL)
    return NULL;

  Node *current = head;
  while (current->next != NULL)
    current = current->next;

  return current;
}

Node *find(Node *head, int value) {
  Node *current = head;
  while (current != NULL) {
    if (current->data == value)
      return current;
    current = current->next;
  }

  return NULL;
}

void printNode(Node *node) {
  if (node == NULL) {
    printf("Node is NULL!\n");
    return;
  }

  printf("{ address: %p, data: %d, next: %p }\n", &(*node), node->data,
         node->next);
}

void printList(Node *head) {
  if (head == NULL) {
    printf("Head is NULL!\n");
    return;
  }

  Node *current = head;
  while (current != NULL) {
    printNode(current);
    current = current->next;
  }
}

void clearList(Node **head) {
  Node *current = *head;
  Node *temp;

  while (current != NULL) {
    temp = current;
    current = current->next;
    free(temp);
  }

  *head = NULL;
}

int main() {
  Node *head = NULL;
  push(&head, 42);
  push(&head, 43);
  push(&head, 44);
  unshift(&head, 30);
  unshift(&head, 20);

  printList(head);

  clearList(&head);
  return 0;
}
```

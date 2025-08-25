---
context:
  - "[[DSAP]]"
---

# Singly Linked List (DSAP)

Implement a full [[Singly Linked List]].

---

```c
#include <stdio.h>
#include <stdlib.h>

typedef struct Node Node;
Node *createNode(int data);
Node *find(Node *head, int value);
Node *getTail(Node *head);
Node *getIndex(Node *head, int index);
int getLength(Node *head);
void push(Node **head, int data);
void pop(Node **head);
void shift(Node **head);
void unshift(Node **head, int data);
void insertAt(Node **head, int index, int data);
void deleteAt(Node **head, int index);
void printNode(Node *node);
void printList(Node *head);
void clearList(Node **head);

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

Node *find(Node *head, int value) {
  Node *current = head;
  while (current != NULL) {
    if (current->data == value)
      return current;
    current = current->next;
  }

  return NULL;
}

Node *getTail(Node *head) {
  if (head == NULL)
    return NULL;

  Node *current = head;
  while (current->next != NULL)
    current = current->next;

  return current;
}

Node *getIndex(Node *head, int index) {
  if (head == NULL)
    return NULL;
  if (index == 0)
    return head;
  if (index < 0)
    return NULL;

  Node *current = head;
  for (int i = 0; i < index; i++) {
    current = current->next;
    if (current == NULL)
      return NULL;
  }

  return current;
}

int getLength(Node *head) {
  if (head == NULL)
    return 0;

  int count = 0;
  Node *current = head;
  while (current != NULL) {
    current = current->next;
    count++;
  }

  return count;
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

void insertAt(Node **head, int index, int data) {
  if (index < 0)
    return;

  if (index == 0) {
    unshift(head, data);
    return;
  }

  if (*head == NULL)
    return;

  Node *before = getIndex(*head, index - 1);
  if (before == NULL)
    return;

  Node *newNode = createNode(data);
  newNode->next = before->next;
  before->next = newNode;
}

void deleteAt(Node **head, int index) {
  if (index < 0)
    return;

  if (index == 0) {
    shift(head);
    return;
  }

  Node *before = getIndex(*head, index - 1);
  if (before == NULL || before->next == NULL)
    return;

  Node *current = before->next;
  before->next = current->next;

  free(current);
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
  push(&head, 40);
  push(&head, 41);
  push(&head, 42);
  push(&head, 43);

  printList(head);

  clearList(&head);
  return 0;
}
```

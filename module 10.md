EXP NO:16 C PROGRAM TO SEARCH A GIVEN ELEMENT IN THE GIVEN LINKED LIST.
Aim:
To write a C program to search a given element in the given linked list.

Algorithm:
1.	Define the structure for a node in a linked list.
2.	Define the search function to find a specific character in the linked list.
3.	Initialize the head of the linked list as needed.
4.	Call the search function and perform other linked list operations as needed.
 
Program:
```
#include <stdio.h>
#include <stdlib.h>

struct Node {
    char data;
    struct Node* next;
};

struct Node* createNode(char data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->next = NULL;
    return newNode;
}

int search(struct Node* head, char key) {
    struct Node* current = head;
    while (current != NULL) {
        if (current->data == key) return 1;
        current = current->next;
    }
    return 0;
}

int main() {
    struct Node* head = createNode('A');
    head->next = createNode('B');
    head->next->next = createNode('C');
    head->next->next->next = createNode('D');

    char key1 = 'C';
    char key2 = 'X';

    if (search(head, key1))
        printf("%c found in the linked list.\n", key1);
    else
        printf("%c not found in the linked list.\n", key1);

    if (search(head, key2))
        printf("%c found in the linked list.\n", key2);
    else
        printf("%c not found in the linked list.\n", key2);

    return 0;
}
```
Output:
Output 1:
C found in the linked list.
Output 2:
X not found in the linked list.

Result:
Thus, the program to search a given element in the given linked list is verified successfully.


 
EXP NO:17  PROGRAM TO INSERT A NODE IN A LINKED LIST.
Aim:
To write a C program to insert a node in a linked list.
Algorithm:
1.	Define the structure for a node in a linked list
2.	Define the insert function to insert a new node with character data at the end of the linked list.
3.	Initialize the head of the linked list as needed.
4.	Call the insert function and perform other linked list operations as needed.
 
Program:
```
#include <stdio.h>
#include <stdlib.h>

struct Node {
    char data;
    struct Node* next;
};

void insert(struct Node** head, char data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->next = NULL;

    if (*head == NULL) {
        *head = newNode;
        return;
    }

    struct Node* temp = *head;
    while (temp->next != NULL)
        temp = temp->next;

    temp->next = newNode;
}

void printList(struct Node* head) {
    struct Node* temp = head;
    while (temp != NULL) {
        printf("%c ", temp->data);
        temp = temp->next;
    }
    printf("\n");
}

int main() {
    struct Node* head = NULL;

    insert(&head, 'A');
    insert(&head, 'B');
    insert(&head, 'C');

    printf("Linked list after 3 insertions:\n");
    printList(head);

    insert(&head, 'D');
    insert(&head, 'E');

    printf("Linked list after adding 2 more nodes:\n");
    printList(head);

    return 0;
}
```

Output:
Output 1:
Linked list after 3 insertions:
A B C 
Output 2:
Linked list after adding 2 more nodes:
A B C D E 
 
Result:
Thus, the program to insert a node in a linked list is verified successfully.


 
EXP NO:18 C PROGRAM TO TRAVERSE A DOUBLY LINKED LIST
Aim:
To write a C program to traverse a doubly linked list.

Algorithm:
1.	Initialize a temporary pointer (temp) to the head of the list.
2.	Use a while loop to traverse the list until the end (temp == NULL) is reached.
3.	Inside the loop, print the data of the current node.
4.	Move to the next node by updating the temp pointer to point to the next node (temp = temp->next).
 
Program:
```
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* prev;
    struct Node* next;
};

void traverse(struct Node* head) {
    struct Node* temp = head;
    printf("Doubly linked list elements:\n");
    while (temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->next;
    }
    printf("\n");
}

struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->prev = NULL;
    newNode->next = NULL;
    return newNode;
}

int main() {
    // Creating nodes
    struct Node* head = createNode(10);
    struct Node* second = createNode(20);
    struct Node* third = createNode(30);

    // Linking nodes
    head->next = second;
    second->prev = head;
    second->next = third;
    third->prev = second;

    // Output 1
    traverse(head);

    // Adding one more node
    struct Node* fourth = createNode(40);
    third->next = fourth;
    fourth->prev = third;

    // Output 2
    traverse(head);

    return 0;
}
```

Output:
Output 1:
Doubly linked list elements:
10 20 30 
Output 2:
Doubly linked list elements:
10 20 30 40 

Result:
Thus, the program to traverse a doubly linked list is verified successfully. 



EXP NO:19 C PROGRAM TO INSERT AN ELEMENT IN DOUBLY LINKED LIST
Aim:
To write a C program to insert an element in doubly linked list

Algorithm:
1.	Create a new node (newNode) and allocate memory for it.
2.	Set the data of the new node to the provided value.
3.	If the list is empty, set the new node as the head.
4.	If the list is not empty, traverse the list to find the last node.
5.	Set the new node's prev pointer to the last node and update the last node's next pointer to the new node.
 
Program:
```
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* prev;
    struct Node* next;
};

void insertEnd(struct Node** head_ref, int new_data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = new_data;
    newNode->next = NULL;

    if (*head_ref == NULL) {
        newNode->prev = NULL;
        *head_ref = newNode;
        return;
    }

    struct Node* temp = *head_ref;
    while (temp->next != NULL) {
        temp = temp->next;
    }

    temp->next = newNode;
    newNode->prev = temp;
}

void traverse(struct Node* head) {
    struct Node* temp = head;
    printf("Doubly linked list elements:\n");
    while (temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->next;
    }
    printf("\n");
}

int main() {
    struct Node* head = NULL;

    // Output 1
    insertEnd(&head, 10);
    insertEnd(&head, 20);
    insertEnd(&head, 30);
    traverse(head);

    // Output 2: Inserting one more element
    insertEnd(&head, 40);
    traverse(head);

    return 0;
}
```

Output:
Output 1:
Doubly linked list elements:
10 20 30 
Output 2:
Doubly linked list elements:
10 20 30 40 

Result:
Thus, the program to insert an element in doubly linked list is verified successfully.




EXP NO:20 C FUNCTION TO DELETE A GIVEN ELEMENT IN THE GIVEN LINKED LIST

Aim:
To write a C function that deletes a given element from a linked list.

Algorithm:
1.	Check if the Linked List is Empty:
o	If the head of the linked list is NULL, print a message indicating the list is empty and exit the function.
2.	Traverse the Linked List:
o	Start from the head node and iterate through the list to find the node that contains the given element (data).
3.	Handle Deletion of the First Node:
o	If the element to be deleted is found in the head node:
	Update the head of the linked list to point to the next node (i.e., head = head->next).
	Free the memory allocated to the node to be deleted.
	Exit the function.
4.	Traverse and Delete from the Middle or End:
o	If the element is not in the head node, continue traversing the list by checking each node’s next pointer.
o	When the node with the element is found, update the previous node’s next pointer to point to the next node of the node to be deleted (prev->next = current->next).
o	Free the memory allocated to the node to be deleted.
5.	Handle the Case when the Element is Not Found:
o	If the element is not found in any node, print a message indicating the element is not present in the list.
6.	End the Function.


Program:
```
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

void insertEnd(struct Node** head, int value) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = value;
    newNode->next = NULL;

    if (*head == NULL) {
        *head = newNode;
        return;
    }

    struct Node* temp = *head;
    while (temp->next != NULL)
        temp = temp->next;

    temp->next = newNode;
}

void deleteElement(struct Node** head, int key) {
    struct Node* temp = *head;
    struct Node* prev = NULL;

    if (temp == NULL) {
        printf("List is empty.\n");
        return;
    }

    if (temp != NULL && temp->data == key) {
        *head = temp->next;
        free(temp);
        printf("Element %d deleted.\n", key);
        return;
    }

    while (temp != NULL && temp->data != key) {
        prev = temp;
        temp = temp->next;
    }

    if (temp == NULL) {
        printf("Element %d not found in the list.\n", key);
        return;
    }

    prev->next = temp->next;
    free(temp);
    printf("Element %d deleted.\n", key);
}

void display(struct Node* head) {
    struct Node* temp = head;
    printf("List: ");
    while (temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->next;
    }
    printf("\n");
}

int main() {
    struct Node* head = NULL;
    insertEnd(&head, 10);
    insertEnd(&head, 20);
    insertEnd(&head, 30);
    display(head);
    deleteElement(&head, 20);
    display(head);
    deleteElement(&head, 40); // Not in list
    deleteElement(&head, 10); // Delete first node
    display(head);

    return 0;
}

```

Output:
Output 1:
List: 10 20 30 
Element 20 deleted.
List: 10 30 
Output 2:
Element 40 not found in the list.
Element 10 deleted.
List: 30 


Result:
Thus, the function that deletes a given element from a linked list is verified successfully.






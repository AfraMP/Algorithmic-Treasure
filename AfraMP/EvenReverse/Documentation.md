# DOCUMENTATION
## Even Reverse<br>
<a><img src="https://img.shields.io/badge/-Amazon-blue" height="25">&nbsp;&nbsp;
<img src= "https://img.shields.io/badge/-Interview Bit-navy" height="25">
&nbsp;&nbsp;<img src= "https://img.shields.io/badge/-Python-red" height="25">
&nbsp;&nbsp;<img src= "https://img.shields.io/badge/-CPP-red" height="25"></a><br>
<br>
**Problem Statement**<br>
<br>
Given a linked list A , reverse the order of all nodes at even positions.<br>
Return the head of the new linked list.
```
Example 1

Input : 1 3 5 7 9 2 4 6 8 0
Output : 1 0 5 6 9 2 4 7 8 3
```
```
Example 2

Input : 1 2 7 6
Output : 1 6 7 2
```
#### Solution<br>
#### Method 1 <br>
The input consists of a set of elements stored in the form of a linked list. 
The output of the above problem is achieved using a single linked list.
Firstly a class called Node is created, which represents a node of linked list with 
variables next that acts as a pointer and data used to store elements in it.
When the method named newNode is called an object of type Node is being returned and 
the element which is passed as a parameter to the newNode is stored in variable data.
Reverse is a method that takes 2 parameters head and prev represents the beginning 
and previous node of the linked list.
* If head is none then nothing is returned
* If head is not none then it loops through the entire linked list until the current node is not none and 
position of the current node is not even and swap the data between the previous node, current node and the next node.
Once the elements are reversed then head pointer is changed, this is repeated until the end of linked list.
The solve method is used to arrange the reversed elements in a particular order.
###### Python code
```
# Creating A Node
class Node:  
    def __init__(self, next = None, data = None):  
        self.next = next
        self.data = data  
  
# Function to create a new node 
def newNode( d): 
  
    newnode = Node() 
    newnode.data = d 
    newnode.next = None
    return newnode 
  
# Function to even reverse the given input
def reverse(head, prev): 
  
    # Base case 
    if (head == None): 
        return None
  
    temp = None
    curr = None
    curr = head 
  
    # Reversing nodes until curr node's value 
    # turn odd or Linked list is fully traversed 
    while (curr != None and curr.data % 2 == 0) : 
        temp = curr.next
        curr.next = prev 
        prev = curr 
        curr = temp 
  
    # If elements were reversed then head pointer needs to be changed 
    if (curr != head) : 
        head.next = curr 
  
        # Recur for the remaining linked list 
        curr = reverse(curr, None) 
        return prev 
      
    # Simply iterate over the odd value nodes 
    else: 
      
        head.next = reverse(head.next, head) 
        return head 
      
# Function to print the contents of the linked list 
def printLinkedList(head): 
  
    while (head != None): 
      
        print(head.data ,end= " ") 
        head = head.next
def solve(head):
    odd=[]
    even=[]
    i=0
    while(head):
        if i%2==0:
            odd.append(head.data)
        else:
            even.append(head.data)
        head=head.next
        i+=1
        l=[]
    even=even[::-1]
    for i in range(len(odd)+len(even)):
        if i%2==0:
            l.append(odd[0])
            odd=odd[1:]
        else:
            l.append(even[0])
            even=even[1:]
    head=newNode(l[0])
    curr=head
    for i in range(1,len(l)):
        curr.next=newNode(l[i])
        curr=curr.next
    return head

arr = list(map(int, input().split()))
n = len(arr) 
      
head = None
p = Node() 
      
i = 0
# Constructing linked list 
while ( i < n ): 
      
    if (head == None): 
          
        p = newNode(arr[i]) 
        head = p 
    else: 
        p.next = newNode(arr[i]) 
        p = p.next
    i = i + 1; 
  
# Update linked list
head = solve(head) 
  
# Printing the even reversed linked list 
printLinkedList(head) 
```
#### Method 2 <br>
###### CPP code
```
#include <iostream>
#include <vector>

using namespace std;


struct Node{
	int data;
	Node* link;
};
int i=1;
Node *start=NULL;

// method to print 
void printList(Node* node)
{
	while(node != NULL){
		printf("%d ", node->data);
		node = node->link;
	}
	printf("\n");
}
void dfs(Node *A,int j)
{
   if(i>j||!start||!A) return;
   if(A->link) A=A->link;
   else return ;
   if(A->link) A=A->link;
   else return ;
   dfs(A,j+2);
   if(start&&i<j+2)
   {
       swap(A->data,start->data);
       i+=2;
       if(start)start=start->link;
       if(start)start=start->link;
       return ;
   }
   return ;
}

Node* evenReverse(Node* A) {
    if(A)
    start=A->link;
    else
    return A;
    i=2;
    dfs(A->link,2);
    return A;
}

// method to insert elements
void insertElement(Node** head_Pointer, int data_elem)
{
	Node* elem = (struct Node*)malloc(sizeof(struct Node));
	elem->data = data_elem;
	elem->link = *head_Pointer;
	*head_Pointer = elem;
}

int main()
{
	int n, i;
	int a[10];
	Node* head = NULL;
	printf("Enter the number of elements:\n");
	scanf("%d", &n);
	printf("Enter the elements\n");
	for(i = 0; i < n; i++){
		scanf("%d", &a[i]);
	}
	for(i = n-1; i >= 0; i--)
		insertElement(&head, a[i]);
	printf("Linked list before even reverse");
	printList(head);
	evenReverse(head);
	printf("Linked list after even reverse");
	printList(head);
	return 0;
}
```
#### Complexity Analysis of Even  Reverse :<br>
* Time Complexity: O(n)<br>
* Space Complexity: O(1)
# DOCUMENTATION
## Swap List Nodes In Pairs<br>
<a><img src= "https://img.shields.io/badge/-Microsoft-orange" height="25">&nbsp;&nbsp;
<img src="https://img.shields.io/badge/-Amazon-blue" height="25">&nbsp;&nbsp;
<img src= "https://img.shields.io/badge/-Interview Bit-navy" height="25">
&nbsp;&nbsp;<img src= "https://img.shields.io/badge/-Python-red" height="25"></a>

 **Problem Statement**<br><br />
Given a linked list, swap every two adjacent nodes and return its head.
```
Example 1
 
Input  : 1 2 3 4
Output : 2 1 4 3
```
```
Example 2

Input  : 2 4 6 3 1 5
Output : 4 2 3 6 5 1
```
#### Solution<br>
Input contains a list of elements in a linked list and the expected output can be achieved by using a single linked list.
Firstly a class called Node is created, which represents a node of linked list with 
variables next that acts as a pointer and data used to store elements in it.
The method rearrange is used to swap the adjacent nodes in following manner :
* If head or node pointed by head is none return head. 
* If head or node pointed by head is none set current node as head and consider 2 nodes at a time and swap their links

###### Python code
```
# A linked list node
class Node:
    def __init__(self, data=None, next=None):
        self.data = data
        self.next = next
 
 
# Helper function to print given linked list
def printList(head):
 
    ptr = head
    while ptr:
        print(ptr.data, end=" ")
        ptr = ptr.next
 
    print("")
 
 
# Function to pairwise swap adjacent nodes of a linked list
def rearrange(head):
 
    # if list is empty or contains just one node
    if head is None or head.next is None:
        return head
 
    curr = head
    prev = None
 
    # consider two nodes at a time and swap their links
    while curr and curr.next:
 
        temp = curr.next
        curr.next = temp.next
        temp.next = curr
 
        if prev is None:
            head = temp
        else:
            prev.next = temp
 
        prev = curr
        curr = curr.next
 
    return head
 
 
if __name__ == '__main__':
 
    head = None
    a = list(map(int, input().split()))
    for i in reversed(a):
        head = Node(i, head)
    head = rearrange(head)
    printList(head)
 
```
#### Complexity Analysis :<br>
* Time Complexity : O(n)<br>
* Space Complexity  : O(n)

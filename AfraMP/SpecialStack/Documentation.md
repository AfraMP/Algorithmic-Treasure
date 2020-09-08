# DOCUMENTATION
## Special Stack<br>
<a><img src="https://img.shields.io/badge/-Amazon-blue" height="25">&nbsp;&nbsp;
<img src="https://img.shields.io/badge/-Goldman Sachs-blue" height="25">&nbsp;&nbsp;
<img src="https://img.shields.io/badge/-Paytm-blue" height="25">&nbsp;&nbsp;
<img src= "https://img.shields.io/badge/-Interview Bit-navy" height="25">&nbsp;&nbsp;
<img src= "https://img.shields.io/badge/-Python-red" height="25"></a><br>

**Problem Statement**<br><br />
Design a data-structure SpecialStack that supports all the stack operations like push(), 
pop(), isEmpty(), isFull() and an additional operation getMin() which should return minimum 
element from the SpecialStack. 
```
Example 1

Enter the size of stack - 5
23 67 657 80 70
Enter your choice:
1.push 2.pop  3.isFull  4.isEmpty  5.minElem  6.exit
1
>>> Stack Full
1.push 2.pop  3.isFull  4.isEmpty  5.minElem  6.exit
3
>>> True
1.push 2.pop  3.isFull  4.isEmpty  5.minElem  6.exit
2
>>> Popped element is 70
1.push 2.pop  3.isFull  4.isEmpty  5.minElem  6.exit
5
>>> 23
1.push 2.pop  3.isFull  4.isEmpty  5.minElem  6.exit
6
```
```
Example 2

Enter the size of stack - 2
43 98
Enter your choice:
1.push 2.pop  3.isFull  4.isEmpty  5.minElem  6.exit
2
>>> Popped Element is 98
1.push 2.pop  3.isFull  4.isEmpty  5.minElem  6.exit
2
>>> Popped Element is 43
1.push 2.pop  3.isFull  4.isEmpty  5.minElem  6.exit
24
>>> True
1.push 2.pop  3.isFull  4.isEmpty  5.minElem  6.exit
5
>>> 2
Stack empty
1.push 2.pop  3.isFull  4.isEmpty  5.minElem  6.exit
6
```
#### Solution<br>
A stack is a linear data structure that stores items in a Last-In First-Out (LIFO) 
or First-In Last-Out (FILO) manner. Input are N, a representing size of stack and input array
* Push method - if N greater than length of the input array elements then push the input element into the stack
                if N is lesser than number of elements then it leads to Stack overflow
* Pop method  - If length of input array is zero it indicates that the stack is empty
                If length of input array is not zero then it returns pop() method.
* isFull      - If length of input array is equal to N then returns True
* isEmpty     - If length of input array is none then it returns True
* MinElem     - This method returns the smallest element by using built-in method min() 
                
###### Python code
```
class SpecialStack:

    def __init__(self, n):
        self.n = n
    
    # function should append an element on to the stack
    def push(self, arr):
        if len(arr) < self.n:
            ele = input("Enter element to push")
            arr.append(ele)
        else:
            print("Stack overflow")
    
    # Function to pop an element from stack
    def pop(self, arr):
        if(len(arr)==0):
            print("Stack empty")
    
        return arr.pop()
    
    # Function to check if stack is full
    def isFull(self, arr):
        if (len(arr) == self.n):
            return True
        return False
    
    # Function to check if stack is empty
    def isEmpty(self, arr):
        if arr == None:
            return True
        else:
            return False
    
    # function should return minimum element from the stack
    def getMin(self, arr):
        if(len(arr)==0):
            return int("-1")
        return min(arr)
a = []
N = int(input("Enter size of stack - "))
for _ in range(0, N):
    a.append(input())
s = SpecialStack(N)
print("Enter your choice")
b = ''
while b != '6':
    b = input("1. push   2. pop   3. isFull   4. isEmpty   5. getMin elem   6. exit")
    if b == '1':
        s.push(a)
    elif b == '2':
        print("Popped element is " + s.pop(a))
    elif b == '3':
        print(s.isFull(a))
    elif b == '4':
        print(s.isEmpty(a))
    elif b == '5':
        print(s.getMin(a))

```
#### Complexity Analysis :<br />
* Time Complexity : O(1)<br />
* Space Complexity : O(1)

        
        

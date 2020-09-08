# DOCUMENTATION
## Find Missing And Repeating<br>
<a><img src="https://img.shields.io/badge/-Amazon-blue" height="25">&nbsp;&nbsp;
<img src= "https://img.shields.io/badge/-Geeks For Geeks-navy" height="25">&nbsp;&nbsp;
<img src= "https://img.shields.io/badge/-Goldman Sachs-red" height="25">&nbsp;&nbsp;
<img src= "https://img.shields.io/badge/-Samsung-navy" height="25">&nbsp;&nbsp;
<img src="https://img.shields.io/badge/-Python-blue" height="25"></a><br><br />
**Problem Statement**<br><br />
 Given an unsorted array of size N of positive integers. One number 'A' from set {1, 2, …N} 
is missing and one number 'B' occurs twice in array. Find these two numbers.
 
```
Example 1

Input : 2
        2
        2 2
        3
        1 3 3
Output : 2 1
         3 2
```
```
Example 2

Input : 3
        2
        1 1
        3
        2 2 1
Output : 1 2
         2 3
```
#### Solution<br>

#### Method 1:<br>

In the above program we are supposed to find the duplicate number and the number
 missing the the range of N with a time complexity not exceeding O(n). <br>
The inputs involved in the above problem are T that represents the testcases, N 
the total number of elements in array, Arr is the list of elements. Initialize 
another a new variable with list of size Arr containing 0's. The problem is solved 
by looping through each elements in the array. While traversing, the value of every 
element of Arr is used as an index and the value at this index is marked as negative 
indicate that the value is visited. If any element is already marked negative then this 
is the repeating element. To find the missing element, traverse the array again until an
 element that is not marked negative is found that is to look for a positive value. <br>
###### Psuedocode<br>
PROGRAM missing_and_repeat<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; INPUT : Read T, N, Arr<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SET B = 0<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SET A = 0<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; FOR each element in Arr<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; IF T[element] >= 0 THEN<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; T[element] = -1<br></br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ELSE<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; B = element<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; END IF<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;END FOR<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; FOR i from 1 to N + 1 // i += 1<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; IF T[i] = 0<br> 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  A = i<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; BREAK<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; END IF<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; END FOR<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; PRINT B, A<br>
END<br>
###### Complexity Analysis:<br>
* Time Complexity : O(n). <br>
* Space Complexity : O(n). <br>
###### Python Code <br />
```
class solution:
    
    # method to find the missing and repeating number 
    def missing_and_repeat(self, T):   
        
        for _ in range(T):
            # number of integers in the array
            n=int(input())
            Arr=(int(i) for i in input().split())
            T=[0] * (n + 1)
            for i in Arr:
                if(T[i] >= 0):
                    T[i] = -1
                else:
                    B = i
            for i in range(1, n+1):
                if(T[i] == 0):
                    A = i
                    break
            print(B, A)

# Creating object of solution class
sol = solution()
sol.missing_and_repeat(int(input()))
```

#### Method 2:<br>
###### CPP code :
```
class solution:
    
    # method to find the missing and repeating number 
    def missing_and_repeat(self, T):   
        
        for _ in range(T):
            # number of integers in the array
            n=int(input())
            Arr=[int(i) for i in input().split()]
            print(sum(Arr) - sum(set(Arr)), int(n*(n+1)/2 - sum(set(Arr))))
# Creating object of solution class
sol = solution()
sol.missing_and_repeat(int(input()))
```
In the above method we subtract the sum of the elements in the list Arr and sum of element 
in set(Arr) (set(Arr) eliminates duplicate element) to obtain the repeating element. The 
missing elements is found by subtracting sum of all integers from 1 to n which can be represented 
in general form as n x (n + 1) / 2 and sum of set(Arr). The above code is less efficient when 
compared to that of the first one. This code does not meet the memory requirements.

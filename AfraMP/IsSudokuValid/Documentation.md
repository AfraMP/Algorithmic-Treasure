# DOCUMENTATION
## IS SUDOKU VALID<br>
<a><img src="https://img.shields.io/badge/-Amazon-blue" height="25">&nbsp;&nbsp;
<img src="https://img.shields.io/badge/-Google-blue" height="25">&nbsp;&nbsp;
<img src= "https://img.shields.io/badge/-Interview Bit-navy" height="25">
&nbsp;&nbsp;<img src= "https://img.shields.io/badge/-Python-red" height="25"></a><br><br />
**Problem Statement**<br><br />
Given an incomplete Sudoku configuration in terms of a 9x9  2-D square matrix (mat[][])
 the task to check if the configuration has a solution or not. 
Note: an incomplete Sudoku state - that is a 0 represents empty block.
```
Example 1

Input : 1
        3 0 6 5 0 8 4 0 0 
        5 2 0 0 0 0 0 0 0 
        0 8 7 0 0 0 0 3 1 
        0 0 3 0 1 0 0 8 0 
        9 0 0 8 6 3 0 0 5 
        0 5 0 0 9 0 6 0 0 
        1 3 0 0 0 0 2 5 0 
        0 0 0 0 0 0 0 7 4 
        0 0 5 2 0 6 3 0 0
Output : 1
```
```
Example 2

Input : 1
        3 6 7 5 3 5 6 2 9 
        1 2 7 0 9 3 6 0 6 
        2 6 1 8 7 9 2 0 2 
        3 7 5 9 2 2 8 9 7 
        3 6 1 2 9 3 1 9 4 
        7 8 4 5 0 3 6 1 0 
        6 3 2 0 6 1 5 5 4 
        7 6 5 6 9 3 7 4 5 
        2 5 4 7 4 4 3 0 7 
Output : 0
```
#### Solution<br>
The above problem takes input T, mat indicating testcases and list 
of numbers  ranging from 0 to 9 in 1D array. This matrix is converted 
into 2D matrix ,i.e, 9x9 matrix and stored in variable array. Each element 
in the matrix has its own position i denoting position of the element 
in row and j denoting the position of the element in column. The output 
can be obtained by looping through the entire elements in the matrix array.<br>
CONDITIONS FOR SUDOKU CONFIGURATION TO BE INVALID : <br>
Consider if array[1][2] = 4 then<br>
* If element 4 is present in same row of index 1 
* If element 4 is present in same column of index 2 
* If element 4 is present twice in the same box
* If the sum on each row equals 45
* If the sum on each column equals 45
* If the sum on each box equals 45
###### Python code
```
class Sudoku:   
    
    # method used to check validity of the inputs in sudoku
    def solution(self):
        T = int(input())
        for i in range(T):
            mat = [x for x in input().replace("0",".").split()]
            array = []
            for i in range(0,81,9):
                array.append(mat[i:i+9])
                row = [set() for _ in range(0,9)]
                col = [set() for _ in range(0,9)]
                box = [set() for _ in range(0,9)]
                flag = True
            for i in range(0,9):
                for j in range(0,9):
                    num = array[i][j]
                    if num == ".":
                        continue
                    if num in row[i] or num in col[j] or num in box[(i//3)*3 + j // 3]:
                        flag = False
                        break
                    row[i].add(num)
                    col[j].add(num)
                    box[i//3*3 + j // 3].add(num)
            if flag:
                print(1)
            else:
                print(0)
a = Sudoku()
a.solution()
```
#### Complexity Analysis : <br>
* Time complexity : O(n^2)<br>
* Space Complexity : O(n^2)

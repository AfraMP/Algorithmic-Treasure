# DOCUMENTATION
## COUNT THE REVERSAL<br>
<a><img src="https://img.shields.io/badge/-Amazon-blue" height="25">&nbsp;&nbsp;
<img src= "https://img.shields.io/badge/-Geeks For Geeks-navy" height="25">&nbsp;&nbsp;
<img src="https://img.shields.io/badge/-Python-blue" height="25"></a><br><br />
**Problem Statement**<br><br />
Given a string S consisting only of opening and closing curly brackets '{' and '}' find 
out the minimum number of reversals required to make a balanced expression. 
If it cannot be balanced, then print -1.
```
Example 1

Input : 4
        }{{}}{{{
        {{}}}}
        {{}{{{}{{}}{{
        {{{{}}}}
Output : 3
         1
         -1
         0
```
#### Solution<br>
The above problem includes inputs T, exp representing testcases and expression.<br>
###### Python code:
```
def minReverse(exp):
    if len(exp)%2!=0:
        return -1
    c=0
    op=0

    for e in exp:
        if e=='}' and op==0:
            op=1
            c+=1
        elif e=='}':
            op-=1
        else:
            op+=1

    if op%2!=0:
        return -1
    else:
        return c+op//2

if __name__ == '__main__':
    T = int(input())

    for _ in range(T):
        exp=input()
        print(minReverse(exp))
```
#### Complexity Analysis : <br>
* Time Complexity : O(n)<br>
* Space Complexity : O(n)
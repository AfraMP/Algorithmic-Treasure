# DOCUMENTATION
## WORD BREAK<br>
<a><img src="https://img.shields.io/badge/-Amazon-blue" height="25">
&nbsp;&nbsp;<img src="https://img.shields.io/badge/-Google-blue" height="25">
&nbsp;&nbsp;<img src="https://img.shields.io/badge/-IBM-blue" height="25">
&nbsp;&nbsp;<img src= "https://img.shields.io/badge/-Zoho-navy" height="25">
&nbsp;&nbsp;<img src= "https://img.shields.io/badge/-Interview Bit-navy" height="25">
&nbsp;&nbsp;<img src= "https://img.shields.io/badge/-Python-red" height="25"></a><br><br />
**Problem Statement**<br><br />
Given an input string and a dictionary of words, find out if the input string can be segmented
 into a space-separated sequence of dictionary words.<br />
See following examples for more details.<br />
Consider the following dictionary
{ i, like, sam, sung, samsung, mobile, ice, cream, icecream, man, go, mango}

Input:  ilike
Output: 1
The string can be segmented as "i like".

Input:  ilikesamsung
Output: 1
The string can be segmented as "i like samsung" or "i like sam sung".
```
Example 1

Input : 2
        12
        i like sam sung samsung mobile ice cream icecream man go mango
        ilike
        12
        i like sam sung samsung mobile ice cream icecream man go mango
        idontlike
Output : 1
         0
```
#### Solution<br>
The input involved contains T, N, li and inputString denoting testcases, 
length of the string to be entered, list of n strings and an input string. In this program,
 we append each letter present in inputString into a variable temp and compare it with item in the list. This 
is repeated until string in temp matches any one of the item in the list. If it matches then the 
particular string is stored in another variable resultString. This operation is repeated for the entire string 
in inputString. Atlast, if the length of string resultString is equal to length of string inputString then the output is 1 otherwise 
the output is 0.<br>
###### Python code
```
class wordBreak:
    
    def solution(self):
        T  = int(input())
        while T>0:
            N = int(input())
            li = [str(i) for i in input().split()]
            inputString = input()
            temp = ""
            resultString = ""
            for i in range(len(inputString)):
                temp = temp + inputString[i]
                if temp in li:
                    resultString = resultString + temp
                    temp = ""
            if len(resultString) == len(input):
                print('1')
            else:
                print("0")
            T-=1
a = wordBreak()
a.solution()
```
#### Complexity Analysis : <br>
* Time Complexity : O(n)<br>
* Space Complexity : O(n)
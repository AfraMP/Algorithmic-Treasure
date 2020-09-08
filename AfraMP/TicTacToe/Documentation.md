# DOCUMENTATION
## Tic-Tac-Toe
<a><img src="https://img.shields.io/badge/-Amazon-blue" height="25">&nbsp;&nbsp;
<img src= "https://img.shields.io/badge/-Geeks For Geeks-navy" height="25">&nbsp;&nbsp;
<img src= "https://img.shields.io/badge/-Flipkart-red" height="25">&nbsp;&nbsp;
<img src= "https://img.shields.io/badge/-Microsoft-navy" height="25">&nbsp;&nbsp;
<img src="https://img.shields.io/badge/-Python-blue" height="25"></a><br><br />
**Problem Statement**<br><br />
A Tic-Tac-Toe board is given after some moves are played. Find out if the given board is valid, i.e., is it possible to reach this board position after some moves or not.

Note that every arbitrary filled grid of 9 spaces isn’t valid e.g. a grid filled with 3 X and 6 O isn’t valid situation because each player needs to take alternate turns.<br>

Note :  The game starts with X<br>
```
Example 1

Input : 2
        X X O O X O O O O 
        X X O O O X X O X
Ouput : Invalid
        Valid
```
```
Example 2

Input : 1
        O X X X O X O O X
Output : Valid
```
#### Solution<br>
In this problem we check the validity of the given inputs of a tic-tac-toe game. The game involves two players 'X' and 'O' who take turns marking the spaces in a 3×3 grid. There are 8 strategies in order to win this game.<br>
Consider player 'X', if 'X' occupies one of the row or one of the column or occupies the diagonals of grid then 'X' wins. If 'X' wins then the game ends which also applies to 'O'.
CONDITIONS TO CHECK IF INPUTS ARE INVALID:<br>
* If both player 'X' and 'O' wins
* When 'O' takes a chance after 'X' wins or vice versa
* When number of 'X' exceed number of 'O' by two or more
* When number of 'O's are greater than 'X'

CHECKING THE VALIDITY:<br>
* Number of 'X' exceeds number of 'O' if 'X' wins.
* Number of 'X' and 'O' equal only if 'O' wins.
* Number of 'X' exceed number of 'O' by 1 not greater than that.

POSSIBILITIES OF WINNING A GAME:
* 'X' occupies one of the row or 'O' occupies one of the row.
* 'X' occupies one of the column or 'O' occupies one of the column.
* 'X' occupies one of the diagonals in the grid or 'O' occupies one of the diagonals in the grid.


![Github Logo](http://d1hyf4ir1gqw6c.cloudfront.net/wp-content/uploads/tictactoe.png)
#### Psuedocode<br>
PROGRAM ticTacToe<br>
// Possibilities() is a function to represent possible ways of winnning<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;INPUT: Read T, a<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SET countX = 0<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SET countY = 0<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; FOR each element in a<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; IF element = 0 THEN<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; INCREMENT countX<br></br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ELSE<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; INCREMENT countO<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; END IF<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; IF countO > countX or countX > countO + 1 THEN<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; PRINT Invalid<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ELSE IF Possibilities(a, 'X') and Possibilities(a, 'O') THEN<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; PRINT Invalid<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ELSE IF Possibilities(a, 'O') THEN<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; IF countX == countO THEN<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; PRINT Valid<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ELSE<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;PRINT Invalid.<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ELSE IF countO + 1 == countX or self.Possibilities(a, 'X') THEN<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;PRINT Valid<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ELSE <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;PRINT Invalid<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; END IF<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; END FOR<br>
END<br>
<br />
#### Python Code<br>
```
class ticTacToe:
    
    # method defining the possibilities of winnning
    def Possibilities(self, a, b):
        
        return ((a[0] == b and a[1] == b and a[2] == a[0]) or
            (a[3] == b and a[4] == b and a[5] == b) or
            (a[6] == b and a[7] == b and a[8] == b) or
            (a[0] == b and a[3] == b and a[6] == b) or
            (a[1] == b and a[4] == b and a[7] == b) or
            (a[2] == b and a[5] == b and a[8] == b) or
            (a[0] == b and a[4] == b and a[8] == b) or
            (a[2] == b and a[4] == b and a[6] == b))

    # method used to check the validity of the given input
    def validity(self, T):
        if 1 <= T <= 100:
            for i in range(T):
                countX = 0
                countO = 0
                a = input().split()
                for t in a:
                    if t == 'X':
                        countX += 1
                    else:
                        countO += 1
                if countO > (countX) or (countX > countO + 1) :
                    print("Invalid")
                elif self.Possibilities(a, 'X') and self.Possibilities(a, 'O'):
                    print("Invalid")
                elif self.Possibilities(a, 'O'):
                    if countX == countO:
                        print('Valid')
                    else:
                        print("Invalid")
                elif countO + 1 == countX or self.Possibilities(a, 'X'):
                    print("Valid")
                else:
                    print("Invalid")

# creating objects of class ticTacToe
chec = ticTacToe()
chec.validity(int(input()))
```
#### Complexity Analysis : <br>
* Time Complexity : O(n^2)<br>
* Space Complexity : O(n)

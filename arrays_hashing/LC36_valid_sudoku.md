## Problem 36: Valid Sudoku
You are given a a 9 x 9 Sudoku board board. A Sudoku board is valid if the following rules are followed:
- Each row must contain the digits 1-9 without duplicates.
- Each column must contain the digits 1-9 without duplicates.
- Each of the nine 3 x 3 sub-boxes of the grid must contain the digits 1-9 without duplicates.
  
Return true if the Sudoku board is valid, otherwise return false
Note: A board does not need to be full or be solvable to be valid.

### Code Solution:
```python
class Solution:
    def isValidSudoku(self, board: List[List[str]]) -> bool:
        cols = collections.defaultdict(set) #hashmap, where the key is the column number and the value is another set which represents all particular values in this column
        rows = collections.defaultdict(set) #the same thing, but for rows
        squares = collections.defaultdict(set) #key = (r/3, c/3)..... this is a pair of values which will help is in the 3x3 subgrids

        for r in range(9):
            for c in range(9):
                if board[r][c] == ".": #the board is empty here
                    continue
                if (board[r][c] in rows[r] or #if this current position that we are at is already in the current row that we are in, then we encountered a duplicate
                    board[r][c] in cols[c] or #same thing for cols.
                    board[r][c] in squares[(r//3, c//3)]): #[(r//3), (c//3)] tells us the current square we are in. it will return a set of the current values we have seen in the square before
                        return False
                #if we get here, that means that this current value is valid. we now want to add it to our hash sets.
                cols[c].add(board[r][c]) #to our current column set, add the value at board[r][c]
                rows[r].add(board[r][c]) #to our current row set, add the value at board[r][c]
                squares[(r//3, c//3)].add(board[r][c])  #to our current 3x3 subsquare set, add the value at board[r][c]
        return True

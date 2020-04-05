# Sudoku-solver

## About

A sudoku solver written in Python, that uses backtracking for solving a given board. Backtracking is an algorithmic-technique for solving problems recursively by trying to build a solution incrementally, one piece at a time, removing those solutions that fail to satisfy the constraints of the problem at any point of time.

## The Algorithm

The algorithm requires an incomplete board to begin with. From here it finds a solution by executing the following steps (the backtracking logic):

1. Find an empty space.
2. Place the digits 1-9 in that space.
3. Check if that digit is valid in the current spot based on the current board. If the digit is valid, recursively attempt to fill the board using steps 1-3. If it is not valid, reset the square you just filled and go back to the previous step.
4. Once the board is full, we have found a solution.

```python
def solve(sudoku):
    find = find_empty(sudoku)
    if not find:
        return True
    else:
        row, col = find

    for i in range(1,10):
        if valid(sudoku, i, (row, col)):
            sudoku[row][col] = i

            if solve(sudoku):
                return True
            sudoku[row][col] = 0

    return False
```
The solved sudoku will be returned like this in the output window. 
```
Original sudoku:
0  0  2  | 0  0  0  | 0  6  0
0  4  0  | 0  0  0  | 0  0  0
0  0  5  | 3  6  0  | 4  0  8
-----------------------------
4  0  0  | 0  7  0  | 0  1  5
0  0  0  | 0  1  0  | 0  0  0
9  5  0  | 0  8  0  | 0  0  6
-----------------------------
8  0  6  | 0  5  7  | 9  0  0
0  0  0  | 0  0  0  | 0  2  0
0  3  0  | 0  0  0  | 6  0  0

Solved sudoku:
3  7  2  | 8  4  5  | 1  6  9
6  4  8  | 7  9  1  | 3  5  2
1  9  5  | 3  6  2  | 4  7  8
-----------------------------
4  8  3  | 9  7  6  | 2  1  5
2  6  7  | 5  1  4  | 8  9  3
9  5  1  | 2  8  3  | 7  4  6
-----------------------------
8  2  6  | 4  5  7  | 9  3  1
7  1  9  | 6  3  8  | 5  2  4
5  3  4  | 1  2  9  | 6  8  7
```

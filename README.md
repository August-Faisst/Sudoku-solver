# Sudoku-solver

## About

A sudoku solver written in Python, that uses backtracking for solving a given board. Backtracking is an algorithmic-technique for solving problems recursively by trying to build a solution incrementally, one piece at a time, removing those solutions that fail to satisfy the constraints of the problem at any point of time.

## The Algorithm

The algorithm requires an incomplete board to begin with. From here it finds a solution by executing the following steps (the backtracking logic):

1. Find an empty space.
2. Place the digits 1-9 in that space.
3. Check if that digit is valid in the current spot based on the current board. If the digit is valid, recursively attempt to fill the board using steps 1-3. If it is not valid, reset the square you just filled and go back to the previous step.
4. Once the board is full, we have found a solution.

```
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

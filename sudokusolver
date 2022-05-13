'''
Sudoku solver 
Description: Using recursion to solve any sudoku puzzle
Author: Harlean
'''

def find_empty(puzzle):
    #find next row, col on puzzle that is not filled, replace with -1
    #using 0 indexing i.e. 0-8
    for row in range(9):
        for column in range(9):
            if puzzle[row][column] == -1:
                return row, column
    
    return None, None # no spaces in puzzle left

def is_valid(puzzle, guess, row, column):
    # checks if guess is valid, returns True if valid and False otherwise
    row_values = puzzle[row]
    if guess in row_values:
        return False
    # create new list of values in the column
    column_values = [] 
    for num in range(9):
        column_values.append(puzzle[num][column])
    if guess in column_values:
        return False
    
    #check 3x3 square - find starting index of row, then starting column
    #check first, second then third set of the 3 rows
    start_row = (row // 3) * 3  # e.g. 5 // 3 = 1 * 3 = 3 which is starting row
    start_column = (column // 3) * 3
    for r in range(start_row, start_row + 3):
        for c in range(start_column, start_column + 3):
            if puzzle[r][c] == guess: # already in 3x3 matrix
                return False
    
    return True # passed through all checks

def solve_sudoku(puzzle):
    # using backtracking, puzzle is a list of lists where each inner list is a row
    # return whether a solution exists
    row, column = find_empty(puzzle)
    if row is None:
        return True 
    for guess in range(1, 10):
        if is_valid(puzzle, guess, row, column) is True:
            puzzle[row][column] = guess
            # recursively call func
            if solve_sudoku(puzzle) is True:
                return True
        # guess not valid, sudoku not solved - backtrack
        puzzle[row][column] = -1 # reset
    
    return False # unsolvable

if __name__ == '__main__':
    board = [
        [3, 9, -1,   -1, 5, -1,   -1, -1, -1],
        [-1, -1, -1,   2, -1, -1,   -1, -1, 5],
        [-1, -1, -1,   7, 1, 9,   -1, 8, -1],

        [-1, 5, -1,   -1, 6, 8,   -1, -1, -1],
        [2, -1, 6,   -1, -1, 3,   -1, -1, -1],
        [-1, -1, -1,   -1, -1, -1,   -1, -1, 4],

        [5, -1, -1,   -1, -1, -1,   -1, -1, -1],
        [6, 7, -1,   1, -1, 5,   -1, 4, -1],
        [1, -1, 9,   -1, -1, -1,   2, -1, -1]
    ]
    print(solve_sudoku(board))
    print(board)




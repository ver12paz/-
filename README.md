def solve_sudoku(grid): 

    """ 

    Solves the sudoku puzzle in-place using backtracking. 

    Returns True if a solution is found, otherwise False. 

    """ 

  

    empty = find_empty(grid) 

    if not empty: 

        return True  # solved 

  

    row, col = empty 

  

    for num in range(1, 10): 

        if is_valid(grid, row, col, num): 

            grid[row][col] = num 

  

            if solve_sudoku(grid): 

                return True 

  

            grid[row][col] = 0  # backtrack 

  

    return False 

  

  

def find_empty(grid): 

    """Finds an empty cell (row, col), or None if full.""" 

    for r in range(9): 

        for c in range(9): 

            if grid[r][c] == 0: 

                return r, c 

    return None 

  

  

def is_valid(grid, row, col, num): 

    """Checks whether num can be placed at grid[row][col].""" 

  

    # Check row 

    if num in grid[row]: 

        return False 

  

    # Check column 

    for r in range(9): 

        if grid[r][col] == num: 

            return False 

  

    # Check 3x3 box 

    box_row = (row // 3) * 3 

    box_col = (col // 3) * 3 

  

    for r in range(box_row, box_row + 3): 

        for c in range(box_col, box_col + 3): 

            if grid[r][c] == num: 

                return False 

  

    return True 

  

  

# Example usage 

puzzle = [ 

    [5,3,0,0,7,0,0,0,0], 

    [6,0,0,1,9,5,0,0,0], 

    [0,9,8,0,0,0,0,6,0], 

    [8,0,0,0,6,0,0,0,3], 

    [4,0,0,8,0,3,0,0,1], 

    [7,0,0,0,2,0,0,0,6], 

    [0,6,0,0,0,0,2,8,0], 

    [0,0,0,4,1,9,0,0,5], 

    [0,0,0,0,8,0,0,7,9] 

] 

  

if solve_sudoku(puzzle): 

    for row in puzzle: 

        print(row) 

else: 

    print("No solution exists") 

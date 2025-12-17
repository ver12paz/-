import random 

import copy 

  

def make_sudoku_puzzle(solved_grid, empty_cells=40): 

    """ 

    Takes a solved 9x9 sudoku grid and removes numbers randomly. 

     

    :param solved_grid: 9x9 list of lists (completed sudoku) 

    :param empty_cells: how many cells to clear 

    :return: puzzle grid with empty cells set to 0 

    """ 

    puzzle = copy.deepcopy(solved_grid) 

  

    # All cell positions 

    positions = [(r, c) for r in range(9) for c in range(9)] 

    random.shuffle(positions) 

  

    for i in range(min(empty_cells, 81)): 

        r, c = positions[i] 

        puzzle[r][c] = 0  # 0 means empty 

  

    return puzzle 

  

  

# Example solved sudoku 

solved = [ 

    [5,3,4,6,7,8,9,1,2], 

    [6,7,2,1,9,5,3,4,8], 

    [1,9,8,3,4,2,5,6,7], 

    [8,5,9,7,6,1,4,2,3], 

    [4,2,6,8,5,3,7,9,1], 

    [7,1,3,9,2,4,8,5,6], 

    [9,6,1,5,3,7,2,8,4], 

    [2,8,7,4,1,9,6,3,5], 

    [3,4,5,2,8,6,1,7,9] 

] 

  

puzzle = make_sudoku_puzzle(solved, empty_cells=45) 

  

# Print the puzzle 

for row in puzzle: 

    print(row) 

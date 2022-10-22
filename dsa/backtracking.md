# Backtracking

> Backtracking can be defined as a general algorithmic technique that considers searching every possible combination in order to solve a computational problem. It is a kind of recursion ([[Recursion]])

#### <span style="color:red">N queen problem</span>
```python
class Solution:
    def solveNQueens(self, n: int) -> List[List[str]]:
        col = set()
        posDiag = set()
        negDiag = set()
        
        res = []
        board = [["."] * n for i in range(n)]
        
        def backtrack(r):
            if r == n:
                copy = ["".join(row) for row in board]
                res.append(copy)
                return
            
            for c in range(n):
                if c in col or (r + c) in posDiag or (r - c) in negDiag:
                    continue
            
                col.add(c)
                posDiag.add(r + c)
                negDiag.add(r - c)
                board[r][c] = "Q"
                
                backtrack(r + 1)
                
                col.remove(c)
                posDiag.remove(r + c)
                negDiag.remove(r - c)
                board[r][c] = "."
                
        backtrack(0)
        return res
```

#### <span style="color:red">Sudoku solver</span>
```python
def print_grid(arr):
	for i in range(9):
		for j in range(9):
			print arr[i][j],
		print ('n')

def find_empty_location(arr, l):
	for row in range(9):
		for col in range(9):
			if(arr[row][col]== 0):
				l[0]= row
				l[1]= col
				return True
	return False

def used_in_row(arr, row, num):
	for i in range(9):
		if(arr[row][i] == num):
			return True
	return False

def used_in_col(arr, col, num):
	for i in range(9):
		if(arr[i][col] == num):
			return True
	return False

def used_in_box(arr, row, col, num):
	for i in range(3):
		for j in range(3):
			if(arr[i + row][j + col] == num):
				return True
	return False

def check_location_is_safe(arr, row, col, num):

	return not used_in_row(arr, row, num) and
		not used_in_col(arr, col, num) and
		not used_in_box(arr, row - row % 3,
						col - col % 3, num)

def solve_sudoku(arr):
	
	l =[0, 0]
	
	if(not find_empty_location(arr, l)):
		return True

	row = l[0]
	col = l[1]
	
	for num in range(1, 10):
		
		if(check_location_is_safe(arr,
						row, col, num)):
			
			arr[row][col]= num

			if(solve_sudoku(arr)):
				return True

			arr[row][col] = 0
			
	return False

if __name__=="__main__":
	
	grid =[[0 for x in range(9)]for y in range(9)]
	
	grid =[[3, 0, 6, 5, 0, 8, 4, 0, 0],
		[5, 2, 0, 0, 0, 0, 0, 0, 0],
		[0, 8, 7, 0, 0, 0, 0, 3, 1],
		[0, 0, 3, 0, 1, 0, 0, 8, 0],
		[9, 0, 0, 8, 6, 3, 0, 0, 5],
		[0, 5, 0, 0, 9, 0, 6, 0, 0],
		[1, 3, 0, 0, 0, 0, 2, 5, 0],
		[0, 0, 0, 0, 0, 0, 0, 7, 4],
		[0, 0, 5, 2, 0, 6, 3, 0, 0]]
	
	if(solve_sudoku(grid)):
		print_grid(grid)
	else:
		print "No solution exists"
```
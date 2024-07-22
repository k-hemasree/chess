def is_safe(board,row,col):
    for i in range(row):
        if board[i] == col:
            return False
    for i,j in zip (range(row-1, -1, -1),range(col-1, -1, -1)):
        if board[i] == j:
            return False
    for i,j in zip(range(row-1, -1, -1),range(col+1, 8)):
        if board[i]==j:
            return False
    return True
            
def solve_queens_util(board,row):
    if row>=8:
        return True
    for col in range(8):
        if is_safe(board,row,col):
            board[row]=col
            if solve_queens_util(board,row+1):
                return True
            board[row]=-1
            
    return False
def solve_queen():
    board=[-1]*8
    if not solve_queens_util(board,0):
        print("solution does not exist")
        return False
    
    print("solution:")
    for i in range(8):
        for j in range(8):
            if board[i]==j:
                print("Q",end=" ")
            else:
                print(".",end=" ")
        print()
    return True

solve_queen()
        

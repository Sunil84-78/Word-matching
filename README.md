def exists(board, word):
    def dfs(i, j, index):
        if index == len(word):  
            return True
        if i < 0 or j < 0 or i >= len(board) or j >= len(board[0]) or board[i][j] != word[index]:
            return False  

        
        temp = board[i][j]
        board[i][j] = '#'

        
        result = (dfs(i+1, j, index+1) or dfs(i-1, j, index+1) or
                  dfs(i, j+1, index+1) or dfs(i, j-1, index+1))

      
        board[i][j] = temp
        return result

    for i in range(len(board)):
        for j in range(len(board[0])):
            if board[i][j] == word[0] and dfs(i, j, 0):  # Start DFS if match found
                return True
    return False


board = [
    ['A', 'B', 'C', 'E'],
    ['S', 'F', 'C', 'S'],
    ['A', 'D', 'E', 'E']
]
word ="input"
print(exists(board, word))  

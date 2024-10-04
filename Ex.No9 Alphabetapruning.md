# Ex.No: 9   Implementation of Alpha Beta Pruning 
### DATE:                                                                            
### REGISTER NUMBER : 
### AIM: 
Write a Alpha beta pruning algorithm to find the optimal value of MAX Player from the given graph.
### Steps:
1. Start the program
2. Initially  assign MAX and MIN value as 1000 and -1000.
3.  Define the minimax function  using alpha beta pruning
4.  If maximum depth is reached then return the score value of leaf node. [depth taken as 3]
5.  In Max player turn, assign the alpha value by finding the maximum value by calling the minmax function recursively.
6.  In Min player turn, assign beta value by finding the minimum value by calling the minmax function recursively.
7.  Specify the score value of leaf nodes and Call the minimax function.
8.  Print the best value of Max player.
9.  Stop the program. 

### Program:
```
# Define the game tree
game_tree = {
    'A': {'B': 3, 'C': 5},
    'B': {'D': 2, 'E': 4},
    'C': {'F': 6, 'G': 1},
    'D': 2,
    'E': 4,
    'F': 6,
    'G': 1
}

# Define the alpha-beta pruning algorithm
def alpha_beta(node, depth, alpha, beta, is_maximizing_player):
    if depth == 0 or node not in game_tree or isinstance(game_tree[node], int):
        return game_tree[node]

    if is_maximizing_player:
        value = float('-inf')
        for child in game_tree[node]:
            value = max(value, alpha_beta(child, depth - 1, alpha, beta, False))
            alpha = max(alpha, value)
            if alpha >= beta:
                break
        return value
    else:
        value = float('inf')
        for child in game_tree[node]:
            value = min(value, alpha_beta(child, depth - 1, alpha, beta, True))
            beta = min(beta, value)
            if alpha >= beta:
                break
        return value

# Test the alpha-beta pruning algorithm
alpha = float('-inf')
beta = float('inf')
depth = 2
root_node = 'A'
optimal_value = alpha_beta(root_node, depth, alpha, beta, True)
print("Optimal value for root node:", optimal_value)
```

### Output:
![Screenshot 2024-10-04 141221](https://github.com/user-attachments/assets/92e6b322-18c2-4b17-97b6-1ec2c6d30385)



### Result:
Thus the best score of max player was found using Alpha Beta Pruning.

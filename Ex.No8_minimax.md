### Ex.No: 8  Implementation of Minimax Search                                                                 
### REGISTER NUMBER : 212221230078
### AIM: 
Write a mini-max search algorithm to find the optimal value of MAX Player from the given graph.
### Algorithm:
1. Start the program
2. import the math package
3. Specify the score value of leaf nodes and find the depth of binary tree from leaf nodes.
4. Define the minimax function
5. If maximum depth is reached then get the score value of leaf node.
6. Max player find the maximum value by calling the minmax function recursively.
7. Min player find the minimum value by calling the minmax function recursively.
8. Call the minimax function  and print the optimum value of Max player.
9. Stop the program. 

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

# Define the Mini-Max algorithm
def mini_max(node, depth, is_maximizing_player):
    if depth == 0 or node not in game_tree or isinstance(game_tree[node], int):
        return game_tree[node]

    if is_maximizing_player:
        value = float('-inf')
        for child in game_tree[node]:
            value = max(value, mini_max(child, depth - 1, False))
        return value
    else:
        value = float('inf')
        for child in game_tree[node]:
            value = min(value, mini_max(child, depth - 1, True))
        return value

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

# Test the Mini-Max algorithm
print("Mini-Max value:", mini_max('A', 2, True))

# Test the alpha-beta pruning algorithm
print("Alpha-Beta value:", alpha_beta('A', 2, float('-inf'), float('inf'), True))
```
### Output:
![Screenshot 2024-10-04 140828](https://github.com/user-attachments/assets/cb65e5f2-ad3f-4969-a528-425c996715e8)



### Result:
Thus the optimum value of max player was found using minimax search.

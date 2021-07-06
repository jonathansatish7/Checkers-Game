# Checkers-Game
----------------------------------------------------------------------------
### Search abstraction:
*Initial state*: The given board containing white and black pichus and pikachus.

*Terminal State*: If all the pichus or pikachus of any of the player are zero, that is the terminal state. It is the position of the board when the game gets over.

*Successor states*: any board which is obtained after a valid move of pichu or pikachu

*Evaluation function*: 

For w turn:

(2 * no of white pikachus + no of white pichus) – (2 * no of black pikachus + no of black pichus)

For b turn:

(2 * no of black pikachus + no of black pichus) – (2 * no of white pikachus + no of white pichus)

### Design decisions and working:
* Different functions have been written to calculate the successors for the given player. According to our functions a pichu will be able to move one step forward, left and right if the square is empty and it can move two steps forward if there is an opponent in between and the next square is empty. A pikachu moves forward, backward, left and right any number of squares and jumps over the opponent and then moves a square, if the squares between the Pikachu and the opponent are empty and the one next to the opponent is also empty. all these functions that define each move of the player have been called in a function successors().

* A successor function to return all the possible successors for the player ‘w’ or ‘b’.The list_successors_w has the list of successors of w and list_successors_b has the list of successors of b. the list of successors are appended in such a way that each successor is checked if it is not the same as the board passed as a parameter.

* We used minimax algorithm with alpha beta pruning and iterative deepening search tree to form the leaf nodes and then back track the values from the depth upwards using the evaluation function applied to the leaf nodes till the root node and then the algorithm gives the best move considering the alpha and beta values of the max and min players respectively. We assign the default alpha beta values to the root, we then carry these values alpha and beta to the child node on the left. And now from the utility value of the terminal state, we will update the values of alpha. Thus alpha beta pruning is done and all the successors with the payoffs are pushed into the stack. The best move or the successor with max value is popped out. Which is the ultimate best move for the player and new board.

* The max value and min value of the successors are being calculated by using the functions:

def max_v(successor, alpha, beta, depth, player, depthlimit,N):

def min_v(successor, alpha, beta, depth, player, depthlimit,N):

these functions are used to calculate the alpha and beta values for min successors and max successors

* There is a terminal state or end state which returns true if the number of w’s or b’s is 0.If the depth reaches the limit then it starts calculating the payoffs using the evaluation function.

* An evaluation function also known as heuristic evaluation function is used to estimate the value or goodness of a position of the player in a particular game. In the evaluation function, the pikachus are given a value of 2 and pichus are given 1. We calculated the payoff to be ((2 * count_W) + (count_w) - (2 * count_B) - (count_b)) for w’s turn. and the payoff to be ((2 * count_B) + (count_b) - (2 * count_W) - (count_w)) for b’s turn.

### Assumptions :
* We took the default values of alpha and beta to be 500000000 and -500000000.

* We assumed the weights of pikachus to be 2 and weights of pichus to be 1 and calculated the weighted features for b and w

### Difficulties:
* We faced difficulty in setting the limits for the row and columns as we have converted the given string to a 2d array. In order to iterate through the rows and columns for the edge cases we had to pass different boards if the output was correctly updating or not.

* We faced hurdle to figure out how to set the time limit and how to run the minimax algorithm such that it stops at the particular leaf node according to the time limit given and how to back track the alpha and beta values to the root node and apply the alpha beta pruning.

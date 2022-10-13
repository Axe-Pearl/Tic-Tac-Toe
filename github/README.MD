
#  Minimax Algorithm  (Implementation in Tic-Tac-Toe)

Mini-max algorithm is a recursive or backtracking algorithm which
is used in decision-making and game theory.

• Step-1: In the first step, the algorithm generates the entire game-tree
and apply the utility function to get the utility values for the terminal
states.

• In the below tree diagram, let's take A is the initial state of the tree.
Suppose maximizetakes first turn which has worst-case initial value
=- infinity, and minimiser will take next turn which has worst-case initial value = +infinity.

## Screenshots

![Screenshot_20221005-134408_2](https://user-images.githubusercontent.com/101443787/194036654-83e5b386-dddb-49f5-af09-87ec1629464c.jpg)

• Step 2: Now, first we find the utilities value for the Maximizer, its
initial value is -∞, so we will compare each value in terminal state
with initial value of Maximizer and determines the higher nodes
values. It will find the maximum among the all.

• Step 3: In the next step, it's a turn for minimizer, so it will compare
all nodes value with +∞, and will find the 3rd layer node values.

• Step 4: Now it's a turn for Maximizer, and it will again choose the
maximum of all nodes value and find the maximum value for the root
node. In this game tree, there are only 4 layers, hence we reach
immediately to the root node, but in real games, there will be more than 4 layers.

## Example Tic-Tac-Toe
![Screenshot_20221005-155423_1](https://user-images.githubusercontent.com/101443787/194039781-1aa854ec-20ef-4266-873c-fc4c445cfc94.jpg)

This image depicts all the possible paths that the game can take from the root board state. It is often called the Game Tree. 

The 3 possible scenarios in the above example are : 

• Left Move : If X plays [2,0]. Then O will play [2,1] and win the game. The value of this move is -10
• Middle Move : If X plays [2,1]. Then O will play [2,2] which draws the game. The value of this move is 0
• Right Move : If X plays [2,2]. Then he will win the game. The value of this move is +10;

Remember, even though X has a possibility of winning if he plays the middle move, O will never let that happen and will choose to draw instead.
Therefore the best choice for X, is to play [2,2], which will guarantee a victory for him.

## Alpha-beta pruning

❖ Alpha-beta pruning is a modified version of the minimax algorithm.
It is an optimization technique for the minimax algorithm.

❖The main condition which required for alpha-beta pruning is:
α>=β

❖ Step 1: At the first step the, Max player will start first
move from node A where α= -∞ and β= +∞, these value of alpha and
beta passed down to node B where again α= -∞ and β= +∞, and Node
B passes the same value to its child D

![Screenshot_20221005-160436_1](https://user-images.githubusercontent.com/101443787/194041390-37c5b10e-42e2-4280-9cbc-fdddbe23916c.jpg)

❖Step 2: At Node D, the value of α will be calculated as its turn for
Max. The value of α is compared with firstly 2 and then 3, and the
max (2, 3) = 3 will  be the value of α at node D and node value will also 3.

❖Step 3: Now algorithm backtrack to node B, where the value of β
will change as this is a turn of Min, Now β= +∞, will compare with
the available subsequent nodes value, i.e. min (∞, 3) = 3, hence at
node B now α= -∞, and β= 3.

![Screenshot_20221005-161023_1](https://user-images.githubusercontent.com/101443787/194042272-f1f2e621-6af5-4073-93ad-90180e2bb37a.jpg)

❖Step 4: At node E, Max will take its turn, and the value of alpha
will change. The current value of alpha will be compared with 5, so
max (-∞, 5) = 5, hence at node E α= 5 and β= 3, where α>=β, so the
right successor of E will be pruned,and algorithm will not traverse it, and the value at node E will be 5.

❖ Step 5: At next step, algorithm again backtrack the tree, from node
B to node A. At node A, the value of alpha will be changed the
maximum available value is 3 as max (-∞, 3)= 3, and β= +∞, these
two values now passes to right successor of A which is Node C.
❖ At node C, α=3 and β= +∞, and the same values will be passed on
to node F.

❖ Step 6: At node F, again the value of α will be compared with left
child which is 0, and max(3,0)= 3, and then compared with right
child which is 1, and max(3,1)= 3 still α remains 3,but the nodevalue of F will become 1.

![Screenshot_20221005-161032_2](https://user-images.githubusercontent.com/101443787/194043156-654b6720-a62c-4d91-9f47-3c2400677a34.jpg)

❖Step 7: Node F returns the node value 1 to node C, at C α= 3 and
β= +∞, here the value of beta will be changed, it will compare with 1
so min (∞, 1) = 1. Now at C, α=3 and β= 1, and again it satisfies the
condition α>=β, so the next child of C which is G will be pruned, and
the algorithm will not compute the entire sub-tree G.

❖Step 8: C now returns the value of 1 to A here the best value for A
is max (3, 1) = 3. Following is the final game tree which is the
showing the nodes which are computed and nodes which has never
computed. Hence the optimal value for the maximizer is 3 for this example.


![Screenshot_20221005-161048_1](https://user-images.githubusercontent.com/101443787/194043865-873be88d-48a6-46b8-bc22-778dd48a5fe1.jpg)


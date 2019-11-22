# CSCI-B 551 Elements of Artficial Intelligence

### IJK-game

### Problem Statement
IJK is a sliding tile game played on a 4x4 board by two players, lowercase (also known as -) and uppercase (+). The players take turns, starting with uppercase. At the start of each turn, a tile labeled a is added randomly somewhere on the board if it is lowercase’s turn, and an A is added if it is uppercase’s turn. A player’s turn consists of making one of ﬁve possible moves: Up, Down, Left, Right, or Skip. Skip means nothing further happens and the player forfeits their turn. Otherwise, all tiles are slid in the direction that the player selected until there are no empty spaces left in that direction. Then, pairs of letters that are the same, of the same case, and adjacent to each other in the direction of the movement are combined together to create a single tile of the subsequent letter and the same case. For example, if an A slides down and hits another A, the two merge and become a single B. Similarly, pairs of B’s merge to become a single C, and so on. For pairs of letters that are the same but with opposite case, e.g. A and a, the tiles merge to become the letter B if it is uppercase’s turn, or b if it is lowercase’s turn. The game ends when a K or k appears on the board, and the player of that case wins the game.
The game has two speciﬁc variants. In Deterministic IJK, the new a or A at the beginning of each turn is added to a predictable empty position on the board (which is a function of the current board state). In Non-deterministic IJK, the new a or A is added to a random position on the board. The rest of the rules are the same for the two variants.
Your goal is to write AI clode that plays these two variants of IJK well. We’ve prepared skeleton code to help you. You can run the code like this:
./ijk.py [uppercase-player] [lowercase-player] [mode]
where uppercase-player and lowercase-player are each either ai or human, and mode is either det for deterministic IJK or nondet for nondeterministic IJK. These commands let you set up various types of games. For example, if you (a human) want to play a deterministic game against the ai, you could type:
./ijk.py human ai det

### We have implemented this game using minimax with alpha-beta pruning and looking 6 steps ahead (has a depth of 6) of the current position of the board. It backs up the value which is going to increase the chances of winning for that player. We tried implementing 3 heuristics for our program.

### The first heuristic is simply the subtraction of the no. of tiles of player 1 and no. of tiles of player 2. The board which has this value highest is chosen and backed up. This one is used in the running and submitted code.

### The second heuristic is: if 2 same alphabets having the same case lie on a row or a column, they add up to the final score. So, there needs to even a pair of alphabets. Then only score gets added to that particular board configuration. E.g.: if one of the rows contains ‘aa’ as well as ‘AA’, then that row gets a score of 2. The same goes for a situation in a column. Finally, all these scores add to the board score. 

### We had the third heuristic in mind but due to lack of time, we couldn’t implement it. This heuristic is built on top of heuristic 2 where instead of giving scores based on the same pairing, we give score even if two different case alphabets are beside each other. E.g.: if one of the rows contains ‘a’ as well as ‘A’, then that row gets a score of 1. The same goes for a situation in a column. Finally, all these scores add to the board score.

### We ran around 12 trials for choosing the efficient heuristic for both det and nondet. In the trials, our first heuristic won 9 games, second heuristic won 2 and one ended in a tie. Hence, we went ahead with the first heuristic.

# Connect-4-Create-Task
This is a game of connect 4 that you can play against. It looks 7 moves ahead and calculates the best move. I made it as part of the Computer Science Principles AP test.

The game is set up as a normal 2 player game of connect for with functions to draw the board, add tiles to the board, and check if someone has won, etc.
The board is stored in the 2d array board[].
Instead of asking a second player for their input, the move2 function calculates the best move for the program to make. It beats me most of the time.

It works by simulaing all the posibilitys for the next 7 moves and for every outcome where it wins it increases the score for that move and decreases if when it loses.
This aproach is very inefficient because it has no way of determining who is winning on a given board state unless one person has won. 
I tried adding a heuistic function to alter the scores based on who has more 3 in a rows but I couldn't get it to work in time.

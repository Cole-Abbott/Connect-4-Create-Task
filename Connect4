#include <cs50.h>
#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>

//global variables
int board[6][7];
int sim_board[6][7];
int move_score[7] = {0, 0, 0, 0, 0, 0, 0};


//functions
void setup(void) //sets up the game
{
    for(int i = 0; i < 6; i++) //fills board and sim_board with 0s
    {
        for(int j = 0; j < 7; j++)
        {
            board[i][j] = 0;
            sim_board[i][j] = 0;
        }
    }


}

void clear(void) // clears the screen
{
    printf("\033[2J");
    printf("\033[%d;%dH", 0, 0);
}

void draw(void) //draws board
{

    clear();
    printf("YOU: X  VS.  COMPUTER: O\n");
    for(int i = 0; i < 6; i++) //fills board and sim_board with 0s
    {
        for(int j = 0; j < 7; j++)
        {
            if (board[i][j] == 0)
            {
                printf("| ");
            }
            else if (board[i][j] == 1)
            {
                printf("|X");
            }
            else if (board[i][j] == 2)
            {
                printf("|O");
            }
        }
        printf("|\n");
    }
    printf(" 1 2 3 4 5 6 7 \n");
}

bool add(spot, player, sim) //adds the tile to the correct spot, spot can be 0-6, player can be 1 or 2, board can be 0,1
{
    if (sim == 0) //adds to board
    {
        if (board[0][spot] != 0) //makes sure it is a valid move
        {
            printf("Invalid Move\n");

            return false;
        }
        if (spot > 6 || spot < 0)
        {
            printf("Invalid Move\n");
            return false;
        }

        for(int i = 0; i < 7; i++) //adds tile to row
        {
            if (i == 6)
            {
                board[5][spot] = player;
                return true;
            }
            if (board[i][spot] != 0)
            {
                board[i - 1][spot] = player;
                return true;
            }
        }

    }

    if (sim == 1) // adds to sim board
    {
        if (sim_board[0][spot] != 0) //makes sure it is a valid move
        {
            return false;
        }

        for(int i = 0; i < 7; i++)
        {
            if (i == 6)
            {
                sim_board[5][spot] = player;
                return true;
            }
            if (sim_board[i][spot] != 0)
            {
                sim_board[i - 1][spot] = player;
                return true;
            }
        }

    }
    return false;
}

int won(void) //checks if someone has won
{
    int count1 = 0, count2 = 0;

    for(int i = 0; i < 6; i++)//checks across
    {
        for(int j = 0; j < 7; j++)
        {
            if(board[i][j] == 1)
            {
                count1++;
                count2 = 0;
                if (count1 == 4)
                {
                    return 1;
                    //printf("test1");
                }
            }
            else if (board[i][j] == 2)
            {
                count2++;
                count1 = 0;
                if (count2 == 4)
                {
                    return 2;
                    //printf("test2");
                }
            }
            else
            {
                count1 = 0;
                count2 = 0;
            }
        }
        count1 = 0;
        count2 = 0;
    }

    for(int j = 0; j < 7; j++) //checks vertical
    {
        for(int i = 0; i < 6; i++)
        {
            if(board[i][j] == 1)
            {
                count1++;
                count2 = 0;
                if (count1 == 4)
                {
                    return 1;
                }
            }
            else if (board[i][j] == 2)
            {
                count2++;
                count1 = 0;
                if (count2 == 4)
                {
                    return 2;
                }
            }
            else
            {
                count1 = 0;
                count2 = 0;
            }
        }
        count1 = 0;
        count2 = 0;
    }

    for(int i = 0; i < 3; i++) //checks top left to bottom right
    {
       for(int j = 0; j < 4; j++)
       {
           if (board[i][j] == 1 && board[i][j] == board[i+1][j+1] && board[i][j] == board[i+2][j+2] && board[i][j] == board[i+3][j+3])
           {
               return 1;
           }
           else if (board[i][j] == 2 && board[i][j] == board[i+1][j+1] && board[i][j] == board[i+2][j+2] && board[i][j] == board[i+3][j+3])
           {
               return 2;
           }
       }
    }

    for(int i = 3; i < 6; i++) //checks bottom left to top right
    {
       for(int j = 0; j < 4; j++)
       {
           if (board[i][j] == 1 && board[i][j] == board[i-1][j+1] && board[i][j] == board[i-2][j+2] && board[i][j] == board[i-3][j+3])
           {
               return 1;
           }
           else if (board[i][j] == 2 && board[i][j] == board[i-1][j+1] && board[i][j] == board[i-2][j+2] && board[i][j] == board[i-3][j+3])
           {
               return 2;
           }
       }
    }

    return 0;

}

int sim_won(void) //checks if someone has won on sim_board
{
    int count1 = 0, count2 = 0;

    for(int i = 0; i < 6; i++)//checks across
    {
        for(int j = 0; j < 7; j++)
        {
            if(sim_board[i][j] == 1)
            {
                count1++;
                count2 = 0;
                if (count1 == 4)
                {
                    return 1;
                }
            }
            else if (sim_board[i][j] == 2)
            {
                count2++;
                count1 = 0;
                if (count2 == 4)
                {
                    return 2;
                }
            }
            else
            {
                count1 = 0;
                count2 = 0;
            }
        }
        count1 = 0;
        count2 = 0;
    }

    for(int j = 0; j < 7; j++) //checks vertical
    {
        for(int i = 0; i < 6; i++)
        {
            if(sim_board[i][j] == 1)
            {
                count1++;
                count2 = 0;
                if (count1 == 4)
                {
                    return 1;
                }
            }
            else if (sim_board[i][j] == 2)
            {
                count2++;
                count1 = 0;
                if (count2 == 4)
                {
                    return 2;
                }
            }
            else
            {
                count1 = 0;
                count2 = 0;
            }
        }
        count1 = 0;
        count2 = 0;
    }

    for(int i = 0; i < 3; i++) //checks top left to bottom right
    {
       for(int j = 0; j < 4; j++)
       {
           if (sim_board[i][j] == 1 && sim_board[i][j] == sim_board[i+1][j+1] && sim_board[i][j] == sim_board[i+2][j+2] && sim_board[i][j] == sim_board[i+3][j+3])
           {
               return 1;
           }
           else if (sim_board[i][j] == 2 && sim_board[i][j] == sim_board[i+1][j+1] && sim_board[i][j] == sim_board[i+2][j+2] && sim_board[i][j] == sim_board[i+3][j+3])
           {
               return 2;
           }
       }
    }

    for(int i = 3; i < 6; i++) //checks bottom left to top right
    {
       for(int j = 0; j < 4; j++)
       {
           if (sim_board[i][j] == 1 && sim_board[i][j] == sim_board[i-1][j+1] && sim_board[i][j] == sim_board[i-2][j+2] && sim_board[i][j] == sim_board[i-3][j+3])
           {
               return 1;
           }
           else if (sim_board[i][j] == 2 && sim_board[i][j] == sim_board[i-1][j+1] && sim_board[i][j] == sim_board[i-2][j+2] && sim_board[i][j] == sim_board[i-3][j+3])
           {
               return 2;
           }
       }
    }

    return 0;

}

int move2(void) // current move function, search depth of 6 with no heuristic
{
  int count = 0; //for testing
  for(int i = 0; i < 6; i++) //updates sim_board
    {
        for(int j = 0; j < 7; j++)
        {
            sim_board[i][j] = board[i][j];
        }
        move_score[i] = 0;
        move_score[6] = 0;
    }

//goes through all possable combanations of the next 7 moves and calculates a score based on who wins
    for(int i =0; i < 7; i++)
    {
        for(int j =0; j < 7; j++)
        {
            for(int w =0; w < 7; w++)
            {
                for(int e =0; e < 7; e++)
                {
                    for(int g =0; g < 7; g++)
                    {
                        for(int k =0; k < 7; k++)
                        {
                            for(int h = 0; h < 7; h++)
                            {
                                if (!add(i, 2, 1)) //adds a tile to simboard, if it is invalid it moves on
                                {
                                    j = 7;
                                    w = 7;
                                    e = 7;
                                    g = 7;
                                    k = 7;
                                    h = 7;
                                    move_score[i] = move_score[i] - 10000;
                                }
                                else if (sim_won() == 2) //changes the score if someone won and moves to the next move
                                {
                                    move_score[i] = move_score[i] + 1000;

                                    j = 7;
                                    w = 7;
                                    e = 7;
                                    g = 7;
                                    k = 7;
                                    h = 7;

                                }
                                else
                                {
                                    if (!add(j, 1, 1))//repeats the above for the user, then again for comp. etc...
                                    {
                                        w = 7;
                                        e = 7;
                                        g = 7;
                                        k = 7;
                                        h = 7;
                                    }
                                    else if (sim_won() == 1)
                                    {
                                        move_score[i] = move_score[i] - 1000;
                                        j = 7;
                                        w = 7;
                                        e = 7;
                                        g = 7;
                                        k = 7;
                                        h = 7;
                                    }
                                    else
                                    {
                                        if (!add(w, 2, 1))
                                        {
                                            e = 7;
                                            g = 7;
                                            k = 7;
                                            h = 7;
                                        }
                                        else if (sim_won() == 2)
                                        {
                                            move_score[i] = move_score[i] + 10;
                                            w = 7;
                                            e = 7;
                                            g = 7;
                                            k = 7;
                                            h = 7;
                                        }
                                        else
                                        {
                                            if (!add(e, 1, 1))
                                            {
                                                g = 7;
                                                k = 7;
                                                h = 7;
                                            }
                                            else if (sim_won() == 1)
                                            {
                                                move_score[i] = move_score[i] - 10;
                                                e = 7;
                                                g = 7;
                                                k = 7;
                                                h = 7;
                                            }
                                            else
                                            {
                                                if (!add(g, 2, 1))
                                                {
                                                    k = 7;
                                                    h = 7;
                                                }
                                                else if (sim_won() == 2)
                                                {
                                                    move_score[i] = move_score[i] + 1;
                                                    g = 7;
                                                    k = 7;
                                                    h = 7;
                                                }
                                                else
                                                {
                                                    if (!add(k, 1, 1))
                                                    {
                                                        h = 7;
                                                    }
                                                    else if (sim_won() == 1)
                                                    {
                                                        move_score[i] = move_score[i] - 1;
                                                        k = 7;
                                                        h = 7;
                                                    }
                                                    else
                                                    {
                                                        if (!add(h, 2, 2))
                                                        {
                                                        }
                                                        else if (sim_won() == 2)
                                                        {
                                                            move_score[i] = move_score[i] + 1;
                                                            h = 7;
                                                        }
                                                    }
                                                }
                                            }
                                        }
                                    }
                                }
                                for(int t = 0; t < 6; t++) //updates sim_board
                                {
                                    for(int s = 0; s < 7; s++)
                                    {
                                        sim_board[t][s] = board[t][s];
                                    }
                                }
                            }
                        }
                    }
                }
            }
        }
    }

    int comp_move = 0;//picks the highest score and returns that move
    for(int i = 0; i < 7; i++)
    {
        printf(" %i ", move_score[i]);
        if (move_score[i] > move_score[comp_move])
        {
            comp_move = i;
        }
    }
    printf("\n %i ", count); //for testing

    return comp_move;
}

//the main loop that runs the game
int main(void)
{
    setup();
    draw();
    int p_move = 0;
    bool valid = false;
    bool game_on = true;
    while (game_on)
    {
        while(!valid)
        {
            p_move = get_int("Enter your move: ");//asks user to input move
            valid = add(p_move - 1, 1, 0);
        }
        valid = false;
        draw();

        if( won() == 1) //checks for win
        {
            printf("***YOU WIN***\n");
            char again = get_char("WOULD YOU LIKE TO PLAY AGAIN? (Y, N)"); //asks if user wants to play again
            if(toupper(again) == 89)
            {
                setup();
                draw();
            }
            else
            {
                break;
            }
        }
        int computer_move = move2(); //gets move from computer

        add(computer_move, 2, 0);
        draw();
        if( won() == 2) //checks for win
        {
           printf("***YOU LOSE***\n");
           char again = get_char("WOULD YOU LIKE TO PLAY AGAIN? (Y, N)");
           if(toupper(again) == 89)
           {
               setup();
               draw();
           }
           else
           {
               break;
           }

           int tie = 0;
           for (int j = 0; j < 7; j++) //ends game if there is a tie
           {
               if (!(board[0][j] == 0))
               {
                   tie++;
                   if (tie == 7)
                   {
                       printf("***IT'S A TIE***\n");
                       again = get_char("WOULD YOU LIKE TO PLAY AGAIN? (Y, N)");
                       if(toupper(again) == 89)
                       {
                           setup();
                           draw();
                        }
                       else
                       {
                           break;
                       }
                   }
               }
           }
        }
    }
}

# Rock, Paper, Scissors
Today we are going to do a new game: rock, paper, scissors game. The logic of this simple game inspires lot of videogames.

Lets think about what we need for this game:
1. Computer will choose one of the three options using random
2. Ask the user for an option
3. Check the logic of the game to resolve the play and output the result.

## Coding
One of the things needed for this game is to handle the three options: rock, paper, scissors. We could use characters as we have used to store the name in previous exercise. but in this cases the best solution is to use a code.

A code will match each posibility with a number, so we can define the following code:
* Rock = 0
* Paper = 1
* Scissors = 2
  
So in the variables used in our code there will be an integer that is going to store the code for a given option.

This code can be used while asking the user to choose an option. This way the user will provide just a number.

```c++
#include <iostream>
#include <cstdlib>

int main() {
  int computer_option = rand() % 3; // will provide a number between 0 and 2
  int player_option;
  // Messages with the instructions of the game
  std::cout << "ROCK, PAPER SCISSORS GAME!!\n";
  std::cout << "Try to beat me, choose an option between 0 and 2\n";
  std::cout << "0 - Rock\n";
  std::cout << "1 - Paper\n";
  std::cout << "2 - Scissors\n";
  // Get the user option
  std::cin >> player_option;

  std::cout << "Computer chose: " << computer_option << "\n";
  std::cout << "Player chose: " << player_option << "\n";

  // Check all posibilities
  if (computer_option == 0)
  {
    if (player_option == 0)
    {
      std::cout << "Draw\n";      
    }
    if (player_option == 1)
    {
      std::cout << "Player wins\n";
    }
    if (player_option == 2)
    {
      std::cout << "Computer wins\n";
    }
  }
  if (computer_option == 1)
  {
    if (player_option == 0)
    {
      std::cout << "Computer wins\n";
    }
    if (player_option == 1)
    {
      std::cout << "Draw\n";
    }
    if (player_option == 2)
    {
      std::cout << "Player wins\n";
    }
  }  
  if (computer_option == 2)
  {
    if (player_option == 0)
    {
      std::cout << "Player wins\n";
    }
    if (player_option == 1)
    {
      std::cout << "Computer wins\n";
    }
    if (player_option == 2)
    {
      std::cout << "Draw\n";
    }
  } 
}
```
One thing about programming games is that all the possibilities must be considered and then coded.

# Random (extended)
If the game is run several times, the game is going to work correctly but all the times the computer will choose the same option. Why? it is because of the random. A computer can not take a "random" number, so it uses some mechanisms to choose a random number. This mechanism is always the same so it is going to get the same result always.

To get a "real", or at least a different random number each time, we need to include another line. ```std::srand(std::time(0))```. This will change some values used by computer to get a random number, and as what is used is the current time it will change each second.

To be able to use the time function be need to include the library where the time function is ```#include <ctime>```.

# Functions (Extended)
One of the main purposes of functions is to reuse code. The code used up to now duplicate a lot of code. Duplicate code is a bad habit while programming, it is better to avoid this.

Following functions are going to be introduced:
* ResultDraw
* ResultCommputer
* ResultPlayer
  
These functions will show the final message.

```c++
#include <iostream>
#include <cstdlib>
#include <ctime>

void ResultDraw()
{
  std::cout << "Draw\n";
}

void ResultComputer()
{
  std::cout << "Computer wins\n";
}

void ResultPlayer()
{
  std::cout << "Player wins\n";
}

int main() {
  std::srand(std::time(0));
  int computer_option = rand() % 3; // will provide a number between 0 and 2
  int player_option;
  // Messages with the instructions of the game
  std::cout << "ROCK, PAPER SCISSORS GAME!!\n";
  std::cout << "Try to beat me, choose an option between 0 and 2\n";
  std::cout << "0 - Rock\n";
  std::cout << "1 - Paper\n";
  std::cout << "2 - Scissors\n";
  // Get the user option
  std::cin >> player_option;

  std::cout << "Computer chose: " << computer_option << "\n";
  std::cout << "Player chose: " << player_option << "\n";

  // Check all posibilities
  if (computer_option == 0)
  {
    if (player_option == 0) ResultDraw();
    if (player_option == 1) ResultPlayer();
    if (player_option == 2) ResultComputer();
  }
  if (computer_option == 1)
  {
    if (player_option == 0) ResultComputer();
    if (player_option == 1) ResultDraw();
    if (player_option == 2) ResultPlayer();
  }  
  if (computer_option == 2)
  {
    if (player_option == 0) ResultPlayer();
    if (player_option == 1) ResultComputer();
    if (player_option == 2) ResultDraw();
  } 
}
```

Now if we want to change one of these messages be only need to change it once not three times.

At this point the program prints the option chosen by computer and player using a number instead of using the word that matches the code. Adding a function to print the option chosen instead of just printing a number is the next step.

```c++
#include <iostream>
#include <cstdlib>
#include <ctime>

void ResultDraw()
{
  std::cout << "Draw\n";
}

void ResultComputer()
{
  std::cout << "Computer wins\n";
}

void ResultPlayer()
{
  std::cout << "Player wins\n";
}

void PrintOption(int option)
{
  if (option == 0) std::cout << "Rock\n";
  if (option == 1) std::cout << "Paper\n";
  if (option == 2) std::cout << "Scissors\n";
}

int main() {
  std::srand(std::time(0));
  int computer_option = rand() % 3; // will provide a number between 0 and 2
  int player_option;
  // Messages with the instructions of the game
  std::cout << "ROCK, PAPER SCISSORS GAME!!\n";
  std::cout << "Try to beat me, choose an option between 0 and 2\n";
  std::cout << "0 - Rock\n";
  std::cout << "1 - Paper\n";
  std::cout << "2 - Scissors\n";
  // Get the user option
  std::cin >> player_option;

  std::cout << "Computer chose: "; 
  PrintOption(computer_option);
  std::cout << "Player chose: ";
  PrintOption(player_option);

  // Check all posibilities
  if (computer_option == 0)
  {
    if (player_option == 0) ResultDraw();
    if (player_option == 1) ResultPlayer();
    if (player_option == 2) ResultComputer();
  }
  if (computer_option == 1)
  {
    if (player_option == 0) ResultComputer();
    if (player_option == 1) ResultDraw();
    if (player_option == 2) ResultPlayer();
  }  
  if (computer_option == 2)
  {
    if (player_option == 0) ResultPlayer();
    if (player_option == 1) ResultComputer();
    if (player_option == 2) ResultDraw();
  } 
}
```

Other common use of functions is reducing complexity. As we can aisolate code in a function we can remove it from the main program. So our main program is going to be more clear and readable.

```c++
#include <iostream>
#include <cstdlib>
#include <ctime>

void ResultDraw()
{
  std::cout << "Draw\n";
}

void ResultComputer()
{
  std::cout << "Computer wins\n";
}

void ResultPlayer()
{
  std::cout << "Player wins\n";
}

void PrintOption(int option)
{
  if (option == 0) std::cout << "Rock\n";
  if (option == 1) std::cout << "Paper\n";
  if (option == 2) std::cout << "Scissors\n";
}

void EvaluateResult(int computerOption, int playerOption)
{
  std::cout << "Computer chose: "; 
  PrintOption(computerOption);
  std::cout << "Player chose: ";
  PrintOption(playerOption);

  // Check all posibilities
  if (computerOption == 0)
  {
    if (playerOption == 0) ResultDraw();
    if (playerOption == 1) ResultPlayer();
    if (playerOption == 2) ResultComputer();
  }
  if (computerOption == 1)
  {
    if (playerOption == 0) ResultComputer();
    if (playerOption == 1) ResultDraw();
    if (playerOption == 2) ResultPlayer();
  }  
  if (computerOption == 2)
  {
    if (playerOption == 0) ResultPlayer();
    if (playerOption == 1) ResultComputer();
    if (playerOption == 2) ResultDraw();
  } 
}

int main() {
  std::srand(std::time(0));
  int computer_option = rand() % 3; // will provide a number between 0 and 2
  int player_option;
  // Messages with the instructions of the game
  std::cout << "ROCK, PAPER SCISSORS GAME!!\n";
  std::cout << "Try to beat me, choose an option between 0 and 2\n";
  std::cout << "0 - Rock\n";
  std::cout << "1 - Paper\n";
  std::cout << "2 - Scissors\n";
  // Get the user option
  std::cin >> player_option;

  EvaluateResult(computer_option, player_option);
}
```

we have already finish the game, but at this point the game is too short, what about makeing a larger game? what about the best of 5? To do that we only need to make a loop that repeats 5 times (in this sample). As we have encapsulated the lgic of the resolution in a function, it s going to be easy to create the loop.

```c++
int main() 
{
  std::srand(std::time(0));
  int computer_option = rand() % 3; // will provide a number between 0 and 2
  int player_option;
  int number_of_tries = 5; // New variable to control the tries

  for (int i = 1; i <= number_of_tries; i++)
  {    
    computer_option = rand() % 3; 
    // Messages with the instructions of the game  
    std::cout << "ROCK, PAPER SCISSORS GAME!!\n";
    std::cout << "Try to beat me, choose an option between 0 and 2\n";
    std::cout << "0 - Rock\n";
    std::cout << "1 - Paper\n";
    std::cout << "2 - Scissors\n";
    // Get the user option
    std::cin >> player_option;
  
    EvaluateResult(computer_option, player_option);
  }
}
```

The ```for``` loop is another way to do loops. This type of loops follow the same structure as all loops: initialization, evaluation, update. This structure is integrated in the syntax of the loop. It has 3 parts:
1. Initialization: executed once before starting
2. Evaluation: evaluated each loop, if it is true continue the loop.
3. update: update values each step.
   
Although all the loops can be done using a while or a for, the for loop is a good loop if we want to repeat a block of code a number of times, because thanks to the syntactic structure of the for, it is more readable than a while loop.

Now, our game asks 5 times for an input and provides the result each time. But the game is not providing a final result.

# Arrays
An array is an aggregated data type. It means that it is not going to store just one variable, but a collection of variables that are called elements. Remember when we used a ```char name[10]``` to store our name. That was an array of 10 elements of type char.

To provide the game bit more functionality an array of integers is going to be added, indeed two arrays are going to be added, one array is going to store the options of the computer and the other one is going to store the options of the player. After the game finishes the loop, all the information is going to be stored and can be used to provide the result of all the game.

```c++
int main() {
  std::srand(std::time(0));
  int computer_option; // will provide a number between 0 and 2
  int player_option;
  int number_of_tries = 5; // New variable to control the tries
  // Declaration of the arrays
  int player_options[5];
  int computer_options[5];

  for (int i = 1; i <= number_of_tries; i++)
  {   
    computer_option = rand() % 3;     
    // Messages with the instructions of the game  
    std::cout << "ROCK, PAPER SCISSORS GAME!!\n";
    std::cout << "Try to beat me, choose an option between 0 and 2\n";
    std::cout << "0 - Rock\n";
    std::cout << "1 - Paper\n";
    std::cout << "2 - Scissors\n";
    // Get the user option
    std::cin >> player_option;

    // options are stored in the arrays
    player_options[i-1] = player_option;
    computer_options[i-1] = computer_option;
    
    EvaluateResult(computer_option, player_option);
  }
  // Include the result summary : TODO
}
```
Check the declaration of the arrays and how the information is stored inside the loop. To access the elements of the array an index is used, so the acces is to the element [index] of the array "identifier". In the sample ```player_options[i-1] = player_option;``` the element at the index i-1 (the indexes of the array starts with 0) of the array "player_options" is going to store the value of the variable "player option". Same is going to happen with computer option.

The only thing left to finish the game is to include a result summary. To do that, all the rounds must be evaluated and check who is the winer. To evaluate the results, the arrays must be "traveled", all the values must be checked, so a new loop is neede.

```c++
int main() {
  std::srand(std::time(0));
  int computer_option; // will provide a number between 0 and 2
  int player_option;
  int number_of_tries = 5; // New variable to control the tries
  // Declaration of the arrays
  int player_options[5];
  int computer_options[5];

  for (int i = 1; i <= number_of_tries; i++)
  {   
    computer_option = rand() % 3;     
    // Messages with the instructions of the game  
    std::cout << "ROCK, PAPER SCISSORS GAME!!\n";
    std::cout << "Try to beat me, choose an option between 0 and 2\n";
    std::cout << "0 - Rock\n";
    std::cout << "1 - Paper\n";
    std::cout << "2 - Scissors\n";
    // Get the user option
    std::cin >> player_option;

    // options are stored in the arrays
    player_options[i-1] = player_option;
    computer_options[i-1] = computer_option;
    
    EvaluateResult(computer_option, player_option);
  }
  // Include the result summary
  std::cout << "\nFINAL RESULTS!! \n";
  for (int i = 1; i <= number_of_tries; i++)
  {
    std::cout << "Round : " << i << "\n";
    EvaluateResult(computer_options[i-1], player_options[i-1]);
  }  
}
```

# Global Variables
To know who is the winner we need to count the number of wins of each. The evaluation of the result is done inside a function, so outside the function there is no way to control the result.

To control the result, the number of wins of computer or player, a variable that can be accesed inside the function and outside the function is needed. That type of variables are the global variables. They are variables that can be accessed anywhere in the program. 

```c++
#include <iostream>
#include <cstdlib>
#include <ctime>

int player_wins = 0;
int computer_wins = 0;

void ResultDraw()
{
  std::cout << "Draw\n";
}

void ResultComputer()
{
  std::cout << "Computer wins\n";
  computer_wins++;
}

void ResultPlayer()
{
  std::cout << "Player wins\n";
  player_wins++;
}

void PrintOption(int option)
{
  if (option == 0) std::cout << "Rock\n";
  if (option == 1) std::cout << "Paper\n";
  if (option == 2) std::cout << "Scissors\n";
}

void EvaluateResult(int computerOption, int playerOption)
{
  std::cout << "Computer chose: "; 
  PrintOption(computerOption);
  std::cout << "Player chose: ";
  PrintOption(playerOption);

  // Check all posibilities
  if (computerOption == 0)
  {
    if (playerOption == 0) ResultDraw();
    if (playerOption == 1) ResultPlayer();
    if (playerOption == 2) ResultComputer();
  }
  if (computerOption == 1)
  {
    if (playerOption == 0) ResultComputer();
    if (playerOption == 1) ResultDraw();
    if (playerOption == 2) ResultPlayer();
  }  
  if (computerOption == 2)
  {
    if (playerOption == 0) ResultPlayer();
    if (playerOption == 1) ResultComputer();
    if (playerOption == 2) ResultDraw();
  } 
}

int main() {
  std::srand(std::time(0));
  int computer_option; // will provide a number between 0 and 2
  int player_option;
  int number_of_tries = 5; // New variable to control the tries
  // Declaration of the arrays
  int player_options[5];
  int computer_options[5];

  for (int i = 1; i <= number_of_tries; i++)
  {   
    computer_option = rand() % 3;     
    // Messages with the instructions of the game  
    std::cout << "ROCK, PAPER SCISSORS GAME!!\n";
    std::cout << "Try to beat me, choose an option between 0 and 2\n";
    std::cout << "0 - Rock\n";
    std::cout << "1 - Paper\n";
    std::cout << "2 - Scissors\n";
    // Get the user option
    std::cin >> player_option;

    // options are stored in the arrays
    player_options[i-1] = player_option;
    computer_options[i-1] = computer_option;
    
    EvaluateResult(computer_option, player_option);
  }
  // Include the result summary
  std::cout << "\nFINAL RESULTS!! \n";
  if (player_wins > computer_wins)
  {
    std::cout << "YOU WIN!!!!\n";
    std::cout << "CONGRATULATIONS\n";
  }
  if (computer_wins > player_wins)
  {
    std::cout << "Computer wins. Best luck next time.\n";
  }

  std::cout << "These are the results of each game:\n";
  for (int i = 1; i <= number_of_tries; i++)
  {
    std::cout << "Round : " << i << "\n";
    EvaluateResult(computer_options[i-1], player_options[i-1]);
  }  
}
```

# Expand your game
To expand this game we can be expanded including the following changes:
## Use a Math formulae
Change the way the winner is determined using a math formulae instead of unsing a serie of conditionals.
## Rock, Paper, Scissors, Lizard, Spock 
This change consist in increasing the number of options from 3 to 5.
## First to get 3 wins
Change the loop to allow the game repeat until one player (or computer) gets 3 wins.
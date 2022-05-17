# Connect 4
- [Connect 4](#connect-4)
  - [Introduction](#introduction)
- [How To Play](#how-to-play)
- [Planning](#planning)
  - [Existing Features](#existing-features)
  - [Features Left to Implement](#features-left-to-implement)
- [Data Model](#data-model)
  - [Logic Flow](#logic-flow)
  - [Libraries Used](#libraries-used)
- [Testing](#testing)
  - [Validator Testing](#validator-testing)
  - [Bugs](#bugs)
- [Deployment](#deployment)
- [Credits](#credits)
  - [Final Notes](#final-notes)

## Introduction

Connect 4 is a strategy game where the idea is to get 4 of your own discs in a line in any direction, horizontally, vertically or diagonally ( -- ¦ / \ ), hence you connect 4 together. You must also block your opponent, Hal (the computer), from connecting 4.

This game is useful for people who spend a lot of time in terminals and allows them to let off steam. They can have a quick game lasting less than a minute, or continue playing until they've beaten Hal, so it's good for somebody to play whether they only have a free moment or lots of time to spare.

A deployed version may be found here: [Connect 4](https://my-connect-4.herokuapp.com/)

![Connect 4](https://github.com/MadStu/connect-4/raw/main/assets/images/web-page.png)

# How To Play

When you load the game, please type "i" and hit enter to read the instructions. This will show you an example of how to win.

Or to skip the instructions type "p" for play!

Once you've entered your name and have chosen your difficulty level you'll be shown a game board with a number of columns.

You go first by entering the column number in which you'd like to drop your disc. Your discs are represented by the letter "O".

Your opponent is named Hal and his discs are represented by the letter "X". You'll take it in turns with Hal to drop your discs into the columns and the first player to connect 4 (to get 4 discs in a line) wins that game!

You'll then move to the next level and the board will narrow making the game slightly harder each time you level up.!

If you get down to a board which is only 4 columns wide, and you win, then you win the whole game!

Max points are given to you on each level, the number of points depends which level you're on and which difficulty setting you have. Hard mode gives you double the points!

Each move you make decreases your points total, so the least amount of moves it takes to win, the more points you'll keep!

There is a cheat code you could use, I'm sure you'll find it if you look hard enough through this documentation, but be warned, it comes at a cost!

Good luck and happy connect 4-ing!

<sup>PS. Will you find the easter eggs?</sup>

# Planning 

I planned to make a python game that could run in any python3 terminal window and be challenging enough for the player to want to return to the game again and again.

Connect 4 was a game I thought could meet the criteria I was looking for and could easily be represented within a text based GUI.

Before writing any code I first built a flow chart to map out where it needed to start, where it needed to go and how it would end.

This helped massively at the beginning of the project to get the ball rolling and I used it to build the initial basic functioning game loop which everything since has been based upon.

![Flow Chart](https://github.com/MadStu/connect-4/raw/main/assets/images/flow-chart.png)

## Existing Features

- __Text Based GUI__

  - The game's GUI is entirely text based and can be run directly in any python3 terminal.

![Text Based GUI](https://github.com/MadStu/connect-4/raw/main/assets/images/text-based-gui.png)

- __New Gameplay Concept__

  - The regular version of the game is 6 columns tall and 7 columns wide. This game starts you on level 1 which is 12 columns wide. This makes it easier as you have more space to win.
  - Every time you win a game, you move up a level and the column width is shortened.

![New Gameplay Comcept](https://github.com/MadStu/connect-4/raw/main/assets/images/new-game-concept.png)

- __Hard Mode__

  - The game features a hard mode allowing the player to play against a much smarter version of Hal.
  - This gives the player a real sense of achievement when they win. 

![Hard Mode](https://github.com/MadStu/connect-4/raw/main/assets/images/hard-mode.png)

- __Animated Disc Drop__

  - Basic animation is included which shows both player discs falling as they're dropped into the column which helps towards giving the user a positive emotional response.

![Animated Disc Drop](https://github.com/MadStu/connect-4/raw/main/assets/images/animated-disc-drop.png)

- __Status Bar__

  - A status bar keeps the player informed with their current level, what game difficulty they're playing, who's turn it is and what their score is.

![Status Bar](https://github.com/MadStu/connect-4/raw/main/assets/images/status-bar.png)

- __Input Validation__

  - All input from the user is validated, whether asking if they want to play hard mode, play again and also the column number they enter.

![Input Validation](https://github.com/MadStu/connect-4/raw/main/assets/images/input-validation.png)

- __Coloured Winning Discs__

  - When either the user or Hal wins, the winning discs are highlighted red to show the line of connect 4.

![Coloured Winning Discs](https://github.com/MadStu/connect-4/raw/main/assets/images/coloured-winning-discs.png)

- __Cheat Code__

  - The game includes a cheat code (88) which may give a hint to the player of the next column to try.
  - If Hal hasn't found a potentially winning pattern the player is instead shown a message that cheats never prosper.
  - There is a penalty for using the cheat code in terms of lost points.

![Cheat Message](https://github.com/MadStu/connect-4/raw/main/assets/images/cheat-message.png)

- __Score Board__

  - A score board shows the player the top ten scores.
  - The player scores are kept in a local .csv file so the top scores are saved permanently.

![Score Board](https://github.com/MadStu/connect-4/raw/main/assets/images/score-board.png)

- __Personalised Messages__

  - A 3 letter name is used to maintain text length and spacing consistency. It also harks back to top scores on retro arcade games producing a feeling of nostalgia and happiness.
  - The players 3 letter name is used in messages throughout the game.

![Players Name](https://github.com/MadStu/connect-4/raw/main/assets/images/big-name.png)

## Features Left to Implement

- Add AI that learns and predicts the players next move based on their previous pattern of moves.
- Make the Easy mode opponent easier to beat.

# Data Model

The run.py file includes user configurable options at the top of the file

All the mutable game data is held within the Game class and is updated after every move. The main playing board is kept in the Game.db list and is a list of lists. Each list within Game.db is 1 game column starting from left to right.

## Logic Flow

- The program begins by calling the welcome() function which displays the logo and asks the user if they'd like to begin playing or want to read the instructions first.

- Input is validated and if the user wants to read the instructions, then that slide show of instructional screens is shown before rejoining the flow.

- The user is asked to input a 3 letter name, it's displayed back to the them and they then confirm or reject what was entered before moving on.

- The top 10 scores are then briefly shown before the main game board is loaded, including the logo and status bar.

- Maximum points are granted to the user based upon the amount of free squares in that board size, user level and whether they're playing in hard mode.

- A column number is then requested for input with error feedback given if the user does not enter an integer, or if their column choice doesn't fall within the range available (depending on active number of columns).

- If that input is valid, the next check is to see if the requested column is available. The user is told if the column is full and requested to input again.

- Once a valid input and a free column is chosen, the animation of the disc drop is called. The animation also actively checks with each frame to see if the next square down is the bottom of the column.

- When the disc has reached the bottom, there is then a check to see if there is a connect 4 winner. This same function also checks for 3 in a line of 4, and if in hard mode, 2 in a line of 4 discs which have the potential of winning.

- If there is a 2 or 3 potential winner, then the free squares are checked to see if it has a support disc underneath it (not an empty square under the potential winning square).

- If the empty square is found to have a supporting square then Hal (the computer player) remembers that column for his next move.

- Points are now deducted from the user's current score. Every move they make will deduct the configurable BASE_POINTS multiplied by the current user level (then multiplied by 2 if in hard mode). Example if BASE_POINTS = 2, you're on level 3 and you're playing in hard mode, the points deducted per move would be 12 ((2 * 3) * 2).

- The updated game board with current points are displayed.

- The active player is then switched and the computer is called upon to take a turn.

- Hal will then choose a random column unless a column has already been flagged as a potential connect 4.

- Hal's turn then goes through the same process as the user. Checking if the column is empty, the disc animation, checking for the bottom, checking for winning lines and updating any potential connect 4's before handing back control to the user.

- Users also have the option of using a cheat code. If they enter "88" as the column number then one of the following actions will be taken.
  - If there hasn't been any potentially winning connect 4 lines:
    - User is told that cheats never prosper.
    - Points are deducted from the user total.
  - If a potential column HAS been found:
    - User is told that column.
    - Points are deducted from the user total.

- The game loop continues until 1 of 3 things happens:
  - Player Wins
    - At this point the players current score is saved.
    - The game level increases by 1.
    - The board width decreases by 1.
    - The current level is checked to see if they have beaten the whole game (see below).
    - User is shown the top scores board and asked if they'd like to play again.
      - If they say yes they continue on to the next level.
      - If they say no the score is saved in the top scores board (if score is high enough) and the program is quit.
  - Computer Wins
    - The user score is reset to their previously saved score and is saved in the top scores board (if score is high enough).
    - User is shown the top scores board and asked if they'd like to play again.
      - If they say yes the whole board is reset and they start from the beginning.
      - If they say no the program is quit.
  - It's a Draw
    - The user score is reset to their previously saved score.
    - User is shown the top scores board and asked if they'd like to play again.
      - If they say yes they continue and play the same level again.
      - If they say no the score is saved in the top scores board (if score is high enough) and the program is quit.

- If the user is found to have beaten the whole game, the following happens:
  - Top score board is updated(if they reached high enough points).
  - Congratulatory message is shown.
  - User is asked if they'd like to play again.
    - If they say yes the whole board is reset, user is asked the game difficulty level they want and they start from the beginning.
    - If they say no the program is quit.

## Libraries Used

I have used the following libraries:
- __os__
  - "system" and "name" are used for clearing the screen.
- __time__
  - "sleep" is used for delaying the display of text, game boards and the disc drop animation.
- __random__
  - "randint" is used for the computer to choose a random column between 1 and whatever the current board width is.
- __math__
  - "floor" is used to make sure calculated points are rounded down to an integer.
- __csv__
  - "open" is used to read and write to a .csv file for saving the top scores.
- __sys__
  - "setrecursionlimit" is used to change the recursion limit to a higher number than is standard. This is due to the high number of checks the computer has to make when looking for a potentially winning connect 4.

# Testing

I've tested the code continuously as I've developed it, making sure all functionality works as it should and fix any typos or coding errors as and when they happen.

I also asked friends and family to play with and try to produce errors or unintended behaviours.

Some feedback I had was that the computer was too hard to beat on Easy mode so I plan to make that mode a little easier.

I also wrote a couple of extra dev codes in for testing purposes:

- Typing "999" into the column entry section will quit the program cleanly so I could quit and retest things over and over after making small changes. Making testing as I go a whole lot easier.
- Typing "22222" into the column entry section increases your game level up to the winning level so that I could test the behaviour when the user wins the game.

These dev codes can be disabled by changing the DEV_MODE to False in the configuration area at the top of run.py.

## Validator Testing 

- PEP8
  - No errors or warnings were returned when passing through [PEP8online.com](http://pep8online.com/).

## Bugs

- ~~herokuapp.com not displaying underscores on the logo.~~
  - Solved by making the logo art text have a lighter weight.
- ~~Game would say there's a winner if it was a tie.~~
  - Solved by adding a disc counter.
- ~~Computer finds the next move to beat the player, but if the player goes there, the computer would still place disc in the same column.~~
  - Solved by checking all discs after a move and not just the previous players.
- ~~Computer would ignore it's own potential win, prioritising blocking the player.~~
  - Solved by: 
    - Having the computer check it's own discs after the players.
    - Prioritising discs with 3 in a row over discs with 2 in a row.
- ~~Computer would try to block players by placing discs in the next column, but the square under where the winning disc would go is empty so the disc just falls past.~~
  - Solved by checking to see if the square underneath is empty.
- ~~Checking the square underneath could produce an IndexError as it wouldn't exist.~~
  - Solved by using a Try/Except block to handle it.
- ~~Recursion Error when the program is checking winners and checking for next computer move.~~
  - Solved by increasing the recursion limit.
- ~~IndexError when resetting game after player has reached top level.~~
  - Solved by adding if else in the reset_game function. It now checks to see if the level was at the top level or not.
- ~~Game difficulty not changing mode when the player selects a different setting after winning at top level.~~
  - Solved, I'd missed adding the setting in the choose_mode function as the default mode was "easy" and only changed when player set mode to "hard".
- ~~Score increments highly when you input invalid data when choosing difficulty mode before game starts.~~
  - Solved by removing the call to reset_game which is no longer required there.
- ~~Scoreboard updates twice when player completes the game and doesn't continue playing.~~
  - Solved by checking the game level within the play_again function.

# Deployment

I've deployed it on herokuapp.com and used the following method.

- The connect4 game can be deployed to herokuapp.com using the web interface terminal template in this repository. The steps to deploy are as follows: 
    - Sign up or log in to GitHub.com.
    - Navigate to this repository page at https://github.com/MadStu/connect-4.
    - Press the "Fork" button which will make a copy of this connect-4 repository in your own account.
    - Sign up or log in to herokuapp.com.
    - Click "New" then "Create new app".
    - Enter an app name, choose your region and then click "Create app".
    - On the next page, go to the Settings Tab.
    - Click on "Add buildpack" and add the python build pack first, then save changes.
    - Click on "Add buildpack" again and add the nodejs build pack for the web interface to work. Be sure these 2 are in that order, Python first.
    - Click on the Deploy tab at the top, select GitHub and connect to your GitHub account.
    - Search for the repository name (connect-4) and click the "Connect" button.
    - Scroll down to the Manual deploy section and choose the main branch to deploy from.
    - Click the "Deploy Branch" button which syncs the herokuapp.com files with the repository.

You can also deploy to your own systems.

- If you wish to deploy within your own Python3 environment:
    - Download or copy the contents of run.py and scores.csv to your own system.
    - make sure the scores.csv has writeable permissions.
    - Run the game by typing: ***__python3 run.py__***

# Credits 

- First and foremost, the original Connect 4 game concept was invented in 1973 by Howard Wexler.
- I used the Code Institute web interface terminal template to deploy the program which is here: https://github.com/Code-Institute-Org/python-essentials-template
- I initially used the check_winner function from https://github.com/justinvallely/Python-Connect-4/blob/master/connect4.py (Line 69).
- I learned how to clear the terminal screen from this tutorial: https://www.geeksforgeeks.org/clear-screen-python/
- I learned how to work with .csv files from this website: https://www.pythontutorial.net/python-basics/python-read-csv-file/
- I got the Connect 4 logo text from this website: https://patorjk.com/software/taag/#p=display&f=Doom&t=Connect%204
- I made the flowchart by using this website: https://online.visual-paradigm.com/
- I often used [W3Schools](https://www.w3schools.com/python/) and [docs.python.org](https://docs.python.org/) as a guide for finding the best solutions and using the code in the correct format.
- I'd also search google which more often than not would show solutions written on [stack overflow](https://stackoverflow.com/).
- I used a royalty free image of an old computer from: https://www.pikpng.com/
- I included quotes from 2001: A Space Odyssey by Arthur C. Clarke.
- I included a quote from The Hitchhiker's Guide to the Galaxy by Douglas Adams.

## Final Notes

I started this project as complete python novice and now I'm at the end I feel like my knowledge and love of python has grown exponentially. And while my skills may not yet be up to it, I know for sure that anything is possible with the right code and in the right order.

It wasn't until I was coming to the end of the project with my python file getting longer and longer that I realised the benefits of using classes over just functions. I do have all of the logic being run within functions but with the deadline approaching I've run out of time to refactor it all into the neat class > function > code heirarchial structure.

I look forward to learning much much more. And to getting better and better with every line of code that I type.

Big thanks to my fellow student [David Bowers](https://www.linkedin.com/in/dnlbowers/) for pointing me in the right direction when it came to writing this readme. I thought I'd finished before he spent his own time to check it over, only to find I'd missed out some crucial information.

I hope anybody who plays this game will find it both enjoyable and challenging. Challenge your friends to beat your high score!

Happy Gaming! :)

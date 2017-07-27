+++
date = "2017-07-26"
title = "Developing an AI for a 5600 Year Old Board Game"

keywords = ["ai", "boardgame", "c#", 'unity']
categories = ["projects"]
+++

For my senior project in college, my partner and myself decided to implement [The Royal Game of Ur](https://en.wikipedia.org/wiki/Royal_Game_of_Ur). The Royal Game of Ur is a two player board game found in the Royal Tomb of Ur in Iraq. It is considered the second oldest game with estimates saying it existed before 2600 BC. Historians suggest the oldest to be the Egyptian game [Senet](https://en.wikipedia.org/wiki/Senet). The Royal Game of Ur incorporates both strategy and luck. Because of the stochastic nature of the gameplay, we believed it would be a good challenge for AI development as it will have to incorporate a good balance of game theory as well as decision making.

![Royal Game Of Ur](/board.jpg "The Board")

## The Royal Game of Ur Rules

The game is played by 2 players. The goal is to get their 7 game pieces to the end of the board before the other player. Each turn the player rolls four 4-sided dice. The dice has two *1s* and two *0s* so it ends up being equivalent to flipping 4 coins.

![Piece Movement](/piece-movement.jpg "Piece Movement")

Each roll, you can move a single piece the sum of your dice. You can move to a free spot or *capture* an opponent piece by landing on it. Additionally there is five *rosette* tiles which are both safe spaces as well as grant the player an additional roll.

![Rosette Location](/rosette-locations.jpg "Rosette Locations")

## AI Approach

For the project I used a variation of the [Minimax](https://en.wikipedia.org/wiki/Minimax) algorithm called [Expectiminimax](https://en.wikipedia.org/wiki/Expectiminimax_tree). This aversion varies from the original algorithm in that incorporates probability.

![Minimax Demonstration](/minimax-demonstration.jpg "Minimax Demonstration")

Minimax works on the theory that each player is trying to maximize there own score. For each turn of the AI it creates a tree of possible board *states* for a predetermined amount of turns. For this game there is no official score for a board so I created my own. This is called an [Evaluation Function (Or heuristic)](https://en.wikipedia.org/wiki/Evaluation_function). For our game the function looked like the below.

![Board Evaluation Function](/ai-board-evaluation.jpg "Board Evaluation Function")

It simply takes the sum of all the tile positions of your pieces and subtracts the sum of all the tile positions of your opponent. The evaluation function greatly determines the personality of your AI. It is much more an art then a science to create one. For this game I focused on having the AI get to rosette tiles and safe tiles. Because the first four tiles have a higher values than the next few tiles it encourages the AI to stay in the safe row until it either can't or it is worth capturing an opponent piece. The tile value increases as it moves along the path to encourage the AI to move towards the end. Finally having a piece finish the path is worth much more than all else because ultimately that is the most important goal of the game.

Because the game is [Stochastic (random)](https://en.wikipedia.org/wiki/Stochastic) we had to use Expectiminimax. This varies from traditional Minimax in that each nodes utility is multiplied by its probability. The pseudocode for this algorithm is available on its Wikipedia page.

[Feel free to look through my code here](https://github.com/chevalierc/RoyalGameOfUr)

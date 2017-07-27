+++
date = "2017-05-24"
title = "Developing Chess in the Unity game engine"

keywords = ["ai", "chess", "c#", 'unity']
categories = ["projects"]
+++

For my senior project in college, my partner and myself decided to implement [The Royal Game of Ur](https://en.wikipedia.org/wiki/Royal_Game_of_Ur) with the major focus being on exploring different AI techniques within the board game. The Royal Game of Ur is a two player board game found in the Royal Tomb of Ur in Iraq. It is considered the second oldest game with estimates saying it existed before 2600 BC. Historians suggest the oldest to be the Egyptian game [Senet](https://en.wikipedia.org/wiki/Senet). The Royal Game of Ur incorporates both strategy and luck. Because of the stochastic nature of the gameplay, we believed it would be a good challenge for AI development as it will have to incorporate a good balance of game theory as well as decision making.

![Royal Game Of Ur](https://upload.wikimedia.org/wikipedia/commons/thumb/6/61/Bm-royalgame.jpg/1024px-Bm-royalgame.jpg "Royal Game Of ur")

*The Royal game of Ur*

For our project we decided to use the Unity game engine for development. Their were a few reasons for that.

* There are a lot of educational resources available due to its popularity.
* It is a free service (until you hit [$100k in revenue](https://blogs.unity3d.com/2016/06/16/evolution-of-our-products-and-pricing/))
* It has great flexibility in [deployment environments](https://unity3d.com/unity/multiplatform).
* It is scripted in C# which I personally wanted more experience using (You can also use JS).

Before jumping into development of the Game Of Ur, I wanted some experience with the environment. I started by following a few tutorials available on the Unity site. I first followed their [UFO](https://unity3d.com/learn/tutorials/projects/2d-ufo-tutorial) tutorial, then their [Tic-Tac-Toe](https://unity3d.com/learn/tutorials/tic-tac-toe/introduction-and-setting-project?playlist=17111) tutorial and finally their [Rougelike](https://unity3d.com/learn/tutorials/projects/2d-roguelike-tutorial) tutorial. All three tutorials have the benefit that you end up with a fully working game. The tutorials bring you through all of the steps of game development. The Rougelike tutorial specifically had some compatibility issues with the current version of Unity, but they did include a PDF of needed changes. One issue I had with all the tutorials is that they didn't explain all the components they used. Using this [page](https://unity3d.com/learn/tutorials/s/scripting) in conjunction with the tutorials I was able to answer most of my questions.

![Rouge-Like tutorial screenshot](https://unity3d.com/sites/default/files/learn-playlist/icon/2droguelike-thumb1.jpg "Rouge Like")

*An image from the rouge-like tutorial*

After finishing these tutorials, I felt decently comfortable the engine. I certainty did not feel like I knew all the features, but I learned the API is very developer friendly. The components are very well designed and documented making learning on the spot simple.

As a testament to this, after only these 3 tutorials I was able to build a chess game and AI inside the engine. I chose to implement chess because of my own interest in the game as well as its technical similarities to the Royal Game of Ur. I began by simply designing the UI of the game. Unity makes it very easy to draw and render sprites so this wasn't to difficult. Game entities are all represented in unity as Game Objects. Within the game objects you can add components such as Sprite-Renderers, Collision-Detectors and Physic Properties. You can edit these very simply inside the editor as well as from code. The object orientated approach is what makes the engine so simple and fun to use.

![Chess](/chess.gif "Chess Gif")

*As of writing, I only implemented pawns*

Having created the UI first, I inadvertently had already started taking a MVC approach to managing my code. This works out for the best as it greatly simplified my ability to implement the AI logic. For my current AI I simply chose to implement a [Minimax](https://en.wikipedia.org/wiki/Minimax) decision tree. Minimax work on the theory, both players want to maximize there game score while minimizing their opponents. For my chess AI I chose this score to be the sum of the players pieces (Using their [relative values](https://en.wikipedia.org/wiki/Chess_piece_relative_value)) minus the AI's sum. This works fine for my basic example but in a real engine you would want to incorporate other factors such as board position, checkmate possibilities and others.

![Minimax](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e1/Plminmax.gif/400px-Plminmax.gif "Minimax")

*Minimax decision tree*

All in all, I'm happy with this venture. It's always empowering to learn new technologies and I'm excited to mess around more with game development in my spare time.

[Feel free to look through my code here](https://github.com/chevalierc/unity-chess)

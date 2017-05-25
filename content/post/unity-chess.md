+++
date = "2017-05-24"
title = "Developing Chess in the Unity game engine"

keywords = ["ai", "chess", "c#", 'unity']
categories = ["projects"]
+++

For my senior project in college, my partner and myself decided to implement [The Royal Game of Ur](https://en.wikipedia.org/wiki/Royal_Game_of_Ur) with the major focus being on exploring different AI techniques within the board game. The Royal Game of Ur is a two player board game found in he Royal Tomb of Ur. It is considered the second oldest game, second to the Egyptian game [Senet](https://en.wikipedia.org/wiki/Senet). It incorporates both strategy and luck. Because of the stochastic nature of the gameplay, we believed it would be a good challenge for AI development.

![Royal Game Of ur](https://upload.wikimedia.org/wikipedia/commons/thumb/6/61/Bm-royalgame.jpg/1024px-Bm-royalgame.jpg "Royal Game Of ur")

For our project we decided to use the Unity game engine for development. Their were a few reasons for that.

* There are a lot of resources available due to its popularity.
* It is a free resource.
* It has great flexibility in target environments.
* It is scripted in C# which I personally wished to gain experience using.

Before jumping into development of the Game Of Ur, I wanted some experience with the environment. I started by following a few tutorials available on the Unity site. I first followed their [UFO](https://unity3d.com/learn/tutorials/projects/2d-ufo-tutorial) example, then their [Tic-Tac-Toe](https://unity3d.com/learn/tutorials/tic-tac-toe/introduction-and-setting-project?playlist=17111) example and finally their [Rougelike](https://unity3d.com/learn/tutorials/projects/2d-roguelike-tutorial). All three examples have the benefit of concluding with a fully working game. The tutorials bring you through all of the steps of game development. The Rougelike specifically had some compatibility issues with the current version of Unity, but they did include a PDF of needed changes. One issue I had with all the tutorials is they didn't explain all the components they used. Using this [page](https://unity3d.com/learn/tutorials/s/scripting) in conjunction with the tutorials I was able to answer most of my questions.

![Rouge-Like](https://unity3d.com/sites/default/files/learn-playlist/icon/2droguelike-thumb1.jpg "Rouge Like")

After finishing these tutorials, I felt decently comfortable the engine. I most certainty did not feel like I knew or could properly use all the features, but I learned the API is very developer friendly. The components are very well designed and documented.

As a testament to this, after only these 3 tutorials I was able to build to build a chess game and chess AI inside the engine. I chose to implement chess because of my own interest in the game as well as its technical similarities to the Royal Game of Ur. I began by simply designing the UI of the game. Unity makes it very easy to draw and render sprites so this wasn't to difficult. Game entities are all represented in unity as Game Objects. With the game objects you can add components such as Sprite-Renderers, Collision-detection and Physic Properties. You can edit these very simply inside the editor as well as from code. The object orientated approach is what makes the engine so simple and fun to use.

![Chess](/chess.PNG "Rouge Like")

*As of writing, I only implemented pawns*

Having created the UI first, I inadvertently started heading down a MVC approach for my code. This works out for the best as, it greatly simplified my ability to implement the AI logic. For my current AI I simply chose to implement a [Minimax](https://en.wikipedia.org/wiki/Minimax) decision tree. Minimax work on the theory, both players want to maximize there game score while minmizing there opponents. For my chess AI I chose this score to be the sum of the players pieces values(pond = 1, king = 10... etc) minus the AI's sum. This works fine for my basic example but in a real engine you would want to incorporate other factors such as board position, checkmate possibilities and others.

![Minimax](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e1/Plminmax.gif/400px-Plminmax.gif "Minimax")

All in all, I'm happy with this venture. It's nice to learn new things and I'm excited to mess around more with game development in my spare time.

[Feel free to look through my code here](https://github.com/chevalierc/unity-chess)

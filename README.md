# CS-370_Treasure_Hunt_Game

## Describe the steps your intelligent agent is taking to solve this pathfinding problem.

The intelligent agent considers the graph as an 8 x 8 array. Each cell has a row and column value. A variable is declared and assigned to an object instance of Treasure Maze passed with the array. Building the neuro network required a member method call passed with the array. Both instances are passed in a member method call for training the model.

Two hyperparameters are needed (epsilon, number of epochs). Epsilon will be used for the epsilon greedy algorithms in determining if the intelligent agent will explore or exploit from previous episodes. Number of epochs is used to glean insight into how many training episodes it took to train the model.

An Experience Replay object instance is instantiated with the model and max memory size passed as arguments. The replay object list of episodes cannot exceed the max memory. The oldest episode is deleted when the maximum capacity is reached.
My code produced different total number of epochs. It returned 900 epochs on the low end and 1400+ on the top end. A safe estimate is chosen for the number of training episodes. A for loop is used to iterate over the estimated number of training episodes.

At the beginning of the training episodes, a variable declared and assigned to a random choice from an array that contains a list of free cells. An object instance of Treasure Maze calls a member method to reset the maze with a pirate in the specified cell. Another variable is declared and assigned to the current state.

While the Treasure Maze object instance return value from the game status member method is equal to ‘not over’, the following will be repeated. i.	The current state is saved and a conditional statement is used to determine if the intelligent agent will explore or exploit based on our epsilon value.

If a random number is less than epsilon, then the intelligent agent will randomly choose a valid action. If the random number is greater, then the intelligent agent will predict the action from experience.

The Treasure Maze object instance makes a member method call with the chosen action and assigns the attributes to three variables (state, reward, game status). A list is declared and assigned with the three variables plus the previous state. The episode (list) is passed to the experience replay object for sampling during a later training run.

We retrieve the training data from a Game Experience member method call. Then, the model is trained on the inputs and targets returned from the replay object.
The while loop will exit when the game status does not equal not over. This implies that upon completion of the while loop, the intelligent agent either won or lost. The training loops (epochs) increases until the agent achieves a 100%-win rate and pass a completion check.

The intelligent agent starts in random cells and primarily learns from exploitation. It is penalized for revisiting a cell, visiting an occupied cell, or moving outside the graph. Ultimately, the agent will try to find the shortest path to the treasure that maximizes the total reward.

Below is the output showing the pirate finding the treasure:

![image](https://github.com/mwesley8/CS-370_Treasure_Hunt_Game/assets/105822088/de3aba14-8ea6-4c93-8e1e-aa27b565bb4f)

I look forward to learning more during my professional development

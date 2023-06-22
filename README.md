## Dice game: Using Full Value Iteration 

For this assignment, I will be writing an agent that can play a simple dice game. Let me explain the basic rules:

I start with 0 points.
I roll three fair six-sided dice.
Now, I have to make a choice:

Stick: I can accept the values shown. If two or more dice show the same values, they are flipped upside down, where 1 becomes 6, 2 becomes 5, 3 becomes 4, and vice versa. The total of the dice is then added to my points, determining my final score.
OR
Reroll: I can choose to reroll the dice. I have the option to hold any combination of dice on their current values. However, rerolling comes with a cost of 1 point, which means my score may be negative during the game or even at the end.
The best possible score in this game is 18, which can be achieved by rolling either three 1s or two 1s and one 6 on the first roll.

The reroll penalty prevents me from endlessly rolling to attain the best score. If the value of the current dice is higher than the expected value of rerolling them, accounting for the penalty, then I should choose to stick.

The optimal decision is independent of my current score. Whether it's my first roll with a score of 0 or my twentieth roll with a score of -19 (making a positive end score impossible), if I roll three 6s (which only adds 3 points if I stick), I still expect a better end score by rerolling and accepting the penalty. Almost any other roll will surpass it, making it the right choice to maximize my score.

### Agent Implementation
The `ValueIterationAgent` class is responsible for computing the optimal policy using the value iteration algorithm. Here is an overview of the class and its methods:

### Class Initialization
`__init__(self, game)`: Initializes the agent with the game object and sets the values for the discount rate (gamma) and convergence threshold (theta).

### Single Value Iteration Step
`perform_single_value_iteration(self, V)`: Performs a single value iteration step given the current values of V (value function). It returns a new dictionary of values for each state.

### Value Iteration Algorithm
`value_iteration(self, theta=0.001)`: Performs the value iteration algorithm to determine the optimal policy for the game. It returns the optimal value function V and the optimal policy.

### Playing the Game
`play(self, state)`: Given a state, returns the chosen action for that state based on the computed optimal policy. If the agent has not computed a policy yet, it computes the optimal value function and policy using value iteration.

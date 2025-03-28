# Creative Maze Solver

This project implements a maze-solving agent using Q-learning with interactive visualization. It supports random maze generation and training, along with the display of training progress and the final solved path.

## Overview

The code consists of two main parts, each intended to be run in separate code cells (as indicated by "cell 1" and "cell 2" in your prompt).

**Cell 1:** Contains a more advanced version of the `CreativeMazeSolver` class with features like:

* Customizable maze size and wall density.
* Two maze types: random and a predefined challenging zigzag pattern.
* Q-learning with epsilon-greedy action selection and added noise for exploration.
* Enhanced reward system to encourage efficient pathfinding.
* Live interactive visualization of the training process, including the maze, path, reward progress, and Q-value heatmap.
* Final results dashboard showing training rewards, average Q-values, success rate, and training time.
* A `solve()` method to find the optimal path using the trained Q-table.

**Cell 2:** Contains a slightly simpler version of the `CreativeMazeSolver` class that focuses on:

* Generating a random maze with a guaranteed path using Breadth-First Search (BFS) validation.
* Q-learning with epsilon-greedy action selection and adaptive exploration decay.
* Interactive visualization of the training process, showing the maze, path, reward progress, and success rate.
* Final visualizations of training rewards, maximum Q-values, and success per episode.
* Creation of an animation showing the solved path.
* A `solve()` method with loop prevention to find the path using the trained Q-table.

## Getting Started

To use this code, you will need to have the following Python libraries installed:

* `numpy`
* `matplotlib`
* `matplotlib.animation`
* `seaborn`
* `IPython`
* `time`
* `collections`

You can install these libraries using pip:

```bash
pip install numpy matplotlib seaborn ipython
```

## Running the Code

The code is designed to be run in an environment that supports interactive Matplotlib plots and the display of HTML animations, such as Jupyter Notebook or Google Colab.

**For the Enhanced Solver (Cell 1):**

1.  Copy and paste the entire code block for "cell 1" into a code cell in your notebook.
2.  Run the cell. This will initialize the solver, start the training process, and display the live visualization.
3.  Once the training is complete, final result plots and a summary will be shown.

You can customize the solver by modifying the parameters when creating an instance of `CreativeMazeSolver`:

```python
solver = CreativeMazeSolver(size=9, wall_density=0.35, maze_type="random") # Example customization
```

* `size`: The dimension of the maze (e.g., 7 for a 7x7 maze).
* `wall_density`: The probability of a cell being a wall in a random maze (between 0 and 1).
* `maze_type`: Either `"random"` for a randomly generated maze or `"predefined"` for a challenging zigzag maze.

You can also adjust the training parameters in the `solver.train()` call:

```python
solver.train(episodes=300, update_freq=15) # Example training customization
```

* `episodes`: The number of training episodes.
* `update_freq`: How often (in episodes) the visualization is updated.

**For the Validated Maze Solver with Animation (Cell 2):**

1.  Copy and paste the entire code block for "cell 2" into a separate code cell in your notebook.
2.  Run the cell. This will initialize the solver with a validated random maze, start the training, and display the live visualization.
3.  After training, final result plots will be shown, followed by an animation of the solved path.

You can customize the solver in this version as well:

```python
solver = CreativeMazeSolver(size=7, wall_density=0.3) # Example customization
```

* `size`: The dimension of the maze.
* `wall_density`: The probability of a cell being a wall.

The training episodes can be adjusted in the `solver.train()` call:

```python
solver.train(episodes=200) # Example training customization
```

## Code Description

**Cell 1 (Enhanced Solver):**

* **`CreativeMazeSolver` Class:**
    * `__init__`: Initializes the maze, Q-table, actions, learning parameters, and visualization setup.
    * `generate_maze`: Creates a maze (random or predefined).
    * `is_valid`: Checks if a given state is within the maze boundaries and not a wall.
    * `step`: Simulates taking an action and returns the next state, reward, and a boolean indicating if the goal is reached.
    * `choose_action`: Selects an action using an epsilon-greedy strategy with added noise.
    * `train`: Trains the Q-learning agent over a specified number of episodes, updating the visualization periodically.
    * `update_visualization`: Updates the live plots showing the maze, path, reward progress, and Q-value heatmap.
    * `show_final_results`: Displays final plots of training rewards, average Q-values, success rate, and training time.
    * `solve`: Uses the trained Q-table to find the optimal path from start to goal.

**Cell 2 (Validated Maze Solver with Animation):**

* **`CreativeMazeSolver` Class:**
    * `__init__`: Initializes the maze with a validated path, Q-table, actions, learning parameters, and visualization setup.
    * `_setup_visualization`: Sets up the Matplotlib figure and axes for interactive plotting.
    * `generate_valid_maze`: Generates a random maze and uses BFS to ensure a path exists between the start and goal.
    * `_bfs_path_exists`: Performs Breadth-First Search to validate path existence.
    * `is_valid`: Checks if a given state is within the maze boundaries and not a wall.
    * `step`: Simulates taking an action and returns the next state, reward, and a boolean indicating if the goal is reached. Uses distance-based reward shaping.
    * `choose_action`: Selects an action using an epsilon-greedy strategy with adaptive exploration decay.
    * `train`: Trains the Q-learning agent over a specified number of episodes, updating the visualization periodically.
    * `_update_visualization`: Updates the live plots showing the maze, path, reward progress, and success rate.
    * `_show_final_results`: Displays final plots of training rewards, maximum Q-values, and success per episode.
    * `_create_path_animation`: Creates and displays an animation of the solved path.
    * `solve`: Uses the trained Q-table to find a path from start to goal, with loop prevention.

## Customization

You can further customize the behavior of the maze solver by adjusting various parameters within the code, such as the learning rate, discount factor, exploration rate decay, and reward values.

Enjoy exploring the creative maze solver!
```
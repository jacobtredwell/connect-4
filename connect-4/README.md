# Connect4 Human vs AI Game

This repository contains a simple implementation of the classic **Connect Four** game where a human can play against another human or an AI opponent directly in the terminal.

## Overview

The goal of Connect Four is to be the first player to form a horizontal, vertical, or diagonal line of four of one's own tokens on a 6×7 grid. In this implementation:

* The game board is represented by a 2‑D list of strings, with `"X"` and `"O"` denoting the two players’ tokens and `"."` indicating an empty slot.
* Players take turns choosing a column (1–7) into which to drop their token. Tokens fall to the lowest available row in the chosen column.
* The program supports both **human vs. human** and **human vs. computer** modes. When playing against the computer, the AI uses a simple heuristic to decide where to play.

## Running the Game

This program requires Python 3.7 or later. There are no third‑party dependencies beyond the standard library.

To run the game:

```bash
python3 connect4_human_vs_ai.py
```

Follow the on‑screen prompts to choose whether you want to play against another human or the computer, and who goes first. Input column numbers (1–7) when prompted.

### Example Game Play

1. The program renders an empty board and asks you to choose a mode (human vs. human or human vs. computer).
2. In human vs. computer mode, you decide whether the human or computer plays first.
3. Each turn, the current player selects a column; the board updates and is displayed.
4. The game ends when a player connects four or the board fills up and results in a draw.

## AI Strategy

The AI uses a basic heuristic consisting of three steps:

1. **Winning Move:** It first simulates each legal move to see if any will immediately win the game. If so, it chooses that column.
2. **Blocking Move:** If the human can win on their next turn, the AI simulates those moves and chooses a column to block the human’s winning opportunity.
3. **Center Bias:** If no immediate win or block is necessary, the AI prefers columns closer to the center of the board (column 4), adding a tiny random value to break ties and avoid identical play patterns.

This heuristic yields competitive play without using advanced search techniques such as minimax. Although simple, it demonstrates how to program an AI that evaluates potential moves and chooses among them.

## Most Challenging Part

The most intricate part of the code is the **win detection logic** implemented in the `check_winner` and `_count_dir` functions. Checking for a win in Connect Four requires scanning in all directions (horizontal, vertical, and both diagonals) while keeping track of the current player’s token and correctly handling board boundaries. The program counts connected tokens in each direction from the last move position to determine if a player has formed a line of four. Properly counting in both the positive and negative directions along each axis without running off the board can be tricky; this section was the only part of the program where it was useful to verify approach details from online references before finalizing the implementation.

## Files in This Repository

* **`connect4_human_vs_ai.py`** — The main program file containing the game logic, board representation, AI heuristic, and command‑line interface.
* **`README.md`** — This documentation file explaining how to run the game and describing the AI approach and most difficult code section.
* **`.gitignore`** — A file specifying common Python build artifacts and OS files to exclude from version control.
* **`requirements.txt`** — Lists any dependencies. This file is provided for completeness even though no external packages are required.

## License

This project is licensed under the MIT License. See the **LICENSE** file for details.

# Risk-Like Territory Game

## Overview
This Java program simulates a strategic, turn-based game similar to the classic board game Risk. Players choose territories, deploy troops, and engage in battles to conquer regions and ultimately dominate the map.

## Features
- **Territory Selection**: Players can select from a list of territories, each with a predefined number of troops.
- **Combat System**: A simple combat system based on random dice rolls determines the outcome of battles.
- **Turn-Based Mechanics**: The game progresses in turns, with a maximum of six turns for each battle.

## How to Play
1. Run the `Main` class.
2. Choose your territory from the list provided.
3. Select an enemy territory to attack.
4. Watch the battle unfold through dice rolls.
5. The game declares the winner based on the remaining troops.

## Code Structure
- `Main` class: Contains the main method and game logic.
- `Territorio` class: Represents a territory with a name and troop count.
- `combattimento` method: Simulates combat between two territories.

## How Combat Works
The combat is resolved through dice rolls:
- Each side rolls a six-sided die.
- If the attacker's roll is higher, the defender loses a troop.
- If the defender's roll is higher, the attacker loses a troop.
- Combat continues for a maximum of six turns or until one side has no troops left.

## Conclusion
This program is a simple representation of the mechanics found in Risk-like games. It demonstrates basic Java programming concepts such as classes, methods, loops, and conditionals.

## License
The code is open-source and can be modified or distributed under the terms specified by the original author, Giuseppe A.

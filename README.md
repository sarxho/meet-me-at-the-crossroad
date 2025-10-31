#  Meet Me at the Crossroads

**Meet Me at the Crossroads** is an interactive, text-based adventure game developed in **Python** and designed to run inside a **Jupyter Notebook**.  
Players start with **£1000** and must navigate a series of choices to reach their friend at the crossroads.  
Each decision affects the player's journey, finances, and final outcome — leading to one of several possible endings.

---

##  Game Overview
Your mission is simple: **reach your friend at the crossroads before your money runs out**.  
However, the path you take will be filled with unexpected challenges, twists, and moral decisions.  
Choose wisely — some paths lead to fortune, while others result in loss or failure.

You’ll encounter situations such as:
- Choosing to **take the bus** or **walk** to save money  
- Deciding whether to **trust strangers** or go alone  
- Buying **maps** or **mystery boxes** that may help or hurt you  
- Managing your **budget** throughout your journey  

---

##  Game Logic
Each choice branches the story in new directions. The game features:
- A **money management system** that updates after every decision  
- **Multiple storylines** based on your answers  
- **Win/Lose** endings depending on your balance and path  
- Background music and sound effects using `pygame`  


---

##  Requirements

To run the game, ensure you have the following installed:

- **Python 3.8+**
- **Jupyter Notebook**
- **Pygame**

Install dependencies by running this command in a Jupyter cell:
```python
!pip install pygame
import pygame
```
---
## Folder Contents

| File Name | Description |
| :--- | :--- |
| `game_project.ipynb` | Main Jupyter Notebook file containing the game logic. |
| `Sakura-Girl-Yay-chosic.com_.mp3` | Background music played during the game. |
| `winner-game-sound-404167.mp3` | Sound effect for winning the game. |
| `game-over-arcade-6435.mp3` | Sound effect for losing or game over. |
| `Meet Me At The Crossroads.drawioo.png` | Exported image version of the flowchart (for reference). |
| `README.md(2)` | This documentation file. |
---

## How to Play

- Open Jupyter Notebook.
- Navigate to your project folder (SARAH OYEYEMI Python project).

- Open `game_project.ipynb`

- Run all cells in order (from the top).

Follow the on-screen prompts and type your responses:

- Example: yes, no, bus, walk, etc.

- The game will display your remaining money and outcome after each decision.


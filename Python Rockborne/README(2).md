
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

---
## Script
```python
#importing the one libary
import pygame

# sound effect functions for winning and losing 

def play_win_sound():
    win_sound = pygame.mixer.Sound("winner-game-sound-404167.mp3")   # this function is to be used when the player wins the game
    win_sound.play()

def play_lose_sound():
    lose_sound = pygame.mixer.Sound("game-over-arcade-6435.mp3")  # this function is to be used when the player wins loses game
    lose_sound.play()


def MeetMeAtTheCrossroads():
    money = 1000  # Here is the set amount of money that the player has to spend
    playing = True
    pygame.mixer.music.load("Sakura-Girl-Yay-chosic.com_.mp3")
    pygame.mixer.music.play(-1)

    print("Welcome to MEET ME AT THE CROSSROADS! You have £1000 to reach your friend at the crossroads. But there may be some challenges ahead. So be careful!!!", flush=True)
    
    while playing:  # Here the game officially starts 
        question = input("Do you want to go and meet your friend at the crossroads? yes or no: ") 
        if question.lower().strip() == "no":
            print("That's too bad. The journey ends before it begins.")
            play_lose_sound() # Here is an example of the sound playing 
            break
        elif question != "yes":
            print("Please type 'yes' or 'no'.", flush=True) # flush=True is used to ensure that the print shows as soon as possible 
            continue

        # THIS is the first choice: BUS or WALK
        question = input("Great! Do you take the BUS or WALK to the nearest train station? TYPE bus or walk: ")

        # --- BUS PATH ---
        if question.lower().strip() == "bus":
            money -= 100
            print("You took the bus which cost you £100.Money left £" + str(money), flush=True)
            question = input("Now that you have £" + str(money) + " do you take a CAB or TRAIN towards your friend? TYPE cab or train: ")

            # CAB PATH
            if question.lower().strip() == "cab":
                money -= 200
                print(Fore.CYAN + "You took the cab which cost you £200. Money left £" + str(money), flush=True)
                question = input("At the station a stranger offers to split a ride to your friend's town. TYPE yes or no: ")

                if question.lower().strip() == "yes":
                    # Thief path
                    money -= 250
                    print("They turned out to be a thief! You lost £250. Money left £" + str(money), flush=True)
                    question = input("Do you CALL the police or stay in a HOTEL? TYPE police or hotel: ")

                    if question.lower().strip() == "police":
                        money += 50
                        print("The police help and give you £50. Money left £" + str(money), flush=True)
                        question = input("Do you ASK them for a lift to the crossroads? TYPE ask or no: ")
                        if question.lower().strip() == "ask":
                            money -= 75
                            print("They charge £75 for fuel. Money left £" + str(money), flush=True)
                            print("You reach the crossroads and meet your friend with £" + str(money) + " left! Congratulations!", flush=True)
                            play_win_sound()
                            break
                        else:
                            print("You decide to go home instead. The friendship will have to wait.", flush=True)
                            play_lose_sound()
                            break

                    else:
                        # Hotel robbery path 
                        money -= 150
                        print("You stay in a cheap hotel for £150. Money left £" + str(money), flush=True)
                        print("You wake up to find your bag gone. All your money has vanished. Game Over.", flush=True)
                        play_lose_sound()
                        break

                else:
                    # Travel alone path
                    money -= 300
                    print("You travel alone. The ride costs £300. Money left £" + str(money), flush=True)
                    print("Halfway there your phone dies and you get lost! You never find the crossroads.", flush=True)
                    play_lose_sound()
                    break

            # TRAIN PATH
            elif question.lower().strip() == "train":
                money -= 120
                print("You buy a train ticket for £120.Money left £" + str(money), flush=True)
                question = input("A friendly passenger offers to sell you a MAP for £50. TYPE buy or ignore: ")

                if question.lower().strip() == "buy":
                    money -= 50
                    print("You bought the map.Money left £" + str(money), flush=True)
                    print("The map helps you find a shortcut, saving £200 in travel costs!", flush=True)
                    money += 200
                    print("You arrive at the crossroads early with £" + str(money) + ". Your friend is amazed at your luck!", flush=True)
                    play_win_sound()
                    break
                else:
                    print("You ignore the map and get off at the wrong stop.", flush=True)
                    money -= 400
                    print("You spend £400 fixing your mistake. Money left £" + str(money), flush=True)
                    if money <= 0:
                        print("You run out of money wandering the countryside. Game Over.", flush=True)
                        play_lose_sound()
                        break
                    else:
                        print("You finally make it, exhausted but relieved. You reach your friend with £" + str(money), flush=True)
                        play_win_sound()
                        break

        # --- WALK PATH ---
        elif question.lower().strip() == "walk":
            money += 50
            print("You walked and found £50 on the way. Money left £" + str(money), flush=True)
            question = input("At the station, do you take the TRAIN or try HITCHHIKING? TYPE train or hitchhike: ")

            if question.lower().strip() == "train":
                money -= 100
                print("The train costs £100. Money left £" + str(money), flush=True)
                question = input("On board, a stranger offers you a 'mystery box' for £200. TYPE yes or no: ")

                if question.lower().strip() == "yes":
                    money -= 200
                    print( "You open the box... it’s full of old coins worth £500!", flush=True)
                    money += 500
                    print("You’re rich! You meet your friend and buy dinner for both of you £" + str(money) + " left.", flush=True)
                    play_win_sound()
                    break
                else:
                    print("You ignore the offer, enjoy a quiet ride, and reach the crossroads calmly.", flush=True)
                    play_win_sound()
                    break

            elif question.lower().strip() == "hitchhike":
                question = input( "A truck driver stops and offers a lift for £50. Do you ACCEPT or DECLINE? TYPE accept or decline: ")

                if question.lower().strip() == "accept":
                    money -= 50
                    print("You pay £50 and hop in.Money left £" + str(money), flush=True)
                    question = input("Halfway there, the truck breaks down. Do you HELP fix it or WALK away? TYPE help or walk: ")

                    if question.lower().strip() == "help":
                        money += 100
                        print("The driver thanks you with £100. Money left £" + str(money), flush=True)
                        print("He drives you the rest of the way. You arrive at the crossroads safely with £" + str(money), flush=True)
                        play_win_sound()
                        break
                    else:
                        money -= 200
                        print("You walk for miles and spend £200 on food and water. Money left £" + str(money), flush=True)
                        if money <= 0:
                            print("You collapse on the road, broke and tired. Game Over.", flush=True)
                            play_lose_sound()
                            break
                        else:
                            print("After hours, you finally find your friend waiting for you at the crossroads.", flush=True)
                            play_win_sound()
                            break

                else:
                    print("You decline and start walking again. It rains heavily and you catch a cold.", flush=True)
                    money -= 100
                    print("You spend £100 on medicine and warm clothes. Money left £" + str(money), flush=True)
                    if money <= 0:
                        print("You run out of money and energy. Game Over.", flush=True)
                        play_lose_sound()
                        break
                    else:
                        print("You recover and eventually reach your friend late but alive.", flush=True)
                        play_win_sound()
                        break
        else:
            print("Invalid input. Please type bus or walk.", flush=True)
            continue

        playing = False  # end loop after a storyline

    # Stop music once the game ends 
    pygame.mixer.music.fadeout(2000)
    pygame.mixer.music.stop()

    print("Thanks for playing MEET ME AT THE CROSSROADS!", flush=True)


# Run the game
MeetMeAtTheCrossroads()

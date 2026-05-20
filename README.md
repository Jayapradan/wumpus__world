<h1>ExpNo 9: Solve Wumpus World Problem using Python demonstrating Inferences from Propositional Logic</h1> 
<h3>Name: JAYAPRADAN M                      </h3>
<h3>Register Number/Staff Id: 212224240061                </h3>
<H3>Aim:</H3>
<p>
    To solve  Wumpus World Problem using Python demonstrating Inferences from Propositional Logic
</p>
<h1>Problem Description</h1>
<hr>
<h2>Wumpus World</h2>
<hr>
The Wumpus world is a simple world example to illustrate the worth of a knowledge-based agent and to represent knowledge representation.

The figure below shows a Wumpus world containing one pit and one Wumpus. There is an agent in room [1,1]. The goal of the agent is to exit the Wumpus world alive. The agent can exit the Wumpus world by reaching room [4,4]. The wumpus world contains exactly one Wumpus and one pit. There will be a breeze in the rooms adjacent to the pit, and there will be a stench in the rooms adjacent to Wumpus.

![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/cd6b68dc-c79f-4dcb-8126-04da90d65912)

<center>Wumpus World Representation</center>
<p>
This is a python program that uses propositional logic sentences to check which rooms are safe. 

It is assumed that there will always be a safe path that the agent can take to exit the Wumpus world. The logical agent can take four actions: Up, Down, Left and Right. These actions help the agent move from one room to an adjacent room. The agent can perceive two things: Breeze and Stench.
</p>

<hr>
<h1>Sample Input and Output:</h1>
<hr>

![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/8696111a-a4a7-47cb-ba4b-43a4ef88573f)
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/4be5bf06-79fa-4fa0-9334-38a33f06060b)

## PROGRAM :

```PY
wumpus = [["Save","Breeze","PIT","Breeze"],
          ["Smell","Save","Breeze","Save"],
          ["WUMPUS","GOLD","PIT","Breeze"],
          ["Smell","Save","Breeze","PIT"]]

# Initial Variables
row = 0
column = 0
arrow = True
player = True
score = 0

while player:
    choice = input("press u to move up\npress d to move down\npress l to move left\npress r to move right\n")

    if choice == "u":
        if row != 0:
            row -= 1
        else:
            print("move denied")

    elif choice == "d":
        if row != 3:
            row += 1
        else:
            print("move denied")

    elif choice == "l":
        if column != 0:
            column -= 1
        else:
            print("move denied")

    elif choice == "r":
        if column != 3:
            column += 1
        else:
            print("move denied")

    else:
        print("move denied")

    print("current location:", wumpus[row][column], "\n")

    # Arrow logic
    if wumpus[row][column] == "Smell" and arrow:
        arrow_choice = input("Throw arrow? (y/n): ")
        if arrow_choice == "y":
            arrow_throw = input("Direction (u/d/l/r): ")

            try:
                if arrow_throw == "u" and wumpus[row-1][column] == "WUMPUS":
                    print("Wumpus killed!")
                    score += 1000
                    wumpus[row-1][column] = "Save"
                elif arrow_throw == "d" and wumpus[row+1][column] == "WUMPUS":
                    print("Wumpus killed!")
                    score += 1000
                    wumpus[row+1][column] = "Save"
                elif arrow_throw == "l" and wumpus[row][column-1] == "WUMPUS":
                    print("Wumpus killed!")
                    score += 1000
                    wumpus[row][column-1] = "Save"
                elif arrow_throw == "r" and wumpus[row][column+1] == "WUMPUS":
                    print("Wumpus killed!")
                    score += 1000
                    wumpus[row][column+1] = "Save"
                else:
                    print("Arrow wasted...")
                    score -= 10
            except:
                print("Invalid direction!")

            print("Score:", score)
            arrow = False

    # Wumpus check
    if wumpus[row][column] == "WUMPUS":
        score -= 1000
        print("\nWumpus here!! You died!")
        print("Score:", score)
        break

    # GOLD condition (MISSING PART)
    if wumpus[row][column] == "GOLD":
        score += 1000
        print("\nYou found GOLD! You win 🏆")
        print("Score:", score)
        break

    # PIT condition
    if wumpus[row][column] == "PIT":
        score -= 1000
        print("You fell into PIT 😭")
        print("Score:", score)
        break
```

## OUTPUT :
<img width="321" height="247" alt="image" src="https://github.com/user-attachments/assets/bcd00a7b-bf16-4468-90ba-9b44eb0b467b" />


## RESULT :

The Wumpus World problem was successfully implemented using Python to demonstrate inference using propositional logic. The agent safely navigates the environment, detects dangers, and reaches the goal or identifies hazards based on logical reasoning.


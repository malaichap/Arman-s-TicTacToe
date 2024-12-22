#Tic Tac Toe Game
#Mind Map For The Game[Tic Tac Toe]
''' (1)The Game Board To Appear On Console
(2)The First Player's Input
(3)Condition To Check For Win Or Tie{1}
(4)The Second Player's Input
(5)Condition To Check For Win Or Tie{2}
(6)Creating A Recurring Loop To Execute It As Per User's Wish'''

import random
GameBoard = [ '1','2','3',
              '4','5','6',
              '7','8','9'  ]
CurrentPlayer = "X"
Winner = None
GameRunning = True

#(1)Printing Gameboard For Player's Visual Reference
def PrintBoard(GameBoard):
    print()
    print("         ",GameBoard[0] + "|" + GameBoard[1] + "|" + GameBoard[2])
    print("        ","-------")
    print("         ",GameBoard[3] + "|" + GameBoard[4] + "|" + GameBoard[5])
    print("        ","-------")
    print("         ",GameBoard[6] + "|" + GameBoard[7] + "|" + GameBoard[8])
    print()

#Player's Input
def PlayerInput(Gameboard):
    a = int(input(f"{CurrentPlayer}'s Turn:"))
    if a>=1 and a<=9 and GameBoard[a-1] == str(a):
        GameBoard[a-1] = CurrentPlayer
    else:
        print()
        print(" !! Spot Already Filled !! ")
        print()
#Checking The Horizontal Row For Winner(Same Sequence In All Horizontal Row)
def checkHorizontal(GameBoard):
    global Winner
    if GameBoard[0] == GameBoard[1] == GameBoard[2]:
        Winner = GameBoard[0]
        return True
    elif GameBoard[3] == GameBoard[4] == GameBoard[5]:
        Winner = GameBoard[3]
        return True
    elif GameBoard[6] == GameBoard[7] == GameBoard[8]:
        Winner = GameBoard[6]
        return True
#Checking The Vertical Column For Winner(Same Sequence In All Vertical Column)
def checkColumn(GameBoard):
    global Winner
    if GameBoard[0] == GameBoard[3] == GameBoard[6]:
        Winner = GameBoard[0]
        return True
    elif GameBoard[1] == GameBoard[4] == GameBoard[7]:
        Winner = GameBoard[1]
        return True
    elif GameBoard[2] == GameBoard[5] == GameBoard[8]:
        Winner = GameBoard[3]
        return True
#Checking The Diagonal For Winner(Same Sequence In Diagonal)
def checkDiagonal(GameBoard):
    global Winner
    if GameBoard[0] == GameBoard[4] == GameBoard[8]:
        Winner = GameBoard[0]
        return True
    elif GameBoard[2] == GameBoard[4] == GameBoard[6]:
        Winner = GameBoard[2]
        return True
#Checking If All The Spaces In The Game Board Have Exhausted Or Not To Declare Tie Situation
def checkTie(GameBoard): 
    global GameRunning
    if checkHorizontal(GameBoard) and checkColumn(GameBoard) and checkDiagonal(GameBoard):
        print(Winner)
    elif GameBoard[0] != str(1) and GameBoard[1] != str(2) and GameBoard[2] != str(3) and GameBoard[3] != str(4) and GameBoard[4] != str(5) and GameBoard[5] != str(6) and GameBoard[6] != str(7) and GameBoard[7] != str(8) and GameBoard[8] != str(9):
        print(GameBoard)
        print()
        print(" !! IT IS A TIE !! ")
        print()
        GameRunning=False
        return GameRunning   
#Condition For Switching Turn Between Players 
def SwitchPlayer():
    global CurrentPlayer
    if CurrentPlayer == "X":
        CurrentPlayer = "O"
    else:
        CurrentPlayer = "X"
#To Check If Winner
def checkWinner():
    global GameRunning
    if checkHorizontal(GameBoard) or checkColumn(GameBoard) or checkDiagonal(GameBoard):
        if Winner=="X":
            print("The Winner Is:", PlayerOne)
        elif Winner=="O":
            print("The Winner Is:", PlayerTwo)
        GameRunning = False
        return GameRunning
#Extra Player As Computer
def NoPlayer(GameBoard):
    while CurrentPlayer == "O":
        position = random.randint(0,8)
        if GameBoard[position] in ['1','2','3','4','5','6','7','8','9']:
            GameBoard[position] = "O"
            SwitchPlayer()
#Function To Repeat The Same Code With Ease
def Play():
    while GameRunning:
        PrintBoard(GameBoard)
        PlayerInput(GameBoard)
        checkWinner()
        SwitchPlayer()
        checkWinner()
        checkTie(GameBoard)
#Variable For While Loop Operation   
AskPlay = input("Press Any Key To Play,Press N To Exit:")
if AskPlay == "Y" or AskPlay == "y" :
    AskPlay = True
elif AskPlay == "N" or AskPlay == "n":
    AskPlay = False

#While Loop That Repeats The Game  
while AskPlay:
    PlayerOne = input("Player One Name[X]:")
    PlayerTwo = input("Player Two Name[O]:")
    print("----------------------------")
    print(PlayerOne , "VS" , PlayerTwo)
    print("----------------------------")
    Play()
    AskPlay = input("Press Any Key To Play,Press N To Exit:")
    if AskPlay == "Y" or AskPlay == "y" :
        AskPlay = True
    elif AskPlay == "N" or AskPlay == "n":
        AskPlay = False
    GameBoard = [ '1','2','3',
              '4','5','6',
              '7','8','9'  ]
    CurrentPlayer = "X"
    Winner = None
    GameRunning = True

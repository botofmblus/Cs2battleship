#_______________________________________________________________________________________________________________________
#__________________________________________________Documentation________________________________________________________
#_______________________________________________________________________________________________________________________
#Gavin Haroche, date:               1/25/2023
#Assignment:                        Battleship
#Versions:                          0.1 Placing Done
#                                   0.2 Items, arrays and variables added
#                                   0.4 added fight function, along with the user being able to attack.
#                                   0.6 Enemy can now attack
#                                   0.7 cleaned up the enemy array
#                                   1   Fight function complete, not bullet proof
#                                   1.2 Added Crafting
#                                   1.3 Added item farming
#                                   1.5 Item cheat code added
#                                   1.8 Using items in the fight
#                                   2.0 Added starting information
#                                   2.1 Win conditions added.
#        CURRENT VERSION            2.2 Bullet proof, sounds added, documentation added, slight finalization tweaks.

#Bonuses:                           Alternate weapons, inventory, crafting system, extra design, mining system.







import random
import time



#_______________________________________________________________________________________________________________________
#__________________________________________________Functions____________________________________________________________
#_______________________________________________________________________________________________________________________

def ship():
    print("                                     # #  ( )")
    print("                                  ___#_#___|__")
    print("                              _  |____________|  _")
    print("                       _=====| | |            | | |==== _")
    print("                 =====| |.---------------------------. | |====")
    print("   <--------------------'   .  .  .  .  .  .  .  .   '--------------/")
    print("     \                                                             /")
    print("      \_______________________________________________WWS_________/")
    print("~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~\n~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~")

    return

def testertool(inventory1):
                                                                                                                        #Appending all the items to the inventory
    inventory1.append("shotgunmissile")
    inventory1.append("radarshell")
    inventory1.append("heavenlyshell")
    inventory1.append("rocks")
    inventory1.append("iron")
    inventory1.append("gunpowder")
    inventory1.append("copper")
    inventory1.append("fuel")
    inventory1.append("fairy dust")

    return inventory1                                                                                                   #return applies value to the function
                                                                                                                        #Generating boats

def generation(enemyarrmap, myarr):

    while True:
        for i in range(5):
            randomrows = random.randint(0, 4)                                                                           # random enemy boat placing.
            randomcolls = random.randint(0, 4)
            if enemyarrmap[randomcolls][randomrows] == "o":                                                             #dont place on the same dot
                pass
            else:
                enemyarrmap[randomcolls][randomrows] = "o"
                #infinite loop
        try:                                                                                                            #Try statement for boat placing for improper coordinate


            print("please enter the coordinate point of the ship you would like to place")
            print("----------------------------------------------------------------------------")
            print(" a1   a2    a3    a4   a5\n b1   b2    b3    b4   b5\n c1   c2    c3    c4   c5\n d1   d2    d3    d4   d5\n e1   e2    e3    e4   e5")
            arrmapvisual = str(myarr[0]) + "\n" + str(myarr[1]) + "\n" + str(myarr[2]) + "\n" + str(myarr[3]) + "\n" + str(myarr[4])
            print("----------------------------------------------------------------------------")
            print(arrmapvisual)
            print("----------------------------------------------------------------------------")
            for i in range(5):
                choice1 = input("type here: ")
                choice1=[*choice1]                                                                                      #split a1 into [a, 1]


                for j in range(5):

                    alphabet = ["a", "b", "c", "d", "e"]
                    if alphabet[j] == choice1[0]:                                                                       #run through the alphabet to get a value out of a,b,c,d,or e
                        collplacement = j
                        break
                    j+=1

                if collplacement < 0 or collplacement > 4:
                    exit()                                                                                              #trigger the except

                myarr[collplacement][int(choice1[1])-1] = "0"                                                           #placing the dot
                arrmapvisual = str(myarr[0]) + "\n" + str(myarr[1]) + "\n" + str(myarr[2]) + "\n" + str(myarr[3]) + "\n" + str(myarr[4])
                print(arrmapvisual)
                i+=1

            print("placing / generation complete!")
            time.sleep(4)
            print("\n\n\n\n\n\n\n\n\n\n\n\n")
            return enemyarrmap, myarr                                                                                   #return both boat placements.
        except:
            print("\n\n\nyou crashed one of your boats, great job smarty......")
            myarr = [["-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-"],["-", "-", "-", "-", "-"],["-", "-", "-", "-", "-"]]
            time.sleep(2)
                                                                                                                        #the main game
                                                                                                                        #main game

def fight(myarr, enemyarrmap, enemyarrmapvisual, inventory1):
    print("\n\n\n\n\nBEEP BOOP, ENGAGING BATTLE, 10011 101312. BEEP!")
    time.sleep(1)
    print("\n\n\n\nencoding radar information")
    time.sleep(0.99)
    print("buffering")
    time.sleep(1)
    print("accesing enemy location info")
    time.sleep(0.5)
    print("plotting")
    time.sleep(0.5)
    print("All systems online!")
    time.sleep(3)
    print("\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n")
    time.sleep(0.5)
    print("╭━━╮╱╱╱╭╮╱╭╮╭╮╱╱╱╱╭━━━┳━━━╮\n┃╭╮┃╱╱╭╯╰┳╯╰┫┃╱╱╱╱┃╭━╮┃╭━╮┃\n┃╰╯╰┳━┻╮╭┻╮╭┫┃╭━━╮┃┃╱┃┃╰━━╮\n┃╭━╮┃╭╮┃┃╱┃┃┃┃┃┃━┫┃┃╱┃┣━━╮┃\n┃╰━╯┃╭╮┃╰╮┃╰┫╰┫┃━┫┃╰━╯┃╰━╯┃\n╰━━━┻╯╰┻━╯╰━┻━┻━━╯╰━━━┻━━━╯")
    time.sleep(1)


    while True:
        print("----------------------------------------------------------------\n   OUR INFORMATION ON THE ENEMY")
        print( str(enemyarrmapvisual[0]) + "\n" + str(enemyarrmapvisual[1]) + "\n" + str(enemyarrmapvisual[2]) + "\n" + str(enemyarrmapvisual[3]) + "\n" + str(enemyarrmapvisual[4]))
        print("----------------------------------------------------------------\n   OUR SHIP MAP LAYOUT AND INFORMATION")
        arrmapvisual = str(myarr[0]) + "\n" + str(myarr[1]) + "\n" + str(myarr[2]) + "\n" + str(myarr[3]) + "\n" + str(myarr[4])
        print(arrmapvisual)
        print("----------------------------------------------------------------")
        time.sleep(2)

                                                                                                                        #option to leave
        attackchoice = input("Do we back out, or do we attack?")
        if attackchoice == "back out":
            return myarr, enemyarrmap, enemyarrmapvisual, inventory1                                                    #leave and save progress
        elif attackchoice == "attack":
            #print(enemyarrmap)
            print("Where do we attack captain!?")                                                                       #coordinate placing and encoding
            attackspot = input(" a1   a2    a3    a4   a5\n b1   b2    b3    b4   b5\n c1   c2    c3    c4   c5\n d1   d2    d3    d4   d5\n e1   e2    e3    e4   e5\n\n")
            try:
                attackspot = [*attackspot]                                                                              #same placing system as the origional generation.

                for i in range(5):

                    alphabet = ["a", "b", "c", "d", "e"]
                    if alphabet[i] == attackspot[0]:                                                                    #running through alphabet to encode a value
                        collplacement = i
                        break
                    i += 1

                print("\nregular shell (infinite)")
                print("\nradar shell")
                print("\nheavenly shell")                                                                               #special item using
                print("\nshotgun missile")
                print("\n\nYour inventory:  " + str(inventory1))
                weaponchoice = input("what should we use to attack!?")

                if weaponchoice == "radar shell":                                                                       #discover ships in a row
                    try:
                        inventory1.remove("radarshell")                                                                 #remove the item, and if you cant, than you must not have it
                    except:
                        print("\n\n\n\nyou cant use a radar shell, system bugged, restarting with error code: 01")
                        time.sleep(3)
                        continue
                    for j in range(5):
                        if enemyarrmap[collplacement][j] == "o":
                            enemyarrmapvisual[collplacement][j]="👁"                                                    #ship detected
                            print("Enemy ship revealed")
                            time.sleep(1)
                        else:
                            enemyarrmapvisual[collplacement][j] = "❌"                                                  #no ship detected

                elif weaponchoice == "shotgun missile":
                    try:                                                                                                #random shot item
                        inventory1.remove("shotgunmissile")
                    except:
                        print("\n\n\n\nyou cant use a shotgun missile, system bugged, restarting with error code 01")
                        time.sleep(3)
                        continue
                    for i in range(5):
                        randomrows = random.randint(0, 4)
                        randomcolls = random.randint(0, 4)                                                              #randomly place shots
                        if enemyarrmap[randomrows][randomcolls] == "o":
                            if enemyarrmapvisual[randomrows][randomcolls] == "🔥":
                                    enemyarrmapvisual[randomrows][randomcolls] = "💀"
                                    enemyarrmap[randomrows][randomcolls] = "-"
                                    print("\nEnemy ship sunken")

                                    time.sleep(1)
                            else:
                                enemyarrmapvisual[randomrows][randomcolls] = "🔥"
                                print("\nEnemy ship damaged")

                                time.sleep(1)
                        else:
                            enemyarrmapvisual[randomrows][randomcolls] = "❌"


                elif weaponchoice == "heavenly shell":                                                                  #one shot weapon
                    try:
                        inventory1.remove("heavenlyshell")                                                              #same checker
                    except:
                        print("\n\n\n\nyou cant use a heavenly shell, SystemError, restarting with error code 01")
                        time.sleep(3)
                        continue

                    if enemyarrmap[collplacement][int(attackspot[1])-1] == "o":                                         #can not damage ships, only destroys them
                            enemyarrmapvisual[collplacement][int(attackspot[1]) - 1] = "💀"

                            print("\nEnemy ship plunged")
                            time.sleep(1)
                            enemyarrmap[collplacement][int(attackspot[1]) - 1] = "-"
                    else:
                        enemyarrmapvisual[collplacement][int(attackspot[1]) - 1] = "❌"
                        print("\nENEMY SHIP MISSED")
                        time.sleep(1)

                elif weaponchoice == "regular shell":                                                                   #Normal weapon
                    if enemyarrmap[collplacement][int(attackspot[1])-1] == "o":
                        if enemyarrmapvisual[collplacement][int(attackspot[1]) - 1] == "🔥":                            #if its alr damaged, kill it
                            enemyarrmapvisual[collplacement][int(attackspot[1]) - 1] = "💀"
                            print("\nEnemy ship sunken")

                            time.sleep(1)
                            enemyarrmap[collplacement][int(attackspot[1]) - 1] = "-"                                    #remove it
                        else:
                            enemyarrmapvisual[collplacement][int(attackspot[1]) - 1] = "🔥"                             #damage shi;s
                            print("\nEnemy ship damaged")

                            time.sleep(1)
                    elif enemyarrmap[collplacement][int(attackspot[1]) - 1] == "-":
                            enemyarrmapvisual[collplacement][int(attackspot[1]) - 1] = "❌"
                            print("\nENEMY SHIP MISSED")
                            time.sleep(1)
                else:
                    print("\nGreat job, youve jammed the cannon with a dry shot")                                       #saftey statement
                    time.sleep(1)
                                                                                                                        #win checker
                counter = 0
                for i in range(5):
                    for j in range(5):
                        if enemyarrmap[i][j] == "o":
                            counter+=1
                if counter == 0:
                    print("ALL ENEMY SHIPS SUNKEN! WE WIN!")
                    return "victory"




                print("\n\n\n\n\n")
                time.sleep(2)
                print("Incoming enemy missile!\n\n\n")
                time.sleep(2)


                while True:
                    rowattack = random.randint(0,4)                                                                     #random attack
                    colattack = random.randint(0,4)
                    if myarr[rowattack][colattack] == "0":
                        print("The enemy hit us!")
                        time.sleep(2)
                        myarr[rowattack][colattack] = "🔥"
                        break
                    elif myarr[rowattack][colattack] == "🔥":                                                           #if its unhit, hit it, if its hit, kill it
                         myarr[rowattack][colattack] = "💀"
                         print("\nThe enemy sunk one of our ships!")
                         time.sleep(2)
                    else:
                        print("\nthe Enemy missed!")                                                                    #else miss
                        time.sleep(2)
                        break


                time.sleep(1)

                counter = 0
                for i in range(5):
                    for j in range(5):
                        if enemyarrmap[i][j] == "💀":
                            counter+=1                                                                                  #same system as old win checker.
                if counter == 5:
                    print("Weve been FATALLY HIT! WERE ALL GONNA DI-I-I-I$R-I3vw3_I3@#$^%@^")
                    return "loss"
            except:
                print("\n\n\n\n\n\nSystem Error: False coordinate, restarting")
                time.sleep(2)


    return myarr, enemyarrmap, enemyarrmapvisual, inventory1
                                                                                                                        #adding resources to inventory

def mine(inventory1):

    time.sleep(1)
    print("\n\n\n\n\n\nfinding a local island to dock your ship")
    time.sleep(1)
    print("\n\n\n\n\ndocking")
    time.sleep(1)
    while True:
        print("\n\n\n\nwelcome to sanctuary island")
        choice = input("\ndo you want to 'leave', or 'collect more resources'.")

        if choice == "collect more resources":
            print("\n\n\n\nmining...")
            for i in range(6):
                time.sleep(random.randint(1,5))                                                                         #random waits
                print("\n\n\n\n\nmining chunk " + str(i))
                i+=1
            materiallist = ["rocks", "iron", "gunpowder", "copper", "fuel", "fairy dust"]
            newitem = random.choice(materiallist)                                                                       #adding to your inventory
            print("you got a " + newitem)
            inventory1.append(newitem)
            print(inventory1)

        elif choice == "leave":
            return inventory1
        else:
            print("\n\n\nnot a valid option.")



    return inventory1
                                                                                                                        #The main main menu at the beginning

def menu():
            print("\n\n\n\nGavin Haroche's 'Battle Ship'")
            time.sleep(2)

            input("\nThis game was inspired by the classic game battleship with combinations of classic RPGs.\n\nImportant game info: You can chose to collect resources in order to craft items which will make the battle go by faster. All ships are 1x1,\nEach ship is able to take one shot before dying unless a holy shell is used.\nReturning to the menu with a damaged enemy ship or one of your ships damaged will NOT revive it.\nSelecting 'cheat' instead of the 3 options will cause your inventory to be fileld with all items in the game, you're welcome testers.\n\n(press enter/return to continue)")

            while True:
                menuchoice = input("\n\n\n\n\n\n\n\n\n\n\n\nShould we 'fight' or 'leave'!")

                if menuchoice == "fight":
                    menuchoice = True
                    break
                elif menuchoice == "leave":
                    menuchoice = False
                    break
                else:
                    print("\nnot a valid choice")
                    time.sleep(1)

            return menuchoice

def craft(inventory1):

    time.sleep(3)
    print("\n\n\n\n\nbeep boop, activating fabricator.")
    time.sleep(1)
    print("\n\n\n\n\n\n\n\nmaterial alchemy station online")
    print("\n\n\n\n\n\n\n\ndownloading blueprints from cloud.")

    for i in range(16):
        print("#", end=" ")
        time.sleep(0.5)
        i+=1

    print("\n\n\n\n\n\n\n\n\n\n\n")
    time.sleep(3)
    print('all crafting systems online\n')
    time.sleep(1)
    while True:
        print("\n\n\n\n\n\n\n\n\n\n\n\n\n\nCrafting options:\nshotgun missile (disperses 5 random shells around the enemy's location)  REQUIRES: gunpowder, rocks, and iron.\nradar shell (detects all enemies within a cross pattern)  REQUIRES:  Copper, iron, and fuel \nheavenly shell (through the power of the battleship gods, smite thy enemies with glory and triumph)  REQUIRES:  Fairy dust, fuel, and gunpowder.")

        print("\nplease say the item you want to craft, if you cant craft anything, please say 'return'")
        time.sleep(1)
        craftingchoice = input(inventory1)                                                                              #remove the items from the users inventory, and if you cant, theu must not have it.
        if craftingchoice == "shotgun missile":
          try:
                    inventory1.remove("gunpowder")
                    inventory1.remove("rocks")
                    inventory1.remove("iron")
                    inventory1.append("shotgun missile")                                                                #add the item
          except:
              print("you cant craft a shotgun missile")
        elif craftingchoice == "radar shell":
         try:
                    inventory1.remove("copper")
                    inventory1.remove("fuel")
                    inventory1.remove("iron")
                    inventory1.append("radar shell")
         except:
               print("you cant craft a radar shell")
        elif craftingchoice == "heavenly shell":
            try:
                    inventory1.remove("fairy dust")
                    inventory1.remove("fuel")
                    inventory1.remove("gunpowder")
                    inventory1.append("heavenly shell")
            except:
                print("you cant craft a heavenly shell")




        elif craftingchoice == "return":
            return inventory1




    return
#_______________________________________________________________________________________________________________________
#__________________________________________________Variables____________________________________________________________
#_______________________________________________________________________________________________________________________
shotgunmissile = 0                                                                                                      #Alternate special craftable weapon
radarshell = 0                                                                                                          #Alternate special craftable weapon
heavenlyshell = 0                                                                                                       #Alternate special craftable weapon
rocks = 0                                                                                                               #Crafting item
iron = 0                                                                                                                #Crafting item
gunpowder = 0                                                                                                           #Crafting item
copper = 0                                                                                                              #Crafting item
fuel = 0                                                                                                                #Crafting item
fairydust = 0                                                                                                           #Crafting item
inventory1 = []                                                                                                         #holding array for all of these items
enemyarrmap = [["-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-"]]
enemyarrmapvisual = [["🌊","🌊","🌊","🌊","🌊"],["🌊","🌊","🌊","🌊","🌊"],["🌊","🌊","🌊","🌊","🌊"],["🌊","🌊","🌊","🌊","🌊"],["🌊","🌊","🌊","🌊","🌊"]]
                                                                                                                        #invisible enemy placing map
myarr = [["-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-"], ["-", "-", "-", "-", "-"]]
                                                                                                                        #The visible user array map
#_______________________________________________________________________________________________________________________
#__________________________________________________MAIN_________________________________________________________________
#_______________________________________________________________________________________________________________________

if menu() == False:                                                                                                     #If the user decides they dont actually want to play
    quit()                                                                                                              #Destroy the console
generation(enemyarrmap, myarr)

while True:
    ship()                                                                                                              #print the design

    print("welcome to home, please sellect the next course of action captain!\n\nshould we: 'collect resources', 'fight', 'craft', or should we 'leave'?\n")
    option = input(":")
                                                                                                                        #second chance to quit
    if option == "leave":
        print("\nwe had a good run.... :(")
        quit()

    elif option == "collect resources":                                                                                 #mining function
        inventory1 = mine(inventory1)

    elif option == "fight":                                                                                             #fighting function
             fightoutput = fight(myarr, enemyarrmap, enemyarrmapvisual, inventory1)
             myarr=fightoutput[0]                                                                                       #re-asserting the defenitions of the variables
             enemyarrmap=fightoutput[1]                                                                                 #re-asserting the defenitions of the variables
             enemyarrmapvisual=fightoutput[2]                                                                           #re-asserting the defenitions of the variables
             inventory1 = fightoutput[3]                                                                                #re-asserting the defenitions of the variables
             if fightoutput == "loss" or fightoutput == "victory":                                                      #end conditionals
                 break


    elif option == "craft":
            inventory1=craft(inventory1)                                                                                #crafting function

    elif option == "cheat":
        inventory1 = testertool(inventory1)                                                                             #crafting function

    else:                                                                                                               #bullet proofing conditional
        print("\nnot a valid option")
        time.sleep(1)


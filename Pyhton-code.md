```phyton
import string
def multilineinput ():
    buffer = []
    while True:
        print("> ", end="")
        line = input()
        if line == "":
            break
        buffer.append(line)
    return("\n".join(buffer))

def tappedout_to_cockatrice(main):
    maindeck = changelinetap(main)
    print("Paste side / enter (weeb)\n")
    inp = multilineinput()
    sidedeck = changelinetap(inp)
    deck = []
    for line in maindeck:
        deck.append(line)
    if sidedeck != [""]:
        for line in sidedeck:
            deck.append("SB: "+line)
    return(deck)

def cockatrice_to_tappedout(main):
    maindeck = []
    sidedeck = []
    for line in main.split("\n"):
        if line[:3] == "SB:":
            sidedeck.append(changeline(line.replace("SB: ","")))
        else:
            maindeck.append(changeline(line))
    return maindeck,sidedeck

def changelinecock(line):
    words = ""
    for letter in line:
        words += letter
        if len(words) == 1:
            words += "x"
    return(words)

def changelinetap(deck):
    if deck != "":
        pos = 0
        countdown = -2
        xs = []
        deckstrlist = []
        deckstr = ""
        for letter in deck:
            deckstrlist.append (letter)
            
        for letter in deck:
            countdown += 1
            if letter == "\n":
                countdown = -2
            if countdown == 0:
                xs.append(pos)
            pos +=1
        
        for pos in xs:
            deckstrlist[pos] = ""
       
        for letter in deckstrlist:
            deckstr += letter
        decklist = deckstr.split("\n")
        return(decklist)
    else:
        return([""])
    
while True:
    print("Paste main and shit \n")
    main = multilineinput()
    print("")
    inp = input("cock2tap or tap2cock ")
    if inp == "cock2tap":
        maindeck,sidedeck = cockatrice_to_tappedout(main)
        print("main")
        for line in maindeck:
            print(line)
        input("press enter for side deck")
        for line in sidedeck:
            print(line)
    elif inp == "tap2cock":
        for line in tappedout_to_cockatrice(main):
            print(line)
    print("")
```

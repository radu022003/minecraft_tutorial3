### @explicitHints 1

# Aktivität: Mine! Alles mein!

---

## Schritt 1  
Erstelle Steuerungen für den Agenten. Benenne den vorhandenen ``||Player:bei Chat-Befehl||``-Block in **"mach"** um.  

---

## Schritt 2  
Du kannst ein einfaches Menü erstellen, um alle Befehle für den Agenten zu steuern. Ziehe einen ``||Logic:wenn ... dann ... ansonsten||``-Block in den ``||Player:bei Chat-Befehl "mach"||``-Block. Klicke auf das **(+)**-Symbol im ``||Logic:wenn ... dann ... ansonsten||``, um einen dritten Zweig hinzuzufügen, da du drei Bedingungen testen wirst.  

---

## Schritt 3  
Klicke auf das **(+)**-Symbol des ``||Player:bei Chat-Befehl "mach"||``-Blocks und benenne **num1** in **AgentenBefehl** um.  

### ~ tutorialhint  
```blocks  
player.onChat("mach", function (AgentenBefehl) {
    if (true) {

    } else if (false) {

    } else {

    }
})
```  

---

## Schritt 4  
Teste, welche Eingabe der Nutzer gemacht hat. Der Nutzer soll den Agenten teleportieren und drehen können. Der dritte Zweig gibt eine Nachricht, falls keine gültige Eingabe erfolgt. Ziehe den ``||Logic:0 = 0||``-Vergleichsblock und dupliziere ihn, da du zwei brauchst.  

Platziere diese Blöcke in den ``||Logic:wenn ... dann ... ansonsten||``-Block.  

---

## Schritt 5  
Passe die Vergleiche an, um die Eingabe des Nutzers zu testen. Der Wert von ``||Variables:AgentenBefehl||`` entscheidet, was passiert. Beispielsweise könnte der Wert **1** bedeuten, dass der Agent teleportiert wird, und **2**, dass er sich drehen soll.  

### ~ tutorialhint  
```blocks  
player.onChat("mach", function (AgentenBefehl) {
    if (AgentenBefehl == 1) {

    } else if (AgentenBefehl == 2) {

    } else {

    }
})
```  

---

## Schritt 6  
Füge die Aktionen für den Agenten hinzu. Ziehe einen ``||Agent: Agent teleportiere zu Spieler||``-Block in den ersten Zweig des ``||Logic:wenn ... dann ... ansonsten||``-Blocks.  

### ~ tutorialhint  
```blocks  
player.onChat("mach", function (AgentenBefehl) {
    if (AgentenBefehl == 1) {
agent.teleportToPlayer()
    } else if (AgentenBefehl == 2) {

    } else {

    }
})
``` 

---

## Schritt 7  
Füge einen ``||Agent:Agent drehe||``-Block in den zweiten Zweig des ``||Logic:wenn ... dann ... ansonsten||``-Blocks ein.  

### ~ tutorialhint  
```blocks  
player.onChat("mach", function (AgentenBefehl) {
    if (AgentenBefehl == 1) {
        agent.teleportToPlayer()
    } else if (AgentenBefehl == 2) {
        agent.turn(TurnDirection.Left)
    } else {

    }
})
``` 

---

## Schritt 8  
Füge eine Nachricht im dritten Zweig hinzu, um dem Nutzer eine Anleitung zu geben. Ziehe einen ``||Player:sag||``-Block in den dritten Zweig des ``||Logic:wenn ... dann ... ansonsten||``-Blocks.  

### ~ tutorialhint  
```blocks  
player.onChat("mach", function (AgentenBefehl) {
    if (AgentenBefehl == 1) {
        agent.teleportToPlayer()
    } else if (AgentenBefehl == 2) {
        agent.turn(TurnDirection.Left)
    } else {
            player.say(":)")
    }
})
``` 

---

## Schritt 9  
Passe den Text im ``||Player:sag||``-Block an, sodass dort steht: **Gib 1 ein, um zu teleportieren oder 2, um zu drehen.**  

### ~ tutorialhint  
```blocks  
player.onChat("mach", function (AgentenBefehl) {
    if (AgentenBefehl == 1) {
        agent.teleportToPlayer()
    } else if (AgentenBefehl == 2) {
        agent.turn(TurnDirection.Left)
    } else {
            player.say("Gib 1 ein, um zu teleportieren oder 2, um dich zu drehen.")
    }
})
``` 

---

## Schritt 10  
Erstelle den „grabe“-Befehl. Ziehe einen neuen ``||Player:bei Chat-Befehl||``-Block in deinen Arbeitsbereich und benenne ihn in **"grabe"** um.  

---

## Schritt 11  
Um Diamanten abzubauen, musst du im Überlebensmodus spielen. Füge den ``||Gameplay:Spielmodus ändern||``-Block in den ``||Player:bei Chat-Befehl "grabe"||``-Block ein.  

---

## Schritt 12  
Passe den ``||Gameplay:Spielmodus ändern||``-Block an, indem du im Dropdown-Menü den Spieler **du selbst @s** auswählst.  

---

## Schritt 13  
Ziehe einen ``||Logic:wenn ... dann ... ansonsten||``-Block und füge ihn nach dem ``||Gameplay:Spielmodus ändern||``-Block ein.  

### ~ tutorialhint  
```blocks  
player.onChat("grabe", function () {
    gameplay.setGameMode(
    SURVIVAL,
    mobs.target(LOCAL_PLAYER)
    )
    if (true) {
    } else {
    }
})
```  

## Schritt 14  
Lass den Agenten nach Diamanten suchen. Du möchtest eine Warnung ausgeben, wenn der Agent wertvolle Blöcke wie Diamanterz findet. Ersetze **wahr** im ``||Logic:wenn ... dann ... ansonsten||``-Block durch einen ``||Logic:0 = 0||``-Vergleichsblock.  

---

## Schritt 15  
Ziehe einen ``||Agent:Agent untersuche||``-Block in das erste Feld des ``||Logic:0 = 0||``-Vergleichsblocks, sodass er die Blöcke vor dem Agenten überprüft. Ziehe dann einen ``||Blocks:Block||``-Block in das zweite Feld und wähle im Dropdown-Menü **Diamanterz** aus.  

### ~ tutorialhint  
```blocks  
player.onChat("grabe", function () {
    gameplay.setGameMode(
    SURVIVAL,
    mobs.target(LOCAL_PLAYER)
    )
    if (agent.inspect(AgentInspection.Block, FORWARD) == DIAMOND_ORE) {

    } else {

    }
})
```  

---

## Schritt 16  
Werde reich! Wenn der Agent **Diamanterz** findet, soll er eine Nachricht anzeigen und das Erz abbauen. Ziehe einen ``||Player:sag||``-Block in den ersten Zweig des ``||Logic:wenn ... dann ... ansonsten||``-Blocks und gib eine Nachricht ein, z. B. **„Wir sind reich!“**  

---

## Schritt 17  
Füge unter dem ``||Player:sag||``-Block die folgenden Blöcke in dieser Reihenfolge ein: ``||Agent:Agent zerstöre||``, ``||Agent:Agent bewege||`` und ``||Agent:Agent sammle alles||``.  

### ~ tutorialhint  
```blocks  
player.onChat("grabe", function () {
    gameplay.setGameMode(
    SURVIVAL,
    mobs.target(LOCAL_PLAYER)
    )
    if (agent.inspect(AgentInspection.Block, FORWARD) == DIAMOND_ORE) {
        player.say("Wir sind reich!")
        agent.destroy(FORWARD)
        agent.move(FORWARD, 1)
        agent.collectAll()
    } else {

    }
})
```  

---

## Schritt 18  
Zerstöre die anderen Blöcke und grabe weiter. Wenn der Agent kein Diamanterz findet, soll er den unwichtigen Block vor ihm zerstören und ohne Einsammeln weitergehen. Ziehe dafür die Blöcke ``||Agent:Agent zerstöre||`` und ``||Agent:Agent bewege||`` in den ``||Logic:ansonsten||``-Zweig.  

---

## Schritt 19  
Wiederhole diesen Vorgang **64** Mal. Ziehe eine ``||Loops:wiederhole||``-Schleife, die den ``||Logic:wenn ... dann ... ansonsten||``-Block umschließt, und setze die Zahl **64** ein.  

### ~ tutorialhint  
```blocks  
player.onChat("grabe", function () {
    gameplay.setGameMode(
    SURVIVAL,
    mobs.target(LOCAL_PLAYER)
    )
    for (let i = 0; i < 64; i++) {
        if (agent.inspect(AgentInspection.Block, FORWARD) == DIAMOND_ORE) {
            player.say("Wir sind reich!")
            agent.destroy(FORWARD)
            agent.move(FORWARD, 1)
            agent.collectAll()
        } else {
            agent.destroy(FORWARD)
            agent.move(FORWARD, 1)
        }
    }
})
```  

---

## Schritt 20  
Sorge dafür, dass der Agent zurückkommt. Nachdem der Agent **64** Blöcke abgebaut hat, soll er sich umdrehen und zurückkehren. Um das zu erreichen, ziehe eine weitere ``||Loops:wiederhole||``-Schleife um die bestehende ``||Loops:wiederhole 64||``-Schleife.  

---

## Schritt 21  
Setze in der äußeren Schleife die Zahl **2**, da der Agent zwei Reihen von Blöcken abbauen soll. Am Ende der ersten Reihe soll der Agent sich umdrehen und eine Reihe höher gehen.  

---

## Schritt 22  
Füge am Ende der inneren Schleife folgende Blöcke in dieser Reihenfolge hinzu: ``||Agent:Agent zerstöre||``, ``||Agent:Agent bewege||`` (nach oben) und zwei ``||Agent:Agent drehe||``-Blöcke (jeweils eine Richtung). Stelle sicher, dass du die Richtungen im Dropdown-Menü anpasst.  

### ~ tutorialhint  
```blocks  
player.onChat("grabe", function () {
    gameplay.setGameMode(
    SURVIVAL,
    mobs.target(LOCAL_PLAYER)
    )
    for (let j = 0; j < 2; j++) {
        for (let i = 0; i < 64; i++) {
            if (agent.inspect(AgentInspection.Block, FORWARD) == DIAMOND_ORE) {
                player.say("Wir sind reich!")
                agent.destroy(FORWARD)
                agent.move(FORWARD, 1)
                agent.collectAll()
            } else {
                agent.destroy(FORWARD)
                agent.move(FORWARD, 1)
            }
        }
        agent.destroy(UP)
        agent.move(UP, 1)
        agent.turn(TurnDirection.Left)
        agent.turn(TurnDirection.Left)
    }
})
```  

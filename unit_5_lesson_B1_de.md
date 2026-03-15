### @explicitHints 1

# Aktivität: Diamantenjagd

---

## 1. Chat-Befehl anlegen
Erstelle Steuerungen für den Agenten. Benenne den vorhandenen ``||PLAYER:bei Chat-Befehl||``-Block in **"mach"** um.  

---

## 2. Parameter hinzufügen
Du kannst ein einfaches Menü erstellen, um alle Befehle für den Agenten zu steuern. Ziehe einen ``||LOGIC:wenn ... dann ... ansonsten||``-Block in den ``||PLAYER:bei Chat-Befehl "mach"||``-Block. Klicke auf das **(+)**-Symbol im ``||LOGIC:wenn ... dann ... ansonsten||``, um einen dritten Zweig hinzuzufügen, da du drei Bedingungen testen wirst.  

---

## 3. Parameter umbenennen
Klicke auf das **(+)**-Symbol des ``||PLAYER:bei Chat-Befehl "mach"||``-Blocks und benenne **num1** in **AgentenBefehl** um.  

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

## 4. Vergleichsblöcke vorbereiten
Teste, welche Eingabe der Nutzer gemacht hat. Der Nutzer soll den Agenten teleportieren und drehen können. Der dritte Zweig gibt eine Nachricht, falls keine gültige Eingabe erfolgt. Ziehe den ``||LOGIC:0 = 0||``-Vergleichsblock und dupliziere ihn, da du zwei brauchst.  

Platziere diese Blöcke in den ``||LOGIC:wenn ... dann ... ansonsten||``-Block.  

---

## 5. Vergleichswerte festlegen
Passe die Vergleiche an, um die Eingabe des Nutzers zu testen. Der Wert von ``||VARIABLES:AgentenBefehl||`` entscheidet, was passiert. Beispielsweise könnte der Wert **1** bedeuten, dass der Agent teleportiert wird, und **2**, dass er sich drehen soll.  

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

## 6. Teleport-Aktion einfügen
Füge die Aktionen für den Agenten hinzu. Ziehe einen ``||AGENT: Agent teleportiere zu Spieler||``-Block in den ersten Zweig des ``||LOGIC:wenn ... dann ... ansonsten||``-Blocks.  

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

## 7. Dreh-Aktion einfügen
Füge einen ``||AGENT:Agent drehe||``-Block in den zweiten Zweig des ``||LOGIC:wenn ... dann ... ansonsten||``-Blocks ein.  

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

## 8. Hinweistext hinzufügen
Füge eine Nachricht im dritten Zweig hinzu, um dem Nutzer eine Anleitung zu geben. Ziehe einen ``||PLAYER:sag||``-Block in den dritten Zweig des ``||LOGIC:wenn ... dann ... ansonsten||``-Blocks.  

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

## 9. Hinweistext hinzufügen
Passe den Text im ``||PLAYER:sag||``-Block an, sodass dort steht: **Gib 1 ein, um zu teleportieren oder 2, um zu drehen.**  

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

## 10. Neuen Chat-Befehl anlegen
Erstelle den „grabe“-Befehl. Ziehe einen neuen ``||PLAYER:bei Chat-Befehl||``-Block in deinen Arbeitsbereich und benenne ihn in **"grabe"** um.  

---

## 11. Spielmodus festlegen
Um Diamanten abzubauen, musst du im Überlebensmodus spielen. Füge den ``||GAMEPLAY:Spielmodus ändern||``-Block in den ``||PLAYER:bei Chat-Befehl "grabe"||``-Block ein.  

---

## 12. Spielmodus festlegen
Passe den ``||GAMEPLAY:Spielmodus ändern||``-Block an, indem du im Dropdown-Menü den Spieler **du selbst @s** auswählst.  

---

## 13. Logik hinzufügen
Ziehe einen ``||LOGIC:wenn ... dann ... ansonsten||``-Block und füge ihn nach dem ``||GAMEPLAY:Spielmodus ändern||``-Block ein.  

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

## 14. Diamanterzsuche setzen
Lass den Agenten nach Diamanten suchen. Du möchtest eine Warnung ausgeben, wenn der Agent wertvolle Blöcke wie Diamanterz findet. Ersetze **wahr** im ``||LOGIC:wenn ... dann ... ansonsten||``-Block durch einen ``||LOGIC:0 = 0||``-Vergleichsblock.  

---

## 15. Blockprüfung konfigurieren
Ziehe einen ``||AGENT:Agent untersuche||``-Block in das erste Feld des ``||LOGIC:0 = 0||``-Vergleichsblocks, sodass er die Blöcke vor dem Agenten überprüft. Ziehe dann einen ``||BLOCKS:Block||``-Block in das zweite Feld und wähle im Dropdown-Menü **Diamanterz** aus.  

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

## 16. Diamantfund behandeln
Werde reich! Wenn der Agent **Diamanterz** findet, soll er eine Nachricht anzeigen und das Erz abbauen. Ziehe einen ``||PLAYER:sag||``-Block in den ersten Zweig des ``||LOGIC:wenn ... dann ... ansonsten||``-Blocks und gib eine Nachricht ein, z. B. **„Wir sind reich!“**  

---

## 17. Diamant abbauen und sammeln
Füge unter dem ``||PLAYER:sag||``-Block die folgenden Blöcke in dieser Reihenfolge ein: ``||AGENT:Agent zerstöre||``, ``||AGENT:Agent bewege||`` und ``||AGENT:Agent sammle alles||``.  

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

## 18. Standardabbau festlegen
Zerstöre die anderen Blöcke und grabe weiter. Wenn der Agent kein Diamanterz findet, soll er den unwichtigen Block vor ihm zerstören und ohne Einsammeln weitergehen. Ziehe dafür die Blöcke ``||AGENT:Agent zerstöre||`` und ``||AGENT:Agent bewege||`` in den ``||LOGIC:ansonsten||``-Zweig.  

---

## 19. Abbau-Schleife setzen
Wiederhole diesen Vorgang **64** Mal. Ziehe eine ``||LOOPS:wiederhole||``-Schleife, die den ``||LOGIC:wenn ... dann ... ansonsten||``-Block umschließt, und setze die Zahl **64** ein.  

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

## 20. Rückweg-Schleife ergänzen
Sorge dafür, dass der Agent zurückkommt. Nachdem der Agent **64** Blöcke abgebaut hat, soll er sich umdrehen und zurückkehren. Um das zu erreichen, ziehe eine weitere ``||LOOPS:wiederhole||``-Schleife um die bestehende ``||LOOPS:wiederhole 64||``-Schleife.  

---

## 21. Reihenanzahl festlegen
Setze in der äußeren Schleife die Zahl **2**, da der Agent zwei Reihen von Blöcken abbauen soll. Am Ende der ersten Reihe soll der Agent sich umdrehen und eine Reihe höher gehen.  

---

## 22. Reihenwechsel einbauen
Füge am Ende der inneren Schleife folgende Blöcke in dieser Reihenfolge hinzu: ``||AGENT:Agent zerstöre||``, ``||AGENT:Agent bewege||`` (nach oben) und zwei ``||AGENT:Agent drehe||``-Blöcke (jeweils eine Richtung). Stelle sicher, dass du die Richtungen im Dropdown-Menü anpasst.  

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

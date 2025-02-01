### @explicitHints 1  
# Aktivität: Maze Pathfinding

## Schritt 1  
Verwende den bereitgestellten Einstiegscode aus der **Einführung in die Agent**-Aktivität:

```template
player.onChat("tp", function () {
    agent.teleportToPlayer()
})
player.onChat("fd", function () {
    agent.move(SixDirection.Forward, 1)
})
player.onChat("lt", function () {
    agent.turn(TurnDirection.Left)
})
player.onChat("bk", function () {
    agent.move(SixDirection.Back, 1)
})
player.onChat("rt", function () {
    agent.turn(TurnDirection.Right)
})
```

---

## Schritt 2  
Nutze die grundlegenden Agentensteuerungen, um den Agenten zum Startpunkt des Labyrinths zu bewegen. Bewege deinen Spieler an den Anfang des Labyrinths und gib den Befehl **"tp"** in das Chatfenster ein – dein Agent sollte sich dorthin teleportieren. Anschließend drehst du den Agenten mit **"lt"** (links) oder **"rt"** (rechts), damit er in das Labyrinth hineinblickt.

---

## Schritt 4  
Erstelle einen **Player:Bei Chat-Befehl**-Block und benenne ihn in **"mr"** um (mr steht für Maze Runner, also Labyrinthläufer).

Platziere den gesamten Algorithmus in einer **Loops:während**-Schleife, die deinem Agenten sagt, dass er weiter nach dem Ende des Labyrinths suchen soll, solange er nicht auf **Redstone** steht. Ziehe dazu aus **Loops:SCHLEIFEN** einen **Loops:während**-Block in deinen **Player:Bei Chat-Befehl "mr"**-Block.

---

## Schritt 5  
Platziere einen **Logic:nicht**-Block in der **Loops:während**-Schleife und ersetze darin den Standardwert „true“.

---

## Schritt 6  
Ziehe einen **Agent:Agent, erkenne**-Block in den **Logic:nicht**-Block hinein.

Im **Agent:Agent, erkenne**-Block wählst du im Dropdown-Menü **Redstone** als den zu erkennenden Blocktyp aus und stellst die Richtung auf **nach unten** ein.

### ~ tutorialhint
``` blocks
player.onChat("mr", function () {
    while (!(agent.detect(AgentDetection.Redstone, DOWN))) {
    }
})
```

---

## Schritt 7  
Überprüfe, ob links ein freier Weg vorhanden ist. Als Nächstes schauen wir, ob ein Weg nach links offen ist – falls ja, soll der Agent nach links abbiegen und sich vorwärts bewegen. Ziehe dazu einen **Logic:wenn dann ansonsten**-Block in die **Loops:während**-Schleife.

---

## Schritt 8  
Ziehe einen **Logic:nicht**-Block in den bedingten Bereich (das „wenn“-Feld) des **Logic:wenn dann ansonsten**-Blocks und ersetze darin den Standardwert **wahr**.

---

## Schritt 9  
Ziehe einen **Agent:Agent, erkenne**-Block in den **Logic:nicht**-Block hinein.

---

## Schritt 10  
Im **Agent:Agent, erkenne**-Block wählst du im Dropdown-Menü **links** als die Richtung aus, in die geschaut werden soll.

### ~ tutorialhint
``` blocks
player.onChat("mr", function () {
    while (!(agent.detect(AgentDetection.Redstone, DOWN))) {
        if (!(agent.detect(AgentDetection.Block, LEFT))) {

        } else {

        }
    }
})
```

---

## Schritt 11  
Drehe den Agenten nach links und bewege ihn vorwärts. Wenn der Agent keinen Block auf seiner linken Seite erkennt, soll er nach links abbiegen und sich vorwärts bewegen. Ziehe dazu einen **Agent:Agent, drehe dich**-Block und einen **Agent:Agent, bewege dich**-Block in den ersten Ast deines **Logic:wenn dann**-Blocks.

---

## Schritt 12  
Prüfe, ob ein Weg vorwärts oder rechts frei ist. Füge dazu zwei weitere Bedingungen hinzu, um zu überprüfen, ob der Weg vor oder rechts des Agenten frei ist. Klicke dazu zweimal auf das Pluszeichen **(+)** unten im **Logic:wenn dann ansonsten**-Block, um zwei zusätzliche **Logic:sonst wenn dann**-Klauseln hinzuzufügen.

### ~ tutorialhint
``` blocks
player.onChat("mr", function () {
    while (!(agent.detect(AgentDetection.Redstone, DOWN))) {
        if (!(agent.detect(AgentDetection.Block, LEFT))) {

        } else if (false) {

        } else if (false) {

        } else {

        }
    }
})
```

---

## Schritt 13  
Dupliziere den **Logic:nicht**-Block aus dem ersten Bedingungsfeld des **Logic:wenn dann**-Blocks. Klicke mit der rechten Maustaste auf diesen Block und wähle „Duplizieren“ – wiederhole dies zweimal, um zwei weitere **Logic:nicht**-Blöcke (mit **Agent:Agent, erkenne**) zu erstellen. Platziere diese duplizierten Blöcke in den beiden zusätzlichen **Logic:sonst wenn dann**-Feldern.

---

## Schritt 14  
Im zweiten Ast des **Logic:sonst wenn dann**-Blocks wählst du im Dropdown-Menü **vorwärts** als die Richtung aus, die überprüft werden soll. Damit prüfst du zuerst links und dann vorwärts.

---

## Schritt 15  
Im dritten Ast des **Logic:sonst wenn dann**-Blocks wählst du im Dropdown-Menü **rechts** als die Richtung aus, die überprüft werden soll. Damit prüfst du zuerst links, dann vorwärts und schließlich rechts.

### ~ tutorialhint
``` blocks
player.onChat("mr", function () {
    while (!(agent.detect(AgentDetection.Redstone, DOWN))) {
        if (!(agent.detect(AgentDetection.Block, LEFT))) {
            agent.turn(TurnDirection.Left)
            agent.move(FORWARD, 1)
        } else if (!(agent.detect(AgentDetection.Block, FORWARD))) {
        } else if (!(agent.detect(AgentDetection.Block, RIGHT))) {
        } else {
        }
    }
})
```

---

## Schritt 16  
Bewege den Agenten vorwärts. Wenn er vor sich keinen Block erkennt, soll er einfach vorwärts gehen. Ziehe dazu einen **Agent:Agentenbewegung**-Block in den zweiten Ast der **Logic:sonst wenn dann**-Klausel.

---

## Schritt 17  
Bewege den Agenten nach rechts. Wenn er auf seiner rechten Seite keinen Block erkennt, soll er nach rechts abbiegen und sich vorwärts bewegen.

---

## Schritt 18  
Ziehe in den dritten Ast der **Logic:sonst wenn dann**-Klausel einen **Agent:Agent, drehe dich nach**-Block und einen **Agent:Agent, bewege dich**-Block hinein.

---

## Schritt 19  
Im **Agent:Agent, drehe dich nach**-Block wählst du im Dropdown-Menü **rechts** als Drehrichtung aus.

---

## Schritt 20  
Du kannst diese Blöcke auch duplizieren – das ist vollkommen in Ordnung!

### ~ tutorialhint
``` blocks
player.onChat("mr", function () {
    while (!(agent.detect(AgentDetection.Redstone, DOWN))) {
        if (!(agent.detect(AgentDetection.Block, LEFT))) {
            agent.turn(TurnDirection.Left)
            agent.move(FORWARD, 1)
        } else if (!(agent.detect(AgentDetection.Block, FORWARD))) {
            agent.move(FORWARD, 1)
        } else if (!(agent.detect(AgentDetection.Block, RIGHT))) {
            agent.turn(TurnDirection.Right)
            agent.move(FORWARD, 1)
        } else {
        }
    }
})
```

---

## Schritt 21  
Drehe den Agenten um und lasse ihn rückwärts gehen. Wenn der Agent in einer Sackgasse steckt (also keine der drei Richtungen frei ist), soll er sich umdrehen und in die entgegengesetzte Richtung zurückgehen. Ziehe dazu aus **Agent:AGENT** die folgenden drei Blöcke in den letzten **Logic:ansonsten**-Ast: zwei **Agent:Agent, drehe dich**-Blöcke und einen **Agent:Agentenbewegung**-Block.

### ~ tutorialhint
``` blocks
player.onChat("mr", function () {
    while (!(agent.detect(AgentDetection.Redstone, DOWN))) {
        if (!(agent.detect(AgentDetection.Block, LEFT))) {
            agent.turn(TurnDirection.Left)
            agent.move(FORWARD, 1)
        } else if (!(agent.detect(AgentDetection.Block, FORWARD))) {
            agent.move(FORWARD, 1)
        } else if (!(agent.detect(AgentDetection.Block, RIGHT))) {
            agent.turn(TurnDirection.Right)
            agent.move(FORWARD, 1)
        } else {
            agent.turn(TurnDirection.Left)
            agent.turn(TurnDirection.Left)
            agent.move(FORWARD, 1)
        }
    }
})
```

---

## Schritt 22  
Redstone gefunden! Sobald der Agent Redstone erkennt, weiß er, dass er das Ziel erreicht hat. Du kannst den Agenten am Ende des Labyrinths einen Freudentanz machen lassen – verwende dazu gerne den Code aus der **Tanz Tanz Agent**-Aktivität in **Lektion 7: Iteration**.

---

## Schritt 23  
Um den Code für den **Player:Bei Chat-Befehl "tanz"** auszuführen, platziere einen **Player:führe Chat-Befehl aus ""**-Block aus **Player:SPIELER** unterhalb und außerhalb der **Loops:während**-Schleife. Der Block sollte lauten **Player:führe Chat-Befehl aus "tanz"**, wenn du fertig bist.  
**Hinweis:** Die Verwendung von **Player:führe Chat-Befehl aus "tanz"** ist wie ein Funktionsaufruf – du könntest hier auch eine Funktion verwenden, wenn du möchtest.

### ~ tutorialhint
``` blocks
player.onChat("fd", function () {
    agent.move(FORWARD, 1)
})
player.onChat("lt", function () {
    agent.turn(TurnDirection.Left)
})
player.onChat("bk", function () {
    agent.move(BACK, 1)
})
player.onChat("rt", function () {
    agent.turn(TurnDirection.Right)
})
player.onChat("tp", function () {
    agent.teleportToPlayer()
})
player.onChat("mr", function () {
    while (!(agent.detect(AgentDetection.Redstone, DOWN))) {
        if (!(agent.detect(AgentDetection.Block, LEFT))) {
            agent.turn(TurnDirection.Left)
            agent.move(FORWARD, 1)
        } else if (!(agent.detect(AgentDetection.Block, FORWARD))) {
            agent.move(FORWARD, 1)
        } else if (!(agent.detect(AgentDetection.Block, RIGHT))) {
            agent.turn(TurnDirection.Right)
            agent.move(FORWARD, 1)
        } else {
            agent.turn(TurnDirection.Left)
            agent.turn(TurnDirection.Left)
            agent.move(FORWARD, 1)
        }
    }
    player.runChatCommand("dance")
})
player.onChat("dance", function () {
    for (let i = 0; i < 4; i++) {
        agent.move(LEFT, 1)
        agent.attack(FORWARD)
        agent.move(RIGHT, 1)
        agent.move(RIGHT, 1)
        agent.move(LEFT, 1)
    }
})
```

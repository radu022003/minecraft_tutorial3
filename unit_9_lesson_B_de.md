### @explicitHints 1
# Aktivität: Maze Pathfinding

## Schritt 1
Verwenden Sie den bereitgestellten Einstiegscode aus der **Einführung in die Agent**-Aktivität.

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

## Schritt 2
Lassen Sie uns die grundlegenden Agentensteuerungen verwenden, um den Agenten zum Startpunkt des Labyrinths zu bewegen. Bewegen Sie Ihren Spieler zum Anfang des Labyrinths. Geben Sie den Befehl "tp" in das Chatfenster ein. Ihr Agent sollte dorthin teleportieren. Dann müssen Sie den Agenten nach links ("lt") oder rechts ("rt") drehen, um ihn nach innen zu richten.

## Schritt 4
Erstellen Sie einen ``||Player:Bei Chat-Befehl||`` Block und benennen Sie ihn in **"mr"** um, was für Labyrinthläufer steht.

Sie werden den gesamten Algorithmus in einer ``||Loops:während||`` Schleife platzieren, die Ihrem Agenten sagt, weiter nach dem Ende des Labyrinths zu suchen, solange er nicht auf **Redstone** steht. Ziehen Sie aus ``||Loops:SCHLEIFEN||`` eine ``||Loops:während||`` Schleife in ``||Player:Bei Chat-Befehl "mr"||``.

## Schritt 5
Platzieren Sie einen ``||Logic:nicht||`` Block in die ``||Loops:während||`` Schleife und ersetzen Sie das "true".

## Schritt 6
Ziehen Sie einen ``||Agent:Agent, erkenne||`` Block in das ``||Logic:nicht||``.

Im ``||Agent:Agent, erkenne||`` Block verwenden Sie das Dropdown-Menü, um **Redstone** als den zu erkennenden Blocktyp auszuwählen.

Im ``||Agent:Agent, erkenne||`` Block verwenden Sie das Dropdown-Menü, um **nach unten** als die Richtung auszuwählen.

### ~ tutorialhint
``` blocks
player.onChat("mr", function () {
    while (!(agent.detect(AgentDetection.Redstone, DOWN))) {
    }
})
```

## Schritt 7
Überprüfen Sie einen Pfad nach links. Als nächstes werden wir überprüfen, ob ein Weg nach links offen ist, und wenn ja, nach links abbiegen und nach vorne bewegen.

Ziehen Sie ein ``||Logic:wenn dann ansonsten||`` Befehl in die ``||Loops:während||`` Schleife.

## Schritt 8
Ziehen Sie einen ``||Logic:nicht||`` Block in den bedingten Steckplatz von ``||Logic:wenn dann||`` und ersetzen Sie den **wahr** Block.

## Schritt 9
Ziehen Sie einen ``||Agent:Agent, erkenne||`` Block in den ``||Logic:nicht||`` Block.

## Schritt 10
Im ``||Agent:Agent, erkenne||`` Block verwenden Sie das Dropdown-Menü, um **links** als die Richtung auszuwählen, in die geschaut werden soll.Im ``||Agent:Agent, erkenne||`` Block verwenden Sie das Dropdown-Menü, um **links** als die Richtung auszuwählen, in die geschaut werden soll.

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

## Schritt 11
Drehen Sie sich nach links und bewegen Sie sich vorwärts. Wenn der Agent keinen Block auf seiner linken Seite erkennt, möchten wir, dass der Agent nach links abbiegt und sich vorwärts bewegt. Ziehen Sie einen ``||Agent:Agent, drehe dich||`` und einen ``||Agent:Agent, bewege dich||`` Befehl in den ersten Ast Ihres ``||Logic:wenn dann||``.

## Schritt 12
Überprüfen Sie einen Weg nach vorne oder rechts. Nun müssen wir zwei weitere Bedingungen hinzufügen, um nach vorne und nach rechts des Agenten zu überprüfen. Klicken Sie zweimal auf das Pluszeichen **(+)** unten im "Wenn dann sonst" Block, um 2 weitere ``||Logic:sonst wenn dann||`` Klauseln hinzuzufügen.

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

## Schritt 13
Duplizieren Sie Bedingungen für die anderen Zweige Ihres Falls. Klicken Sie mit der rechten Maustaste auf den ``||Logic:nicht||`` Block im ersten Wenn-dann-Bedingungsfeld und wählen Sie Duplizieren aus – tun Sie dies zweimal, um zwei weitere ``||Logic:nicht||`` ``||Agent:Agent, erkenne||`` Bedingungen zu erstellen.

Platzieren Sie diese duplizierten Bedingungen in die beiden zusätzlichen ``||Logic:sonst wenn dann||`` Steckplätze.

## Schritt 14
Im zweiten Ast des ``||Logic:sonst wenn dann||`` verwenden Sie das Dropdown-Menü, um **vorwärts** als die Richtung auszuwählen, die überprüft werden soll. Damit überprüfen wir zuerst links und dann vorwärts.

## Schritt 15
Im dritten Ast des ``||Logic:sonst wenn dann||`` verwenden Sie das Dropdown-Menü, um **rechts** als die Richtung auszuwählen, die überprüft werden soll. Damit überprüfen wir zuerst links, dann vorwärts und dann rechts.

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

## Schritt 16
Bewegen Sie sich vorwärts. Wenn der Agent keinen Block vor sich erkennt, sollte er einfach vorwärts gehen. Ziehen Sie aus ``||Agent:AGENT||`` einen ``||Agent:Agentenbewegung||`` Block in den zweiten Ast der ``||Logic:else if||`` Klausel.

## Schritt 17
Bewegen Sie sich nach rechts. Wenn der Agent keinen Block auf seiner rechten Seite erkennt, sollte der Agent nach rechts abbiegen und sich vorwärts bewegen.

## Schritt 18
Ziehen Sie einen ``||Agent:Agent, drehe dich nach||`` und einen ``||Agent:Agent, drehe dich nach||`` Block in den dritten Ast der ``||Logic:else if||`` Klausel.

## Schritt 19
Im ``||Agent:Agent, drehe dich nach||`` Block verwenden Sie das Dropdown-Menü, um **rechts** als die Richtung auszuwählen, in die gedreht werden soll.

## Schritt 20
Sie können auch einfach diese Blöcke duplizieren. Das ist vollkommen in Ordnung!

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

## Schritt 21
Drehen Sie sich um und gehen Sie rückwärts. Schließlich, wenn der Agent an einer Sackgasse ist (keine der drei Richtungen ist offen), möchten Sie, dass der Agent sich umdreht und in die entgegengesetzte Richtung zurückkehrt. Ziehen Sie aus ``||Agent:AGENT||`` die folgenden 3 Blöcke in die letzte ``||Logic:ansonsten||`` Klausel: 2 Agentendrehungsblöcke und einen ``||Agent:Agent, drehe dich nach||`` Block.

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

## Schritt 22
Gefunden das Redstone! Wenn der Agent Redstone erkennt, wird er wissen, dass er das Ziel erreicht hat. Sie können den Agenten am Ende des Labyrinths einen Freudentanz machen lassen! Sie können gerne den Code aus der **Tanz Tanz Agent** Aktivität in **Lektion 7: Iteration** wiederverwenden.

## Schritt 23
Um den Code für ``||Player:Bei Chat-Befehl "tanz"||`` auszuführen, platzieren Sie einen ``||Player:führe Chat-Befehl aus ""||`` Block von ``||Player:SPIELER||`` unterhalb und außerhalb der ``||Loops:während||`` Schleife. Es sollte ``||Player:führe Chat-Befehl aus "tanz"||`` lauten, wenn Sie fertig sind. **Die Verwendung von ``||Player:führe Chat-Befehl aus "tanz"||`` ist wie das Aufrufen einer Funktion. Sie könnten hier stattdessen eine Funktion verwenden, wenn Sie möchten**.


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

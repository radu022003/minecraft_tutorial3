Nachgedacht für eine Sekunde


Entschuldige, das passe ich an und achte darauf, dass alle „`||…||`“-Blöcke genau erhalten bleiben:

---

### @explicitHints 1

# Aktivität: Maze Pathfinding

## Schritt 1

Verwende den bereitgestellten Starter-Code aus der **Einführung in die Agent**-Aktivität:

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

Nutze die grundlegenden Agenten-Steuerungen, um den Agenten zum Startpunkt des Labyrinths zu bewegen.

1. Bewege deinen Spieler an den Labyrinth-Eingang.
2. Tippe im Chat **"tp"** ein – dein Agent teleportiert sich zu dir.
3. Drehe den Agenten mit **"lt"** (links) oder **"rt"** (rechts), damit er ins Labyrinth schaut.

---

## Schritt 3

Erstelle einen `||Player:Bei Chat-Befehl||`-Block und benenne ihn in **"mr"** um (mr = Maze Runner).
Ziehe aus `||Loops:SCHLEIFEN||` einen `||Loops:während||`-Block in deinen `||Player:Bei Chat-Befehl "mr"||`-Block.
So sucht dein Agent weiter, bis er unter sich **Redstone** erkennt.

---

## Schritt 5

Platziere einen `||Logic:nicht||`-Block in die `||Loops:während||`-Schleife und ersetze darin den Standardwert **falsch** damit.

---

## Schritt 6

Ziehe einen `||Agent:Agent erkenne||`-Block in den `||Logic:nicht||`-Block.

* Wähle im Dropdown **Redstone** als zu erkennenden Block-Typ.
* Wähle **nach unten** als Richtung.

### ~ tutorialhint

```blocks
player.onChat("mr", function () {
    while (!(agent.detect(AgentDetection.Redstone, DOWN))) {
    }
})
```

---

## Schritt 7

Prüfe, ob links ein Weg frei ist.
Ziehe einen `||Logic:wenn dann ansonsten||`-Block in deine `||Loops:während||`-Schleife.

---

## Schritt 8

Platziere einen `||Logic:nicht||`-Block im **wenn**-Feld des `||Logic:wenn dann ansonsten||`-Blocks und ersetze dort **wahr**.

---

## Schritt 9

Ziehe einen weiteren `||Agent:Agent erkenne||`-Block in den neuen `||Logic:nicht||`-Block.

---

## Schritt 10

Im `||Agent:Agent erkenne||`-Block wähle im Dropdown **links** als Richtung.

### ~ tutorialhint

```blocks
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

Wenn links frei ist, soll der Agent nach links drehen und einen Schritt vorwärts machen.
Ziehe hierfür einen `||Agent:Agent drehe dich||`- und einen `||Agent:Agent bewege dich||`-Block in den **wenn**-Ast deines `||Logic:wenn dann ansonsten||`.

---

## Schritt 12

Prüfe nun auch vorwärts und rechts:
Klicke zweimal auf das **(+)-Symbol** im `||Logic:if then else||`-Block, um zwei **else if**-Klauseln hinzuzufügen.

### ~ tutorialhint

```blocks
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

Dupliziere den `||Logic:nicht||`-Block aus dem ersten **wenn**-Ast zweimal (Rechtsklick → Duplizieren).
Platziere die Duplikate in die beiden **sonst wenn**-Felder.

---

## Schritt 14

Im zweiten **sonst wenn**-Ast wähle im `||Agent:Agent erkenne||`-Block **vorwärts** als Richtung.

---

## Schritt 15

Im dritten **sonst wenn**-Ast wähle **rechts** als Richtung.

### ~ tutorialhint

```blocks
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

Wenn vorwärts frei ist, ziehe einen weiteren `||Agent:Agent bewege||`-Block in den zweiten **sonst wenn**-Ast, damit der Agent einfach vorwärts geht.

Wenn rechts frei ist, soll der Agent nach rechts drehen und vorwärts gehen.
Ziehe einen weiteren `||Agent:Agent drehe||`- und einen `||Agent:Agent bewege dich||`-Block in den dritten **sonst wenn**-Ast.
Im `||Agent:Agent drehe dich||`-Block wähle **rechts** als Drehrichtung.

Du kannst diese Blöcke auch duplizieren – das ist völlig in Ordnung!

### ~ tutorialhint

```blocks
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

## Schritt 17

Wenn alle drei Richtungen blockiert sind (Sackgasse), soll der Agent umdrehen und rückwärts gehen.
Ziehe dazu in den **ansonsten**-Ast des `||Logic:wenn dann ansonsten||` aus  `||Agent:Agent||` zwei `||Agent:agent drehe dich||`-Blöcke und einen `||Agent:agent bewege dich||`-Block.

### ~ tutorialhint

```blocks
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

## Schritt 18

Redstone gefunden! Sobald der Agent **Redstone** unter sich erkennt, weiß er, dass er das Ziel erreicht hat.
Du kannst ihn am Ende einen Freudentanz aufführen lassen – verwende dazu bespielsweise Code aus der **Tanze Tanze Agent**-Aktivität in **Lektion 5: Iteration**.

---

## Schritt 19

Um den Tanz auszulösen, füge außerhalb der `||Loops:während||`-Schleife einen `||Player:führe Chatbefehl aus""||`-Block ein und stelle ihn auf **"dance"**:

* Ziehe aus `||Player:Spieler||` den Block `||Player:führe Chatbefehl aus""||` unter deine während-Schleife.
* Ändere das leere Feld auf **"dance"**.

> Die Verwendung von `||Player:führe Chatbefehl "dance" aus""|| ist wie ein Funktionsaufruf – du könntest auch eine Funktion verwenden.

### \~ tutorialhint

```blocks
player.onChat("mr", function () {
    while (!(agent.detect(AgentDetection.Redstone, DOWN))) {
        // … Pfadfindungs-Logik …
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

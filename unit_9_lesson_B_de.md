### @explicitHints 1

# Aktivität: Maze-Runner

## 1. Maze-Runner mit Starter-Code

Verwende den bereitgestellten Starter-Code aus der **Einführung in die Agent**-Aktivität:

```template
player.onChat("tp", function () {
    agent.teleportToPlayer()
})
player.onChat("lt", function () {
    agent.turn(TurnDirection.Left)
})
```

---

## 2. Agent zum Labyrinth-Eingang bewegen

Nutze die grundlegenden Agenten-Steuerungen, um den Agenten zum Startpunkt des Labyrinths zu bewegen.

1. Bewege deinen Spieler an den Labyrinth-Eingang.
2. Tippe im Chat **"tp"** ein – dein Agent teleportiert sich zu dir.
3. Drehe den Agenten mit **"lt"**, damit er ins Labyrinth schaut.

---

## 3. Maze-Runner-Befehl erstellen

Erstelle einen `||PLAYER:Bei Chat-Befehl||`-Block und benenne ihn in **"mr"** um (mr = Maze Runner).
Ziehe aus `||LOOPS:SCHLEIFEN||` einen `||LOOPS:während||`-Block in deinen `||PLAYER:Bei Chat-Befehl "mr"||`-Block.

---

## 4. Schleifenbedingung setzen

Platziere einen `||LOGIC:nicht||`-Block in die `||LOOPS:während||`-Schleife und ersetze darin den Standardwert **falsch** damit.

---

## 5. Redstone-Prüfung einbauen

Ziehe einen `||AGENT:Agent erkenne||`-Block in den `||LOGIC:nicht||`-Block.

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

## 6. Linken Weg prüfen

Prüfe, ob links ein Weg frei ist.
Ziehe einen `||LOGIC:wenn dann ansonsten||`-Block in deine `||LOOPS:während||`-Schleife.

---

## 7. Negation für Wegprüfung

Platziere einen `||LOGIC:nicht||`-Block im **wenn**-Feld des `||LOGIC:wenn dann ansonsten||`-Blocks und ersetze dort **wahr**.

---

## 8. Zweiten Erkennungsblock einfügen

Ziehe einen weiteren `||AGENT:Agent erkenne||`-Block in den neuen `||LOGIC:nicht||`-Block.

---

## 9. Auswahl treffen

Im `||AGENT:Agent erkenne||`-Block wähle im Dropdown **links** als Richtung.

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

## 10. Drehung einrichten

Wenn links frei ist, soll der Agent nach links drehen und einen Schritt vorwärts machen.
Ziehe hierfür einen `||AGENT:Agent drehe dich||`- und einen `||AGENT:Agent bewege dich||`-Block in den **wenn**-Ast deines `||LOGIC:wenn dann ansonsten||`.

---

## 11. Sonst-wenn-Zweige hinzufügen

Prüfe nun auch vorwärts und rechts:
Klicke zweimal auf das **(+)-Symbol** im `||LOGIC:wenn dann ansonsten||`-Block, um zwei **sonst wenn**-Klauseln hinzuzufügen.

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

## 12. Bedingungen duplizieren

Dupliziere den `||LOGIC:nicht||`-Block aus dem ersten **wenn**-Ast zweimal (Rechtsklick → Duplizieren).
Platziere die Duplikate in die beiden **sonst wenn**-Felder.

---

## 13. Bedingung konfigurieren

Im zweiten **sonst wenn**-Ast wähle im `||AGENT:Agent erkenne||`-Block **vorwärts** als Richtung.

---

## 14. Chat-Befehl erstellen

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

## 15. Bedingung konfigurieren

Wenn vorwärts frei ist, ziehe einen weiteren `||AGENT:Agent bewege||`-Block in den zweiten **sonst wenn**-Ast, damit der Agent einfach vorwärts geht.

Wenn rechts frei ist, soll der Agent nach rechts drehen und vorwärts gehen.
Ziehe einen weiteren `||AGENT:Agent drehe||`- und einen `||AGENT:Agent bewege dich||`-Block in den dritten **sonst wenn**-Ast.
Im `||AGENT:Agent drehe dich||`-Block wähle **rechts** als Drehrichtung.

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

## 16. Drehung einrichten

Wenn alle drei Richtungen blockiert sind (Sackgasse), soll der Agent umdrehen und rückwärts gehen.
Ziehe dazu in den **ansonsten**-Ast des `||LOGIC:wenn dann ansonsten||` aus  `||AGENT:Agent||` zwei `||AGENT:agent drehe dich||`-Blöcke und einen `||AGENT:agent bewege dich||`-Block.

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

## 17. Zielerkennung abschließen
Sobald der Agent **Redstone** unter sich erkennt, weiß er, dass er das Ziel erreicht hat.
Du kannst ihn am Ende einen Freudentanz aufführen lassen 

---

## 18. Tanzbefehl auslösen

Um den Tanz auszulösen, füge außerhalb der `||LOOPS:während||`-Schleife einen `||PLAYER:führe Chatbefehl aus""||`-Block ein und stelle ihn auf **"dance"**:

* Ziehe aus `||PLAYER:Spieler||` den Block `||PLAYER:führe Chatbefehl aus""||` unter deine während-Schleife.
* Ändere das leere Feld auf **"dance"**.

> Die Verwendung von  `||PLAYER:führe Chatbefehl "dance" aus""||` ist wie ein Funktionsaufruf – du könntest auch eine Funktion verwenden.

### ~ tutorialhint

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

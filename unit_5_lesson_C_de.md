### @explicitHints 1

# Aktivität: Pyramide

## Schritt 1
Kopiere den Starter-Code. Kopiere den Code aus dem Hinweis.

### ~ tutorialhint
```javascript
player.onChat("tp", function () {
        player.teleport(positions.create(3, 0, 3))
        agent.teleportToPlayer() 
        player.teleport(positions.create(-3, 0, -3)) 
}) 
player.onChat("pyramid", function (BaseSize) {
        agent.setAssist(AgentAssist.PlaceOnMove, true)
        for (let i = 0; i <= 3; i++) {
                agent.move(SixDirection.Forward, BaseSize - 1)
                agent.turn(TurnDirection.Left)
        } 
        agent.move(SixDirection.Up, 1)
        agent.setAssist(AgentAssist.PlaceOnMove, false)
        agent.move(SixDirection.Forward, 1)
        player.runChatCommand("pyramid " + (BaseSize - 2))
})
player.onChat("turn", function () {
        agent.turn(TurnDirection.Left)
})
```

## Schritt 2
Führe den Code aus und untersuche das Problem mit dem Starter-Code. Wenn du diesen Code genau so ausführst, wirst du etwas Merkwürdiges bemerken.

## Schritt 3
Rüste deinen Agenten mit einigen Blöcken aus.

Gib im Chatfenster **tp** ein, um deinen Agenten in deine Nähe zu teleportieren. Möglicherweise möchtest du auch deinen Agenten mit dem Drehbefehl drehen, aber das ist eventuell nicht nötig.

## Schritt 4
Gib **pyramid 5** im Chatfenster ein und sieh, was passiert. Dein Agent sollte die Pyramide problemlos bauen, aber er wird nicht aufhören. Der Agent baut einfach immer weiter. Dein Code ist in einer Endlosschleife! Dies passiert, weil am Ende des Codes ein Block steht, der den Code immer wieder aufruft.

### ~ tutorialhint
``` javascript
let BaseSize = 0
player.runChatCommand("pyramid " + (BaseSize - 2))
```

## Schritt 5
Füge **If-Anweisungen** hinzu. Deine Aufgabe ist es, einige **If-Anweisungen** in den Code einzufügen, um das endlose Verhalten zu stoppen!

### ~ tutorialhint
Wenn du in einer Endlosschleife steckst, musst du deinen Code aus dem Verbindungsfenster stoppen. Klicke auf die Stopp-Taste in der unteren linken Ecke des Code-Verbindungsfensters.

## Schritt 6
Beende die Schleife. Um die Schleife zu stoppen, musst du eine Variable überprüfen und dem Code sagen, dass er die Schleife stoppen soll. Eine If-Anweisung ist in dieser Situation sehr hilfreich. Ziehe einen ``||Logic:if then else||``-Block in deinen Code, sodass die **If-Anweisung** den gesamten Code innerhalb von ``||Player:bei Chat-Befehl "pyramid"||`` umgibt.

### ~ tutorialhint
```javascript
player.onChat("pyramid", function (BaseSize) {
    if (true) {
        agent.setAssist(PLACE_ON_MOVE, true)
        for (let i = 0; i <= 3; i++) {
            agent.move(FORWARD, BaseSize - 1)
            agent.turn(TurnDirection.Left)
        }
        agent.move(UP, 1)
        agent.setAssist(PLACE_ON_MOVE, false)
        agent.move(FORWARD, 1)
        player.runChatCommand("pyramid " + (BaseSize - 2))
    } else {

    }
})
```

## Schritt 7
Jetzt fügen wir die Bedingung hinzu. Du möchtest, dass die Schleife stoppt, wenn die **Größe** unter **null** geht. Der Benutzer gibt eine Größe ein, und nach jedem Durchlauf des Codes wird die Größe um **2** verringert. Genau hier passiert das.

```javascript
let BaseSize = 0
player.runChatCommand("pyramid " + (BaseSize - 2))
```

## Schritt 8
Greife einen der Befehle ``||Logic:0 = 0"||`` oder ``||Logic:0 < 0"||`` und platziere ihn in deiner ``||Logic:if then else||``.

### ~ tutorialhint
```javascript
let MadePyramid = false
player.onChat("pyramid", function (BaseSize) {
    // Überprüfe, ob wir mit dem Bau der Pyramide fortfahren sollen
    if (BaseSize > 0) {
        agent.setAssist(PLACE_ON_MOVE, true)
        // Baut eine Ebene der Pyramide
        for (let i = 0; i <= 3; i++) {
            agent.move(FORWARD, BaseSize - 1)
            agent.turn(TurnDirection.Left)
        }
        agent.move(UP, 1)
        agent.setAssist(PLACE_ON_MOVE, false)
        agent.move(FORWARD, 1)
        MadePyramid = true
        player.runChatCommand("pyramid " + (BaseSize - 2))
    } else {

    }
})
```

## Schritt 9
Du möchtest, dass der Vergleich **'BaseSize > 0'** lautet. Wenn die Größe größer als null ist, bauen wir etwas, aber wenn nicht, gibst du dem Benutzer eine Nachricht.

### ~ tutorialhint
```javascript
let MadePyramid = false
player.onChat("pyramid", function (BaseSize) {
    // Überprüfe, ob wir mit dem Bau der Pyramide fortfahren sollen
    if (BaseSize > 0) {
        agent.setAssist(PLACE_ON_MOVE, true)
        // Baut eine Ebene der Pyramide
        for (let i = 0; i <= 3; i++) {
            agent.move(FORWARD, BaseSize - 1)
            agent.turn(TurnDirection.Left)
        }
        agent.move(UP, 1)
        agent.setAssist(PLACE_ON_MOVE, false)
        agent.move(FORWARD, 1)
        MadePyramid = true
        player.runChatCommand("pyramid " + (BaseSize - 2))
    } else {

    }
})
```

## Schritt 10
Mit dieser If-Anweisung hast du die Schleife gestoppt! Wie könntest du diesen Code noch verbessern? Es gibt zwei Situationen, in denen die Größe null wird. Wenn der Agent gerade eine Pyramide gebaut hat oder der Benutzer vergessen hat, eine Größe für die Pyramide einzugeben. Der Code wird zum Else-Punkt im ``||Logic: If Then||``-Block gehen, wenn dies passiert.

## Schritt 11
Kannst du eine Möglichkeit finden, diese beiden Bedingungen (A und B) zu überprüfen? Du würdest dies im Else-Zweig überprüfen. Schau dir unseren finalen Code genau an, bevor du die Herausforderungen angehst. Es gibt einen Hinweis, wie du dieses Puzzle lösen kannst. Hast du den neuen Befehl bemerkt?

### ~ tutorialhint
```javascript
let MadePyramid = false
// Teleportiert den Agenten in deine Nähe, aber etwas weiter weg, damit
// du Zeit hast, aus dem Weg zu gehen, wenn er mit dem Bau beginnt
player.onChat("tp", function () {
    player.teleport(pos(3, 0, 3))
    agent.teleportToPlayer()
    player.teleport(pos(-3, 0, -3))
})
player.onChat("turn", function () {
    agent.turn(TurnDirection.Left)
})
player.onChat("pyramid", function (BaseSize) {
    // Überprüfe, ob wir mit dem Bau der Pyramide fortfahren sollen
    if (BaseSize > 0) {
        agent.setAssist(PLACE_ON_MOVE, true)
        // Baut eine Ebene der Pyramide
        for (let i = 0; i <= 3; i++) {
            agent.move(FORWARD, BaseSize - 1)
            agent.turn(TurnDirection.Left)
        }
        agent.move(UP, 1)
        agent.setAssist(PLACE_ON_MOVE, false)
        agent.move(FORWARD, 1)
        MadePyramid = true
        player.runChatCommand("pyramid " + (BaseSize - 2))
    } else {

    }
})
```

## Schritt 12
Versuche, diese Variable und eine ``||Logic:if||``-Anweisung zu verwenden, um die Herausforderungen zu lösen!

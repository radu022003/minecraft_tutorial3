### @explicitHints 1

# Aktivität: Pyramide

## Schritt 1
Kopiere den Startcode. Kopiere den Code aus dem Hinweis.

### ~ tutorialhint
```blocks
player.onChat("tp", function () {
        player.teleport(positions.create(3, 0, 3))
        agent.teleportToPlayer() 
        player.teleport(positions.create(-3, 0, -3)) 
}) 
player.onChat("pyramide", function (BaseSize) {
        agent.setAssist(AgentAssist.PlaceOnMove, true)
        for (let i = 0; i <= 3; i++) {
                agent.move(SixDirection.Forward, BaseSize - 1)
                agent.turn(TurnDirection.Left)
        } 
        agent.move(SixDirection.Up, 1)
        agent.setAssist(AgentAssist.PlaceOnMove, false)
        agent.move(SixDirection.Forward, 1)
        player.runChatCommand("pyramide " + (BaseSize - 2))
})
player.onChat("drehe", function () {
        agent.turn(TurnDirection.Left)
})
```
## Schritt 2
Starten Sie den Code und untersuchen Sie das Problem mit dem Startcode. Wenn Sie diesen Code genau so ausführen, wie er ist, werden Sie etwas Merkwürdiges feststellen.

## Schritt 3
Rüsten Sie Ihren Agenten mit einigen Blöcken aus.

In Ihrem Chatfenster geben Sie **tp** ein, um Ihren Agenten in Ihre Nähe zu teleportieren. Möglicherweise möchten Sie Ihren Agenten auch mit dem Befehl Drehen drehen, aber das ist vielleicht nicht notwendig.

## Schritt 4
Geben Sie **pyramide 5** in das Chatfenster ein und sehen Sie, was passiert. Ihr Agent sollte die Pyramide problemlos bauen, aber er hört nicht auf. Der Agent baut immer weiter und weiter, ohne anzuhalten. Ihr Code befindet sich in einer Endlosschleife! Dies geschieht, weil am Ende des Codes ein Block steht, der den Code immer wieder aufruft.

### ~ tutorialhint
``` blocks
let BaseSize = 0
player.runChatCommand("pyramide " + (BaseSize - 2))
```

## Schritt 5
Fügen Sie **Falls-Anweisungen** hinzu. Ihre Aufgabe besteht darin, einige **Falls-Anweisungen** in diesen Code einzufügen, um das unendliche Verhalten zu stoppen!

### ~ tutorialhint
Wenn Sie in einer Endlosschleife gefangen sind, müssen Sie Ihren Code aus dem Code-Verbindungsfenster heraus stoppen. Klicken Sie auf die Stopp-Schaltfläche in der unteren linken Ecke Ihres Code-Verbindungsfensters.

## Schritt 6
Stoppen Sie die Schleife. Um die Schleife zu stoppen, müssen Sie eine Variable überprüfen und dann Ihrem Code mitteilen, die Schleife zu stoppen. In einer solchen Situation ist die Verwendung einer if-Anweisung großartig. Ziehen Sie eine ``||Logic: wenn dann ansonsten||``-Anweisung in Ihren Code, sodass die **Falls-Anweisung** den gesamten Code innerhalb von ``||Player:Bei Chat-Befehl "pyramide"||`` umgibt.

### ~ tutorialhint
``` blocks
player.onChat("pyramide", function (BaseSize) {
    if (true) {
        agent.setAssist(PLACE_ON_MOVE, true)
        for (let i = 0; i <= 3; i++) {
            agent.move(FORWARD, BaseSize - 1)
            agent.turn(TurnDirection.Left)
        }
        agent.move(UP, 1)
        agent.setAssist(PLACE_ON_MOVE, false)
        agent.move(FORWARD, 1)
        player.runChatCommand("pyramide " + (BaseSize - 2))
    } else {

    }
})
```

## Schritt 7
Nun geben wir die Bedingung ein. Sie möchten, dass die Schleife stoppt, wenn die **Größe** unter **null** fällt. Der Benutzer gibt eine Größe ein, und nach jedem Durchlauf durch diesen Code wird die Größe um **2** reduziert. Auch hier passiert das in diesem Block.

``` javascript
let BaseSize = 0
player.runChatCommand("pyramid " + (BaseSize - 2))
```

## Schritt 8
Greifen Sie eine der Befehle ``||Logic:0 = 0"||`` oder ``||Logic:0 < 0"||`` und platzieren Sie diese innerhalb Ihres ``||Logic: wenn dann ansonsten||``.

### ~ tutorialhint
``` blocks
let MadePyramid = false
player.onChat("pyramide", function (BaseSize) {
    // Detect if we should continue building pyramid
    if (BaseSize > 0) {
        agent.setAssist(PLACE_ON_MOVE, true)
        // Builds one level of the pyramid
        for (let i = 0; i <= 3; i++) {
            agent.move(FORWARD, BaseSize - 1)
            agent.turn(TurnDirection.Left)
        }
        agent.move(UP, 1)
        agent.setAssist(PLACE_ON_MOVE, false)
        agent.move(FORWARD, 1)
        MadePyramid = true
        player.runChatCommand("pyramide " + (BaseSize - 2))
    } else {

    }
})

```

## Schritt 9
Sie möchten Ihren Vergleich auf **'BaseSize > 0'** setzen. Wenn die Größe größer als null ist, möchten Sie etwas bauen. ABER wenn nicht, geben Sie dem Benutzer eine Nachricht.

### ~ tutorialhint
``` blocks
let MadePyramid = false
player.onChat("pyramide", function (BaseSize) {
    // Detect if we should continue building pyramid
    if (BaseSize > 0) {
        agent.setAssist(PLACE_ON_MOVE, true)
        // Builds one level of the pyramid
        for (let i = 0; i <= 3; i++) {
            agent.move(FORWARD, BaseSize - 1)
            agent.turn(TurnDirection.Left)
        }
        agent.move(UP, 1)
        agent.setAssist(PLACE_ON_MOVE, false)
        agent.move(FORWARD, 1)
        MadePyramid = true
        player.runChatCommand("pyramide " + (BaseSize - 2))
    } else {

    }
})
```

## Schritt 10
"Mit dieser If-Anweisung haben Sie das Endloslooping gestoppt! Wie könnten Sie diesen Code noch verbessern? Es gibt zwei Situationen, in denen die Größe null sein kann. Wenn der Agent gerade eine Pyramide fertiggestellt hat oder der Benutzer vergessen hat, eine Größe für seine Pyramide einzugeben. Der Code wird in den ``||Logic: sonst||``-Zweig des ``||Logic: wenn dann||``-Blocks gelangen, wenn das passiert."

## Schritt 11
Können Sie eine Möglichkeit finden, die beiden vorhergehenden Bedingungen (A und B) zu überprüfen? Sie würden dies in diesem else-Zweig überprüfen. Schauen Sie sich unseren endgültigen Code genau an, bevor Sie die Herausforderungen meistern. Es gibt einen Hinweis, wie man dieses Rätsel löst. Haben Sie den neuen Befehl bemerkt?

### ~ tutorialhint
``` blocks
let MadePyramid = false
// Teleports the agent near you but a little away so
// you have time to get out of his way when he starts
// building
player.onChat("tp", function () {
    player.teleport(pos(3, 0, 3))
    agent.teleportToPlayer()
    player.teleport(pos(-3, 0, -3))
})
player.onChat("drehe", function () {
    agent.turn(TurnDirection.Left)
})
player.onChat("pyramide", function (BaseSize) {
    // Detect if we should continue building pyramid
    if (BaseSize > 0) {
        agent.setAssist(PLACE_ON_MOVE, true)
        // Builds one level of the pyramid
        for (let i = 0; i <= 3; i++) {
            agent.move(FORWARD, BaseSize - 1)
            agent.turn(TurnDirection.Left)
        }
        agent.move(UP, 1)
        agent.setAssist(PLACE_ON_MOVE, false)
        agent.move(FORWARD, 1)
        MadePyramid = true
        player.runChatCommand("pyramide " + (BaseSize - 2))
    } else {

    }
})
```

## Schritt 12
Versuchen Sie, diese Variable und eine ``||Logic:wenn||`` Anweisung zu verwenden, um die Herausforderungen abzuschließen!

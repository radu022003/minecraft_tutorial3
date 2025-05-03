### @explicitHints 1

# Aktivität: Labyrinth Generierung

## Schritt 1: Starter-Code verwenden

Nutze den Starter-Code

```template
let dirs: number[] = []
let index2 = 0
let index = 0
let right = 0
let left = 0
let forward = 0
let temp = 0
let moves: string[] = []
let tempArray: number[] = []
player.onChat("laby", function () {
    blocks.fill(
        blocks.block(Block.Stone),
        positions.create(-5, 0, -5),
        positions.create(5, 0, 5),
        FillOperation.Replace
    )
    agent.teleportToPlayer()
    blocks.place(blocks.block(Block.Air), positions.create(0, 0, 0))
    agent.setAssist(AgentAssist.DestroyObstacles, false)
    player.teleport(positions.create(0, 5, 0))
    player.say("Lass uns das Labyrinth graben!")
    dig()
})
function shuffle() {
    tempArray = [forward, left, right]
    for (let i = 0; i < 3; i++) {
        index = Math.randomRange(0, 2)
        index2 = Math.randomRange(0, 2)
        temp = tempArray[index]
        tempArray[index] = tempArray[index2]
        tempArray[index2] = temp
    }
    for (let k = 0; k < 3; k++) {
        dirs.push(tempArray[k])
    }
}
function dig() {
    player.say("Tiefer graben")
    shuffle()
    for (let i = 0; i < 3; i++) {
        player.say("Versuch " + moves[dirs[dirs.length - 1]])
        // zur neuen Richtung drehen
        if (dirs[dirs.length - 1] == left) {
            agent.turn(TurnDirection.Left)
        } else if (dirs[dirs.length - 1] == right) {
            agent.turn(TurnDirection.Right)
        }
        // ist das eine Wand?
        if (agent.detect(AgentDetection.Block, SixDirection.Forward)) {
            // einmal graben
            agent.destroy(SixDirection.Forward)
            agent.move(SixDirection.Forward, 1)
            // haben wir durch die Wand gegraben?
            if (!(agent.detect(AgentDetection.Block, SixDirection.Forward))) {
                player.say("Oops, das war eine Wand")
                // zurück und Wand wieder platzieren
                agent.move(SixDirection.Back, 1)
                agent.place(SixDirection.Forward)
            } else {
                // weiter graben
                agent.destroy(SixDirection.Forward)
                agent.move(SixDirection.Forward, 1)
                // ist das Ende erreicht?
                if (!(agent.detect(AgentDetection.Block, SixDirection.Forward))) {
                    player.say("Oops, zu weit")
                    agent.move(SixDirection.Back, 1)
                    agent.place(SixDirection.Forward)
                    agent.move(SixDirection.Back, 1)
                } else {
                    dig()
                    // zurückrollen
                    agent.move(SixDirection.Back, 2)
                }
            }
        }
        // zurück zur ursprünglichen Richtung drehen
        if (dirs[dirs.length - 1] == left) {
            agent.turn(TurnDirection.Right)
        } else if (dirs[dirs.length - 1] == right) {
            agent.turn(TurnDirection.Left)
        }
        dirs.pop()
    }
}
moves = ["forward", "left", "right"]
temp = 1
forward = 0
left = 1
right = 2
```

## Schritt 2: Materialien zum Reparieren bereitstellen

Manchmal zerstört der Agent versehentlich einen Block der Labyrinthwand, den wir später aber brauchen. Deshalb flickt der Agent das Loch wieder.

**Aufgabe:** Gib dem Agenten einige Eichenholzbretter in seinem Inventar. Lege sie in den oberen linken Slot.

## Schritt 3: Programm ausprobieren

Probiere jetzt dein Programm aus!

**So geht’s:**

1. Tippe im Chat-Fenster den Befehl **laby** ein.
2. Drücke die Leertaste zweimal schnell hintereinander, um hochzufliegen und zuzusehen.

## Schritt 4: Start- und Endpunkte bauen

Baue einen Start- und einen Endpunkt für dein Labyrinth.
Warum? In der nächsten Aktivität soll der Agent erkennen, wann er das Labyrinth erfolgreich durchquert hat.

**Aufgabe:** Bereite die Bereiche für Start und Ende vor.

## Schritt 5: Spieler ausstatten

Versorge den Spieler mit folgenden Gegenständen:

* **Diamantspitzhacke**: Zum Zerstören der Steinblöcke am Start und Ende.
* **Redstone-Block**: Markiert das Ende.

**So geht’s:**

1. Öffne das Terminal mit `/`.
2. Gib ein:

   ```
   /give @s diamond_pickaxe
   /give @s redstone_block
   ```


## Schritt 6: Start- und Endpunkt festlegen

Überlege dir, wo das Labyrinth beginnen und wo es enden soll. Meist liegen Start und Ende an gegenüberliegenden Enden des Felds.

## Schritt 7: Blöcke zerstören und platzieren

1. Zerstöre an der Startposition einen Block, um den Eingang freizulegen.
2. Zerstöre an der Endposition einen Block.
3. Platziere **unter** dem Endpunkt einen Redstone-Block, damit er gut sichtbar ist.

## Schritt 8: Endpunkt im Boden markieren

Nachdem du den Grasblock am Ende entfernt hast, setze einen Redstone-Block in den Erdboden darunter. So erkennt der Agent das Ziel leicht.

## Schritt 9: Nächste Aufgabe – Labyrinth Pathfinding

In der nächsten Aktivität lernst du, wie der Agent anhält, sobald er **Redstone** unter sich erkennt.
**Das bedeutet:** Wenn der Agent Redstone unter seinen Füßen findet, weißt du, dass er das Labyrinth geschafft hat!


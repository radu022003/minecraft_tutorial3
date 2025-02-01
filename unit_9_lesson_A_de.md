### @explicitHints 1
# Aktivität: Labyrinth Generation

## Schritt 1: Starter-Code verwenden
Nutze den folgenden Starter-Code:

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
    for (let k = 0; k <= 3 - 1; k++) {
        dirs.push(tempArray[k])
    }
}
function dig() {
    player.say("Tiefer graben")
    shuffle()
    for (let i = 0; i < 3; i++) {
        player.say("versuch " + moves[dirs[dirs.length - 1]])
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
                player.say("oops, das war eine Wand")
                // geh zurück und platziere die Wand wieder
                agent.move(SixDirection.Back, 1)
                agent.place(SixDirection.Forward)
            } else {
                // yay! weiter graben
                agent.destroy(SixDirection.Forward)
                agent.move(SixDirection.Forward, 1)
                // haben wir das Ende des Labyrinths erreicht?
                if (!(agent.detect(AgentDetection.Block, SixDirection.Forward))) {
                    // gehe zurück und platziere eine Wand
                    player.say("oops, zu weit")
                    agent.move(SixDirection.Back, 1)
                    agent.place(SixDirection.Forward)
                    agent.move(SixDirection.Back, 1)
                } else {
                    dig()
                    // starte rollback
                    agent.move(SixDirection.Back, 2)
                }
            }
        }
        // zurück zur eigentlichen Richtung
        if (dirs[dirs.length - 1] == left) {
            agent.turn(TurnDirection.Right)
        } else if (dirs[dirs.length - 1] == right) {
            agent.turn(TurnDirection.Left)
        }
        temp = dirs.pop()
    }
}
moves = ["forward", "left", "right"]
temp = 1
forward = 0
left = 1
right = 2
```

## Schritt 2: Materialien zum Reparieren bereitstellen
Manchmal zerstört der Agent aus Versehen einen Block der Labyrinthwand – aber später merken wir, dass wir diesen Block doch brauchen. Deshalb flickt der Agent den Fehler aus und repariert das Loch.

**Aufgabe:** Gib dem Agenten etwas Holz (Eichenholzbretter) in seinem Inventar. Lege die Bretter in den oberen linken Slot.



## Schritt 3: Programm ausprobieren
Probier jetzt dein Programm aus!

**So geht’s:**

1. Tippe im Chat-Fenster den Befehl **laby** ein.
2. Drücke die Leertaste zweimal schnell hintereinander, um hochzufliegen und das Geschehen zu beobachten.

## Schritt 4: Starte- und Endpunkte bauen
Baue einen Start- und einen Endpunkt für dein Labyrinth.
Warum das wichtig ist: In der nächsten Aufgabe soll der Agent wissen, wann er das Labyrinth erfolgreich durchquert hat.
In Aktivität 2 wirst du Code schreiben, der dem Agenten hilft, das Labyrinth zu meistern.

**Aufgabe:** Bereite daher den Bereich für den Start- und Endpunkt vor.


## Schritt 5: Spieler ausstatten
Du musst den Spieler mit Werkzeugen versorgen:

- Diamantspitzhacke: Damit kannst du den Stein an den Start- und Endpunkten zerstören.
- Redstone-Block: Dieser Block markiert den Endpunkt des Labyrinths.

**So geht’s:**

Öffne das Terminal, indem du / eingibst.
Tippe die folgenden Befehle ein:

**/give @s diamond_pickaxe**

**/give @s redstone_block**

## Schritt 6
Jetzt musst du nur noch den Start- und Endpunkt bauen.
Überlege:

- Wo soll das Labyrinth beginnen?
- Wo soll es enden?

Meistens liegen diese Punkte an den gegenüberliegenden Enden des Labyrinths.



## Schritt 7: Blöcke zerstören und platzieren
Was du machen sollst:

1. Zerstöre einen Block an der Startposition, um den Start freizumachen.
2. Zerstöre einen Block an der Endposition.

Anschließend:
- **Platziere einen Redstone-Block unter dem Endpunkt**, damit du ihn klar erkennen kannst.

## Schritt 8: Endpunkt im Boden markieren
Nachdem du den Grasblock am Endpunkt zerstört hast, setze einen Redstone-Block in den darunterliegenden Erdboden.
So wird der Endpunkt deutlich markiert.

## Schritt 9: Nächste Aufgabe – Labyrinth Pathfinding
In der nächsten Aktivität „Labyrinth Pathfinding“ lernst du, wie der Agent anhält, sobald er unter sich Redstone entdeckt.

**Das bedeutet:** Wenn der Agent Redstone unter seinen Füßen findet, weißt du, dass er das Labyrinth erfolgreich durchquert hat!

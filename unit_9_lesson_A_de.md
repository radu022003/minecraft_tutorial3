### @explicitHints 1
# Aktivität: Maze Generation

## Schritt 1
Verwenden Sie den präsentierten Einstiegscode. 

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
player.onChat("maze", function () {
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
    player.say("let's dig that maze!")
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
    player.say("dig deeper")
    shuffle()
    for (let i = 0; i < 3; i++) {
        player.say("try " + moves[dirs[dirs.length - 1]])
        // turn towards the new direction
        if (dirs[dirs.length - 1] == left) {
            agent.turn(TurnDirection.Left)
        } else if (dirs[dirs.length - 1] == right) {
            agent.turn(TurnDirection.Right)
        }
        // is this a wall?
        if (agent.detect(AgentDetection.Block, SixDirection.Forward)) {
            // dig once
            agent.destroy(SixDirection.Forward)
            agent.move(SixDirection.Forward, 1)
            // did we dig through a wall?
            if (!(agent.detect(AgentDetection.Block, SixDirection.Forward))) {
                player.say("oops, that was a wall")
                // move back and put the wall back
                agent.move(SixDirection.Back, 1)
                agent.place(SixDirection.Forward)
            } else {
                // yay! keep digging
                agent.destroy(SixDirection.Forward)
                agent.move(SixDirection.Forward, 1)
                // did we reach the end of the maze?
                if (!(agent.detect(AgentDetection.Block, SixDirection.Forward))) {
                    // go back and place wall
                    player.say("oops, too far")
                    agent.move(SixDirection.Back, 1)
                    agent.place(SixDirection.Forward)
                    agent.move(SixDirection.Back, 1)
                } else {
                    dig()
                    // start roll back
                    agent.move(SixDirection.Back, 2)
                }
            }
        }
        // turn back to the original direction
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

## Schritt 2
Der Agent wird Materialien benötigen, um Löcher zu stopfen, die er im Labyrinth verursacht. Da der Agent beim Erkunden "lernt", kann es passieren, dass er versehentlich einen Block der Labyrinthwand bricht, nur um später festzustellen, dass wir diesen Block benötigen. Daher stopft der Agent dann das Loch, das er versehentlich gemacht hat. Sie können dem Agenten einige Eichenholzdielen geben, um die Löcher zu stopfen. Geben Sie dem Agenten einige Eichenholzdielen in seinem Inventar, im oberen linken Inventarplatz.

## Schritt 3
Lassen Sie uns das Programm ausprobieren! Geben Sie den Befehl "Labyrinth" im Chatfenster ein, um das Programm auszuführen. Tippen Sie zweimal auf die Leertaste und fliegen Sie nach oben, um einen Überblick zu bekommen.

## Schritt 4
Bauen Sie die Start- und Endpositionen. Für die nächste Aktivität muss der Agent wissen, wann er das Labyrinth erfolgreich durchquert hat. In Aktivität 2 werden Sie einige Codes erstellen, um den Agenten erfolgreich durch das Labyrinth zu navigieren. Um sich für die nächste Aktivität vorzubereiten, müssen Sie die Start- und Endbereiche des Labyrinths vorbereiten.

## Schritt 5
Sie müssen den Spieler mit einer Diamantspitzhacke und einem Redstone-Block ausstatten. Die Spitzhacke dient dazu, den Stein für den Startpunkt und den Endpunkt zu zerstören. Das Redstone wird den Endpunkt markieren. Öffnen Sie das Terminal mit '/', geben Sie dann den Befehl "give" ein, um den Spieler mit einer Diamantspitzhacke und einem Redstone-Block auszustatten.
**/give @s diamond_pickaxe**
**/give @s redstone_block**

## Schritt 6
Jetzt müssen Sie nur noch einen Start- und einen Endpunkt bauen. Entscheiden Sie einen Startpunkt und einen Endpunkt. Wahrscheinlich werden diese sich an entgegengesetzten Enden des Labyrinths befinden.

## Schritt 7
Zerstören Sie einen Block am Startpunkt.

Zerstören Sie einen Block am Endpunkt. Platzieren Sie einen Redstone-Block unter dem Endpunkt.

## Schritt 8
Nachdem Sie den Grasblock, der den Endstandort markiert, zerstört haben, platzieren Sie einen Redstone-Block im Erdreich.

## Schritt 9
In der nächsten Aktivität, Maze Pathfinding, wird der Agent anhalten, wenn er Redstone unter seinen Füßen entdeckt. So werden Sie wissen, dass er das Labyrinth abgeschlossen hat!

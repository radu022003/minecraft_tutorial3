### @explicitHints 1

# Aktivität: Tanz, Tanz Agent 

## Schritt 1
Erstellen Sie den "tanz" Befehl. Ziehen Sie einen neuen ``||Player:Bei Chat-Befehl||`` Block in die Codierungs-Arbeitsfläche. Benennen Sie diesen Befehl **"tanz"**.

## Schritt 2
Erstellen Sie eine Sequenz von Bewegungen, die Ihr Agent ausführen soll. Hier ist ein Beispiel:

```template 
player.onChat("tanz", function () {
    agent.move(LEFT, 1)
    agent.attack(FORWARD)
    agent.move(RIGHT, 1)
    agent.move(RIGHT, 1)
    agent.move(RIGHT, 1)
    agent.turn(TurnDirection.Left)
    agent.move(LEFT, 1)
})
```

## Schritt 3
Tanzen Sie immer wieder. Ziehen Sie einen ``||Loops:-mal wiederholen||`` Block in den ``||Player:Bei Chat-Befehl "tanz"||`` Block und umgeben Sie die Agentenblöcke.

## Schritt 4
Verwenden Sie den ``||Loops:-mal wiederholen||`` Block, um Ihre Sequenz von Tanzbewegungen so oft wie gewünscht zu wiederholen.

### ~ tutorialhint
``` blocks
player.onChat("tanz", function () {
    for (let i = 0; i < 4; i++) {
        agent.move(LEFT, 1)
        agent.attack(FORWARD)
        agent.move(RIGHT, 1)
        agent.move(RIGHT, 1)
        agent.move(RIGHT, 1)
        agent.turn(TurnDirection.Left)
        agent.move(LEFT, 1)
    }
})
```

## Schritt 5
Wo ist dein Agent? Zuletzt müssen Sie Ihren Agenten zu Ihrem Charakter bringen, damit Sie Ihren Roboter tanzen sehen können. Denken Sie daran, dass Sie Ihren Agenten teleportieren können. Lassen Sie uns einen separaten ``||Player:Bei Chat-Befehl||`` erstellen, um Ihren Agenten zu bekommen.

## Schritt 6
Ziehen Sie einen neuen ``||Player:Bei Chat-Befehl||`` Block in die Codierungs-Arbeitsfläche und benennen Sie ihn "tp".

## Schritt 7
Platzieren Sie ``||Agent:Agent, teleportiere zu Spieler||`` innerhalb von ``||Player:Bei Chat-Befehl "tp"||``.

## Schritt 8
Gehen Sie zu Minecraft. Zuerst teleportieren Sie den Agenten an Ihren Standort, indem Sie **tp** in das Chatfenster eingeben. Dann lassen Sie ihn tanzen, indem Sie **tanz** in das Chatfenster eingeben!

## Schritt 9
Langsamer Modus. Da der Agent die Tanzschritte so schnell durchläuft, kann es schwierig sein, seine Tanzroutine zu erkennen. MakeCode verfügt über eine Slo-Mo-Funktion, mit der Sie ein Programm verlangsamen können, sodass Sie jeden Schritt einzeln durchgehen können, während er ausgeführt wird. Dies ist sehr hilfreich, wenn Sie Code beheben oder einem Roboter beim Tanzen zusehen möchten! Die **Slo-Mo**-Schaltfläche befindet sich unten links im MakeCode-Bildschirm und hat ein Schneckensymbol darauf. Wenn Sie darauf klicken, um es einzuschalten, wird die Schaltfläche gelb. Wenn Sie jetzt ein MakeCode-Programm ausführen, läuft alles langsam ab. Sie sollten in der Lage sein, jeden Befehl im Codierungs-Workspace zu sehen, während der Roboter ihn in Minecraft ausführt. Außerdem kann das Ändern Ihrer Ansicht mit **F5** das Tanzen besser sichtbar machen.

### ~ tutorialhint
``` blocks
player.onChat("tanz", function () {
    for (let i = 0; i < 4; i++) {
        agent.move(LEFT, 1)
        agent.attack(FORWARD)
        agent.move(RIGHT, 1)
        agent.move(RIGHT, 1)
        agent.move(RIGHT, 1)
        agent.turn(TurnDirection.Left)
        agent.move(LEFT, 1)
    }
})
player.onChat("tp", function () {
    agent.teleportToPlayer()
})

```

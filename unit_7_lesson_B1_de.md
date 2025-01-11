### @explicitHints 1

# Aktivität: Tanz, Tanz Agent 

## Schritt 1
Erstelle den "tanz" Befehl. Ziehe einen neuen ``||Player:Bei Chat-Befehl||`` Block in die Codierungs-Arbeitsfläche. Benenne diesen Befehl **"tanz"**.

## Schritt 2
Erstelle eine Sequenz von Bewegungen, die der Agent ausführen soll. Hier ist ein Beispiel:

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
Lass den Agent immer wieder tanzen! Ziehe einen ``||Loops:...-mal wiederholen||`` Block in den ``||Player:Bei Chat-Befehl "tanz"||`` Block.

## Schritt 4
Verwende den ``||Loops:...-mal wiederholen||`` Block, um die Sequenz von Tanzbewegungen so oft wie gewünscht zu wiederholen.

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
Wo ist dein Agent? Zuletzt müsst du deinen Agenten zu Ihrem Charakter bringen, damit du Ihn tanzen sehen kannst. Denk daran, dass du deinen Agenten teleportieren kannst. Lass uns einen separaten ``||Player:Bei Chat-Befehl||`` erstellen, um Ihren Agenten zu dir zu bekommen.

## Schritt 6
Ziehe einen neuen ``||Player:Bei Chat-Befehl||`` Block in die Codierungs-Arbeitsfläche und benennen ihn "tp".

## Schritt 7
Platzieren das ``||Agent:Agent, teleportiere zu Spieler||`` innerhalb von ``||Player:Bei Chat-Befehl "tp"||``.

## Schritt 8
Gehe zu Minecraft. Zuerst teleportierst du den Agenten an Ihren Standort, indem du **tp** in das Chatfenster eingibst. Dann lasst du ihn tanzen, indem du **tanz** in das Chatfenster eingibst!

## Schritt 9
Langsamer Modus. Da der Agent die Tanzschritte so schnell durchläuft, kann es schwierig sein, seine Tanzroutine zu erkennen. MakeCode verfügt über eine Slo-Mo-Funktion, mit der Sie ein Programm verlangsamen können, sodass Sie jeden Schritt einzeln durchgehen können, während er ausgeführt wird. Dies ist sehr hilfreich, wenn du Codefehler finden oder einem Roboter beim Tanzen zusehen möchten! Die **Slo-Mo**-Schaltfläche befindet sich unten links im MakeCode-Bildschirm und hat ein Schneckensymbol darauf. Wenn du darauf klickst, um es einzuschalten, wird die Schaltfläche gelb. Wenn du jetzt ein MakeCode-Programm ausführst, läuft alles langsam ab. Du solltest in der Lage sein, jeden Befehl im Codierungs-Workspace zu sehen, während der Roboter ihn in Minecraft ausführt. Außerdem kann das Ändern der Ansicht mit **F5** das Tanzen besser sichtbar machen.

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

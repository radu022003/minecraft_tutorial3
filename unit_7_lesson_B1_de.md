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

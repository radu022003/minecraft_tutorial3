### @explicitHints 1

# Aktivität: Tanz, Tanz Agent 

## 1. Chat-Befehl anlegen
Erstelle den "tanz" Befehl. Ziehe einen neuen ``||PLAYER:Bei Chat-Befehl||`` Block in die Codierungs-Arbeitsfläche. Benenne diesen Befehl **"tanz"**.

## 2. Chat-Befehl erstellen
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

## 3. Chat-Befehl erstellen
Lass den Agent immer wieder tanzen! Ziehe einen ``||LOOPS:...-mal wiederholen||`` Block in den ``||PLAYER:Bei Chat-Befehl "tanz"||`` Block.

## 4. Chat-Befehl erstellen
Verwende den ``||LOOPS:...-mal wiederholen||`` Block, um die Sequenz von Tanzbewegungen so oft wie gewünscht zu wiederholen.

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

## 5. Teleport einrichten
Wo ist dein Agent? Zuletzt musst du deinen Agenten zu deinem Charakter bringen, damit du ihn tanzen sehen kannst. Denk daran, dass du deinen Agenten teleportieren kannst. Lass uns einen separaten ``||PLAYER:Bei Chat-Befehl||`` erstellen, um deinen Agenten zu dir zu bekommen.

## 6. Chat-Befehl anlegen
Ziehe einen neuen ``||PLAYER:Bei Chat-Befehl||``-Block in die Codierungs-Arbeitsfläche und benenne ihn "tp".

## 7. Teleport einrichten
Platziere das ``||AGENT:Agent, teleportiere zu Spieler||`` innerhalb von ``||PLAYER:Bei Chat-Befehl "tp"||``.

## 8. Teleport einrichten
Gehe zu Minecraft. Teleportiere zuerst den Agenten an deinen Standort, indem du **tp** in das Chatfenster eingibst. Dann lass ihn tanzen, indem du **tanz** in das Chatfenster eingibst!

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

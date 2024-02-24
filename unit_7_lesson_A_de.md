### @explicitHints 1
# Agent Einführung

## Schritt 1
Ändern Sie den Namen des Standardblocks ``||Player:Bei Chat-Befehl||`` in "tp".

### ~ tutorialhint
```blocks
player.onChat("tp", function () {})
```

## Schritt 2
Teleportiere den Agenten. Ziehen Sie einen ``||Agent:Agent, teleportiere zu Spieler||`` Block und platzieren Sie ihn innerhalb des "Bei Chat-Befehl" Blocks.

### ~ tutorialhint
```blocks
player.onChat("tp", function () {
    agent.teleportToPlayer()
})
```

## Schritt 3
Bewegen und drehen Sie Ihren Agenten. Jetzt, in Minecraft, wenn Sie **tp** in das Chatfenster eingeben, wird der Agent direkt an Ihren Standort teleportiert. Sie sollten dies immer dann tun, wenn Sie den Agenten in einem Projekt verwenden möchten. Sie könnten auch einige zusätzliche grundlegende Befehle erstellen, um den Agenten zu bewegen.

### ~ tutorialhint
```blocks 
player.onChat("fd", function () {
    agent.move(FORWARD, 1)
})
player.onChat("lt", function () {
    agent.turn(TurnDirection.Left)
})
player.onChat("bk", function () {
    agent.move(BACK, 1)
})
player.onChat("rt", function () {
    agent.turn(TurnDirection.Right)
})
```

## Schritt 4
Das macht es einfacher, den Agenten präzise zu steuern. Alternativ könnten Sie einfach dort stehen bleiben, wo Sie möchten, dass der Agent ist, und dann **tp** im Chatfenster eingeben.

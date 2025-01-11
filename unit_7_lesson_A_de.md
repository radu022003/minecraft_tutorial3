### @explicitHints 1
# Agent Einführung

## Schritt 1
Ändern den Namen des Standardblocks ``||Player:Bei Chat-Befehl||`` in "tp".

### ~ tutorialhint
```blocks
player.onChat("tp", function () {})
```

## Schritt 2
Teleportiere den Agenten. Ziehe einen ``||Agent:Agent, teleportiere zu Spieler||`` Block und platziere ihn innerhalb des "Bei Chat-Befehl" Blocks.

### ~ tutorialhint
```blocks
player.onChat("tp", function () {
    agent.teleportToPlayer()
})
```

## Schritt 3
Bewege und drehe den Agenten. Jetzt, in Minecraft, wenn du **tp** in das Chatfenster eingeben, wird der Agent direkt an deinen Standort teleportiert. Du solltest dies immer dann tun, wenn du den Agenten in einem Projekt verwenden möchten. Du könntest auch einige zusätzliche grundlegende Befehle erstellen, um den Agenten zu bewegen.

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
Das macht es einfacher, den Agenten präzise zu steuern. Alternativ kannst du einfach dort stehen bleiben, wo du möchtest, dass der Agent ist, und dann **tp** im Chatfenster eingeben.

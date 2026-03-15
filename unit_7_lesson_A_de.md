### @explicitHints 1
# Agent Einführung

## 1. Teleport-Chat-Befehl erstellen
Ändern den Namen des Standardblocks ``||PLAYER:Bei Chat-Befehl||`` in "tp".

### ~ tutorialhint
```blocks
player.onChat("tp", function () {})
```

## 2. Teleport einrichten
Teleportiere den Agenten. Ziehe einen ``||AGENT:Agent, teleportiere zu Spieler||`` Block und platziere ihn innerhalb des "Bei Chat-Befehl" Blocks.

### ~ tutorialhint
```blocks
player.onChat("tp", function () {
    agent.teleportToPlayer()
})
```

## 3. Bewegungs- und Drehbefehle hinzufügen
Bewege und drehe den Agenten. Wenn du jetzt in Minecraft **tp** in das Chatfenster eingibst, wird der Agent direkt an deinen Standort teleportiert. Du solltest dies immer dann tun, wenn du den Agenten in einem Projekt verwenden möchtest. Du kannst auch einige zusätzliche grundlegende Befehle erstellen, um den Agenten zu bewegen.

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

## 4. Agent-Aktion einbauen
Mit diesen Befehlen kannst du den Agenten präzise steuern. Alternativ kannst du einfach dort stehen bleiben, wo du möchtest, dass der Agent ist, und dann **tp** im Chatfenster eingeben.

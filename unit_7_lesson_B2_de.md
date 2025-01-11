### @explicitHints 1

# Aktivität: Hilf dein Agent beim Farmen

## Schritt 1
Standardmäßig starten neue Projekte mit einem ``||Player:Bei Chat-Befehl||``, aber diesmal wirst du zwei benötigen. Duplizieren diesen ``||Player:Bei Chat-Befehl||``, indem du mit der rechten Maustaste darauf klickst und "Duplizieren" auswählen.

## Schritt 2
Benennen einen **"tp"**, um den Agent an deinen Standort zu teleportieren, und benennen den anderen **"farm"**.

## Schritt 3
Platzieren ``||Agent:Agent, teleportiere zu Spieler||`` innerhalb von ``||Player:Bei Chat-Befehl "tp"||``.


### ~ tutorialhint
``` blocks
player.onChat("tp", function () {
    agent.teleportToPlayer()
})
player.onChat("farm", function () {
})
```

## Schritt 4
Ziehen  einen ``||Loops:-mal wiederholen||`` Block in ``||Player:Bei Chat-Befehl "farm"||``.
Dies bestimmt die Länge unserer Reihe, also ändere in ``||Loops:-mal wiederholen||`` **4** auf **6**.

## Schritt 5
Platziere einen ``||Agent:Agent, grabe um||`` und einen ``||Agent:Agent, bewege dich||`` Block in ``||Loops:-mal wiederholen||``.


### ~ tutorialhint
``` blocks
player.onChat("farm", function () {
    for (let i = 0; i < 6; i++) {
        agent.till(FORWARD)
        agent.move(FORWARD, 1)
    }
})
```

## Schritt 7
Komm zurück und bearbeite eine weitere Reihe. Bisher wird der Agent mit dem aktuellen Code den Boden direkt vor ihm bearbeiten (mit seiner eigenen Diamantschaufel) und sich dann in diesen Raum bewegen. Er macht dies sechsmal aufgrund der ``||Loops:-mal wiederholen||`` Schleife. Versuche den Code in Minecraft auszuführen, um zu sehen, was passiert.

## Schritt 8
Beachte, wo der Agent nach Abschluss des ``||Loops:-mal wiederholen||`` Blocks landet. Das ist großartig, aber du brauchst zwei Reihen! Du musst den Agent dazu bringen, sich umzudrehen und die nächste Reihe zu bearbeiten.

## Schritt 9
Wenn du einen weiteren ``||Loops:-mal wiederholen||`` Block hinzufügst, kannst du dies erreichen. Du musst auch einige Anweisungen hinzufügen, um den Agent umzudrehen, bevor er mit der nächsten Reihe beginnt. Hier ist ein Versuch:


### ~ tutorialhint
``` blocks
player.onChat("tp", function () {
    agent.teleportToPlayer()
})
player.onChat("farm", function () {
    for (let i = 0; i < 2; i++) {
        for (let j = 0; j < 6; j++) {
            agent.till(FORWARD)
            agent.move(FORWARD, 1)
        }
        agent.turn(TurnDirection.Left)
        agent.move(FORWARD, 1)
        agent.turn(TurnDirection.Left)
    }
})
```

## Schritt 10
Wenn Sie diesen Code ausführst, wirst du feststellen, dass ein Problem besteht. Der Agent ist nicht richtig eingestellt, und die zweite Reihe ist nicht ausgerichtet. Wie kannst du den Code reparieren, um ihn richtig zu machen?
Kurz: Du möchtest etwas, bei dem die Reihen perfekt ausgerichtet sind. Die Richtung, in die der Roboter am Ende schaut, ist nicht wichtig.

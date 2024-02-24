### @explicitHints 1

# Aktivität: Hilf dein Agent beim Farmen

## Schritt 1
Standardmäßig starten neue Projekte mit einem ``||Player:Bei Chat-Befehl||``, aber Sie werden zwei benötigen. Duplizieren Sie diesen ``||Player:Bei Chat-Befehl||``, indem Sie mit der rechten Maustaste darauf klicken und "Duplizieren" auswählen.

## Schritt 2
Benennen Sie einen **"tp"**, um den Agent an Ihren Standort zu teleportieren, und benennen Sie den anderen **"farm"**.

## Schritt 3
Platzieren Sie ``||Agent:Agent, teleportiere zu Spieler||`` innerhalb von ``||Player:Bei Chat-Befehl "tp"||``.


### ~ tutorialhint
``` blocks
player.onChat("tp", function () {
    agent.teleportToPlayer()
})
player.onChat("farm", function () {
})
```

## Schritt 4
Bearbeiten Sie einige Böden. Ziehen Sie einen ``||Loops:-mal wiederholen||`` Block in ``||Player:Bei Chat-Befehl "farm"||``.

## Schritt 5
Dies bestimmt die Länge unserer Reihe, also ändern Sie in ``||Loops:-mal wiederholen||`` **4** auf **6**.

## Schritt 6
Platzieren Sie einen ``||Agent:Agent, grabe um||`` und einen ``||Agent:Agent, bewege dich||`` Block in ``||Loops:-mal wiederholen||``.


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
Kommen Sie zurück und bearbeiten Sie eine weitere Reihe. Bisher wird der Agent mit dem aktuellen Code den Boden direkt vor ihm bearbeiten (mit seiner eigenen Diamantschaufel) und sich dann in diesen Raum bewegen. Er macht dies sechsmal aufgrund der ``||Loops:-mal wiederholen||`` Schleife. Versuchen Sie, den Code in Minecraft auszuführen, um zu sehen, was passiert.

## Schritt 8
Beachten Sie, wo der Agent nach Abschluss des ``||Loops:-mal wiederholen||`` Blocks landet. Das ist großartig, aber Sie brauchen zwei Reihen! Sie müssen den Agent dazu bringen, sich umzudrehen und die nächste Reihe zu bearbeiten, damit er wie auf dem folgenden Bild endet.

## Schritt 9
Wenn Sie einen weiteren ``||Loops:-mal wiederholen||`` Block hinzufügen, können Sie dies erreichen. Sie müssen auch einige Anweisungen hinzufügen, um den Agent umzudrehen, bevor er mit der nächsten Reihe beginnt. Hier ist unser Versuch:


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
Wenn Sie diesen Code ausführen, werden Sie feststellen, dass ein Problem besteht. Der Agent ist nicht richtig eingestellt, und die zweite Reihe ist nicht ausgerichtet. Wie können Sie den Code reparieren, um ihn richtig zu machen? Noch einmal, Sie möchten etwas, bei dem die Reihen perfekt ausgerichtet sind. Die Richtung, in die der Roboter am Ende schaut, ist nicht wichtig.

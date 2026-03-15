### @explicitHints 1

# Aktivität: Hilf dein Agent beim Farmen

## 1. Block duplizieren
Standardmäßig starten neue Projekte mit einem ``||PLAYER:Bei Chat-Befehl||``, aber diesmal wirst du zwei benötigen. Dupliziere diesen ``||PLAYER:Bei Chat-Befehl||``, indem du mit der rechten Maustaste darauf klickst und "Duplizieren" auswählst.

## 2. Teleport einrichten
Benenne einen **"tp"**, um den Agenten an deinen Standort zu teleportieren, und benenne den anderen **"farm"**.

## 3. Teleport einrichten
Platziere ``||AGENT:Agent, teleportiere zu Spieler||`` innerhalb von ``||PLAYER:Bei Chat-Befehl "tp"||``.


### ~ tutorialhint
``` blocks
player.onChat("tp", function () {
    agent.teleportToPlayer()
})
player.onChat("farm", function () {
})
```

## 4. Chat-Befehl erstellen
Ziehe einen ``||LOOPS:-mal wiederholen||``-Block in ``||PLAYER:Bei Chat-Befehl "farm"||``.
Dies bestimmt die Länge unserer Reihe, also ändere in ``||LOOPS:-mal wiederholen||`` **4** auf **6**.

## 5. Chat-Befehl erstellen
Platziere einen ``||AGENT:Agent, grabe um||`` und einen ``||AGENT:Agent, bewege dich||``-Block in ``||LOOPS:-mal wiederholen||``.


### ~ tutorialhint
``` blocks
player.onChat("farm", function () {
    for (let i = 0; i < 6; i++) {
        agent.till(FORWARD)
        agent.move(FORWARD, 1)
    }
})
```

## 7. Bedingung konfigurieren
Komm zurück und bearbeite eine weitere Reihe. Bisher wird der Agent mit dem aktuellen Code den Boden direkt vor ihm bearbeiten (mit seiner eigenen Diamantschaufel) und sich dann in diesen Raum bewegen. Er macht dies sechsmal aufgrund der ``||LOOPS:-mal wiederholen||`` Schleife. Versuche den Code in Minecraft auszuführen, um zu sehen, was passiert.

## 8. Schleife konfigurieren
Beachte, wo der Agent nach Abschluss des ``||LOOPS:-mal wiederholen||`` Blocks landet. Das ist großartig, aber du brauchst zwei Reihen! Du musst den Agent dazu bringen, sich umzudrehen und die nächste Reihe zu bearbeiten.

## 9. Chat-Befehl erstellen
Wenn du einen weiteren ``||LOOPS:-mal wiederholen||`` Block hinzufügst, kannst du dies erreichen. Du musst auch einige Anweisungen hinzufügen, um den Agent umzudrehen, bevor er mit der nächsten Reihe beginnt. Hier ist ein Versuch:


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

## 10. Bedingung konfigurieren
Wenn du diesen Code ausführst, wirst du feststellen, dass ein Problem besteht. Der Agent ist nicht richtig eingestellt, und die zweite Reihe ist nicht ausgerichtet. Wie kannst du den Code reparieren, um ihn richtig zu machen?
Kurz: Du möchtest, dass die Reihen perfekt ausgerichtet sind. Die Richtung, in die der Agent am Ende schaut, ist nicht wichtig.

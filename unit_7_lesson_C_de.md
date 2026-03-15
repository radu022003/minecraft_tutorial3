### @explicitHints 1

# Aktivität: Einen Block nach dem anderen

## 1. Agent-Grundbefehle verwenden
Verwenden die Aktivität "Einführung in den Agenten" als Ausgangscode. Dadurch kannst du deinen Agenten leicht positionieren, und dann kannst du einige Teile davon anpassen, um etwas Neues zu tun.

```template
player.onChat("tp", function () {
    agent.teleportToPlayer()
})
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

## 2. Gold-Befehl vorbereiten
Mach dich bereit, den Agenten auszurüsten. Um den Agenten dazu zu bringen, Dinge zu platzieren, müsst du ihn zuerst mit dem Block oder Gegenstand ausrüsten, den du platzieren möchtest. Ein Chat-Befehl könnte dies etwas einfacher machen, aber letztendlich gibt es aktuell noch keine vollautomatische Möglichkeit, dies zu tun. Ziehe dazu aus ``||PLAYER:SPIELER||`` einen ``||PLAYER:Bei Chat-Befehl||`` in die Arbeitsfläche.

## 3. Givegold-Chat-Befehl erstellen
Benenne den Befehl in **givegold** um.

Gehe zur Suche und finde **give**.

## 4. 64 Goldbrücke austeilen
Gebe dir selbst Blöcke und rüste dann deinen Agenten manuell aus. Ändere den 'Give'-Befehl, sodass du deinem Charakter Goldblöcke gibst. Das Maximum, das du in einem Inventarplatz halten kannst beträgt 64, also gebe deinem Charakter **64** Blöcke **Gold**.

### ~ tutorialhint
``` blocks
player.onChat("givegold", function () {
    mobs.give(
    mobs.target(LOCAL_PLAYER),
    GOLD_BLOCK,
    64
    )
})
```

## 5. Teleport einrichten
Rüste den Agenten aus. Jetzt, da du Goldblöcke hast, musst du deinen Agenten ausstatten. Verwende den ``||PLAYER:Bei Chat-Befehl 'tp'||``, um deinen Agenten in deine Nähe zu teleportieren, oder gehe zu deinem Agenten hinüber.

## 6. Bedingung konfigurieren
Klicke mit der rechten Maustaste auf deinen Agenten, um das Inventar des Agenten und das Inventar deines Charakters anzuzeigen. Übertrage die Goldblöcke zum Agenten. **Wichtig:** Jeder Gegenstand, den der Agent verwenden soll, muss in die **obere linke Ecke** seines Inventars gelegt werden! Nur dort greift der Agent darauf zu.

## 7. Schritt gezielt umsetzen

## 8. Quadrat-Chat-Befehl erstellen
Lass uns den Boden zerstören und diese Blöcke durch Goldblöcke ersetzen. Dupliziere zuerst ``||PLAYER:Bei Chat-Befehl "fd"||`` und benenne es in **quadrat** um. Du kannst dies durch Rechtsklick und Auswahl von "Duplizieren" tun.

## 9. Quadrat-Anforderungen planen
Um dein Quadrat zu erstellen, müsst du darüber nachdenken, was erforderlich ist, um es zu erstellen. Beginne mit dem großen Ziel und arbeite dich zu den kleinen Teilen vor, die erforderlich sind, um dies zu erreichen. Wenn du mit dem Codieren beginnen, arbeite zuerst am kleinsten Teil und füge mehr hinzu, während du fortfahrst. 

## 10. Block zerstören und platzieren
Beginne damit, nur einen Goldblock zu platzieren, um das Ziel zu erreichen. Welchen Code benötigst du dafür? Setze ``||AGENT:Agent, zerstöre nach unten||`` aus ``||AGENT:AGENT||`` in ``||PLAYER:Bei Chat-Befehl "quadrat"||``.

## 11. Chat-Befehl erstellen
Setze ``||AGENT:Agent, platziere nach unten||`` innerhalb von ``||PLAYER:Bei Chat-Befehl "quadrat"||``. Der Agent wird das platzieren, was sich in der oberen linken Ecke seines Inventars befindet, wie wir zuvor besprochen haben. In diesem Fall werden die Goldblöcke platziert. Nun sollte ``||PLAYER:Bei Chat-Befehl "quadrat"||`` wie folgt aussehen:

### ~ tutorialhint
``` blocks 
player.onChat("quadrat", function () {
    agent.destroy(DOWN)
    agent.place(DOWN)
})

```

## 12. Wiederholungsschleife für Reihe
Erfolg! Jetzt versuchen wir, einen Schritt weiter zu gehen. Mit einer Schleife versuchen wir, eine Seite des Quadrats zu erstellen! Du benötigst, dass dein Agent sich bewegt und mehrmals bricht und platziert. Das ist ein perfektes Problem für eine Schleife. Nimm dazu aus ``||LOOPS:SCHLEIFEN||`` eine ``||LOOPS:-mal wiederholen||``-Schleife und umschließe den vorhandenen Code in ``||PLAYER:Bei Chat-Befehl "quadrat"||``.

## 13. Bedingung konfigurieren
Passe die ``||LOOPS:-mal wiederholen||``-Schleife an, damit sie sechs Mal wiederholt wird.

## 14. Chat-Befehl erstellen
Füge am Ende dieser Schleife ``||AGENT:Agent bewege dich vorwärts um 1||`` hinzu, um den Agenten zu bewegen, während er Blöcke zerstört und platziert.

### ~ tutorialhint
``` blocks
player.onChat("quadrat", function () {
    for (let i = 0; i < 6; i++) {
        agent.destroy(DOWN)
        agent.place(DOWN)
        agent.move(FORWARD, 1)
    }
})

player.onChat("tp", function () {
    agent.teleportToPlayer()
})
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

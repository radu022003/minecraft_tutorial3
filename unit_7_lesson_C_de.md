### @explicitHints 1

# Aktivität: Einen Block nach dem anderen

## Schritt 1
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

## Schritt 2
Mach dich bereit, den Agenten auszurüsten. Um den Agenten dazu zu bringen, Dinge zu platzieren, müsst du ihn zuerst mit dem Block oder Gegenstand ausrüsten, den du platzieren möchtest. Ein Chat-Befehl könnte dies etwas einfacher machen, aber letztendlich gibt es aktuell noch keine vollautomatische Möglichkeit, dies zu tun. Ziehe dazu aus ``||Player:SPIELER||`` einen ``||Player:Bei Chat-Befehl||`` in die Arbeitsfläche.

## Schritt 3
Benennen den Befehl in **givegold** um.

Gehe zur Suche und finde **give**.

## Schritt 4
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

## Schritt 5
Rüsten den Agenten aus. Jetzt, da du Goldblöcke ausgerüstet hast, musst du deinen Agenten ausrüsten. Verwende den ``||Player:Bei Chat-Befehl 'tp'||``, um deinem Agenten in deine Nähe zu teleportieren, oder gehen zu deinem Agenten hinüber.

## Schritt 6
Klicke mit der rechten Maustaste auf deinen Agenten, um das Inventar des Agenten und das Inventar deines Charakters anzuzeigen. Übertragen die Goldblöcke zum Agenten. Jeder Gegenstand, den du möchtest, dass der Agent verwendet, muss zuerst in die obere linke Ecke seines Inventars gelegt werden! Genau dieser Ort, die obere linke Ecke, ist entscheidend! Es ist der einzige Ort, an dem es funktioniert.

## Schritt 7
Agent - Mach ein kleines Quadrat! Jetzt, da dein Agent Goldblöcke hat, ist es an der Zeit, etwas zu machen. Erinnerst du dich an Lektion 2 - Aktivität 1 - Gelber Ziegelweg? Lasse den Agenten dieses Mal ein Quadrat machen, das sich eines Tages mit dem gelben Ziegelweg verbinden könnte! Agenten können keine Blöcke ersetzen, aber sie können Dinge zerstören!

## Schritt 8
Lass uns den Boden zerstören und diese Blöcke durch Goldblöcke ersetzen. Duplizieren Sie zuerst ``||Player:Bei Chat-Befehl "fd"||`` und benenne es in **quadrat** um. Du kannst dies durch Rechtsklick und Auswahl von "Duplizieren" tun.

## Schritt 9
Um dein Quadrat zu erstellen, müsst du darüber nachdenken, was erforderlich ist, um es zu erstellen. Beginne mit dem großen Ziel und arbeite dich zu den kleinen Teilen vor, die erforderlich sind, um dies zu erreichen. Wenn du mit dem Codieren beginnen, arbeite zuerst am kleinsten Teil und füge mehr hinzu, während du fortfahrst. 

## Schritt 10
Beginne damit, nur einen Goldblock zu platzieren, um das Ziel zu erreichen. Welchen Code benötigst du dafür? Setze ``||Agent:Agent, zerstöre nach unten||`` aus ``||Agent:AGENT||`` in ``||Player:Bei Chat-Befehl "quadrat"||``.

## Schritt 11
Setze ``||Agent:Agent, platziere nach unten||`` innerhalb von ``||Player:Bei Chat-Befehl "quadrat"||``. Der Agent wird das platzieren, was sich in der oberen linken Ecke seines Inventars befindet, wie wir zuvor besprochen haben. In diesem Fall werden die Goldblöcke platziert. Nun sollte ``||Player:Bei Chat-Befehl "quadrat"||`` wie folgt aussehen:

### ~ tutorialhint
``` blocks 
player.onChat("quadrat", function () {
    agent.destroy(DOWN)
    agent.place(DOWN)
})

```

## Schritt 12
Erfolg! Jetzt versuchen wir, einen Schritt weiter zu gehen. Mit einer Schleife versuchen wir, eine Seite des Quadrats zu erstellen! Du benötigst, dass dein Agent sich bewegt und mehrmals bricht und platziert. Dies ist ein perfektes Problem für eine Schleife. Greifen dazu aus ``||Loops:SCHLEIFEN||`` eine ``||Loops:-mal wiederholen||``-Schleife und umschließe den vorhandenen Code in ``||Player:Bei Chat-Befehl "quadrat"||``.

## Schritt 13
Passen die ``||Loops:-mal wiederholen||``-Schleife an, damit sie sechs Mal wiederholt wird.

## Schritt 14
Füge am Ende dieser Schleife ``||Agent:Agent bewege dich vorwärts um 1||`` hinzu, um den Agenten zu bewegen, während er Blöcke zerstört und platziert.

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

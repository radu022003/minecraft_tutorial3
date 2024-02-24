### @explicitHints 1

# Aktivität: Einen Block nach dem anderen

## Schritt 1
Verwenden Sie die Aktivität "Einführung in den Agenten" als Ausgangscode. Dadurch können Sie Ihren Agenten leicht positionieren, und dann können Sie einige Teile davon anpassen, um etwas Neues zu tun.

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
Machen Sie sich bereit, den Agenten auszurüsten. Um Ihren Agenten dazu zu bringen, Dinge zu platzieren, müssen Sie ihn zuerst mit dem Block oder Gegenstand ausrüsten, den Sie platzieren möchten. Ein Chat-Befehl könnte dies etwas einfacher machen, aber letztendlich gibt es zum Zeitpunkt dieser Veröffentlichung keine vollautomatische Möglichkeit, dies zu tun. Ziehen Sie dazu aus ``||Player:SPIELER||`` einen ``||Player:Bei Chat-Befehl||`` in die Arbeitsfläche.

## Schritt 3
Benennen Sie den Befehl in **givegold** um.

Gehen Sie zur Suche und finden Sie **give**.

## Schritt 4
Geben Sie sich selbst Blöcke und rüsten Sie dann Ihren Agenten manuell aus. Ändern Sie den 'Give'-Befehl, sodass Sie Ihrem Charakter Goldblöcke geben. Das Maximum, das Sie in einem Inventarplatz halten können, beträgt 64, also geben Sie Ihrem Charakter **64** Blöcke **Gold**.

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
Rüsten Sie den Agenten aus. Jetzt, da Sie Goldblöcke ausgerüstet haben, müssen Sie Ihren Agenten ausrüsten. Verwenden Sie den ``||Player:Bei Chat-Befehl 'tp'||``, um Ihren Agenten in Ihre Nähe zu teleportieren, oder gehen Sie zu Ihrem Agenten hinüber.

## Schritt 6
Klicken Sie mit der rechten Maustaste auf Ihren Agenten, um das Inventar des Agenten und das Inventar Ihres Charakters anzuzeigen. Übertragen Sie die Goldblöcke an Ihren Agenten. Jeder Gegenstand, den Sie möchten, dass der Agent verwendet, muss zuerst in die obere linke Ecke seines Inventars gelegt werden! Genau dieser Ort, die obere linke Ecke, ist entscheidend! Es ist der einzige Ort, an dem es funktioniert.

## Schritt 7
Agent - Mach ein kleines Quadrat. Jetzt, da Ihr Agent Goldblöcke hat, ist es an der Zeit, etwas zu machen. Erinnern Sie sich an Lektion 2 - Aktivität 1 - Gelber Ziegelweg? Lassen Sie den Agenten dieses Mal ein Quadrat machen, das sich eines Tages mit dem gelben Ziegelweg verbinden könnte! Agenten können keine Blöcke ersetzen, aber sie können Dinge zerstören!

## Schritt 8
Lassen Sie uns den Boden zerstören und diese Blöcke durch Goldblöcke ersetzen. Duplizieren Sie zuerst ``||Player:Bei Chat-Befehl "fd"||`` und benennen Sie es in **quadrat** um. Sie können dies durch Rechtsklick und Auswahl von "Duplizieren" tun.

## Schritt 9
Um Ihr Quadrat zu erstellen, müssen Sie darüber nachdenken, was erforderlich ist, um es zu erstellen. Beginnen Sie mit dem großen Ziel und arbeiten Sie sich zu den kleinen Teilen vor, die erforderlich sind, um dies zu erreichen. Wenn Sie mit dem Codieren beginnen, arbeiten Sie zuerst am kleinsten Teil und fügen mehr hinzu, während Sie fortfahren. 

## Schritt 10
Agent - Mach ein kleines Quadrat. Beginnen wir damit, nur einen Goldblock zu platzieren, um Ihr Ziel zu erreichen. Welchen Code benötigen Sie dafür? Setzen Sie ``||Agent:Agent, zerstöre nach unten||`` aus ``||Agent:AGENT||`` in ``||Player:Bei Chat-Befehl "quadrat"||``.

## Schritt 11
Setzen Sie ``||Agent:Agent, platziere nach unten||`` innerhalb von ``||Player:Bei Chat-Befehl "quadrat"||``. Der Agent wird das platzieren, was sich in der oberen linken Ecke seines Inventars befindet, wie wir zuvor besprochen haben. In diesem Fall werden die Goldblöcke platziert. Nun sollte ``||Player:Bei Chat-Befehl "quadrat"||`` wie folgt aussehen:

### ~ tutorialhint
``` blocks 
player.onChat("quadrat", function () {
    agent.destroy(DOWN)
    agent.place(DOWN)
})

```

## Schritt 12
Erfolg! Jetzt versuchen wir, einen Schritt weiter zu gehen. Mit einer Schleife versuchen wir, eine Seite des Quadrats zu erstellen! Sie benötigen, dass Ihr Agent sich bewegt und mehrmals bricht und platziert. Dies ist ein perfektes Problem für eine Schleife. Greifen Sie dazu aus ``||Loops:SCHLEIFEN||`` eine ``||Loops:-mal wiederholen||``-Schleife und umschließen Sie den vorhandenen Code in ``||Player:Bei Chat-Befehl "quadrat"||``.

## Schritt 13
Passen Sie die ``||Loops:-mal wiederholen||``-Schleife an, damit sie sechs Mal wiederholt wird.

## Schritt 14
Fügen Sie am Ende dieser Schleife ``||Agent:Agent bewege dich vorwärts um 1||`` hinzu, um Ihren Agenten zu bewegen, während er Blöcke zerstört und platziert.

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

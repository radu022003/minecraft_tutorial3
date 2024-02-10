### @explicitHints 1
# Aktivität: Wortzauberer 

## Schritt 1
Ziehen Sie ``||Loops:beim Start||`` in die Arbeitsfläche.

Öffnen Sie ``||Variables: VARIABLEN ||``, erstellen Sie 2 neue Variablen und nennen Sie sie **Wort1** und **Wort2**. Fügen Sie ``||Variables: setze auf ||`` innerhalb von ``|| Loops: beim Start ||`` hinzu.

## Schritt 2
Klicken Sie auf **FORTGESCHRITTEN**, um die ``||Text: TEXT ||``-Werkzeugkategorie anzuzeigen. Wählen Sie ``||Variables||`` aus und platzieren Sie dies innerhalb von ``||Variables: setze auf ||``, um die Zahl **0** zu ersetzen. Sie werden diese Variable auf einen String setzen.

## Schritt 3
Verwenden Sie die Dropdown-Liste von ``||Variables: setze auf ||``, um **item** in **Wort1** umzubenennen.

Klicken Sie mit der rechten Maustaste auf ``||Variables: setze Wort1 ||`` und duplizieren Sie es. Legen Sie diese neue Duplikation in ``||Loops: beim Start ||``.

## Schritt 4
Gehen Sie jetzt zurück zum zweiten ``||Variables: setze Wort1 ||`` und ändern Sie **Wort1** in der Dropdown-Liste in **Wort2**.

### ~ tutorialhint
``` blocks
let Wort2 = ""
let Wort1 = ""
Wort1 = ""
Wort2 = ""
```

## Schritt 5
Schreiben Sie zwei lustige Wörter! Ersetzen Sie das leere **" "** durch Text für **Wort1**.

Ersetzen Sie das leere **" "** durch Text für **Wort2**. Hier ist ein Beispiel: **rail** für ``||Variables:Wort1||`` und **road** für ``||Variables:Wort2||``.

### ~ tutorialhint
``` blocks
let Wort2 = ""
let Wort1 = ""
Wort1 = "Schiene"
Wort2 = "Strasse""
```

## Schritt 6
Schreiben Sie Wort1. Ziehen Sie ``||Player:bei Chat-Befehl||`` in die Arbeitsfläche. Benennen Sie den Befehl **mix**.

Ziehen Sie den Block ``||Blocks:schreibe||`` in den ``||Player:bei Chat-Befehl mix||``-Block, um ihn einzurasten.

## Schritt 7
Platzieren Sie ``||Variables: Wort1 ||`` innerhalb von ``||Blocks: schreibe ||``.

Ändern Sie das Gras zu **Redstone-Erz**.

### ~ tutorialhint
``` blocks
let Wort2 = ""
let Wort1 = ""
player.onChat("mix", function () {
    blocks.print(
    Wort1,
    REDSTONE_ORE,
    pos(0, 0, 0),
    WEST
    )
})
Wort1 = "Schiene"
Wort2 = "Strasse""
```

##  Step 8
Setzen Sie Wort2. Duplizieren Sie ``||Blocks:schreibe||`` ``||Variables:Wort1||``.

Ändern Sie dies so, dass es ``||Variables:Wort2||`` ausgibt. Ändern Sie das **Gras** in **Redstone-Lampe**.

## Schritt 9
Fine-tune and test. You need to print in the air a bit to leave enough room for everything to fit. Also, you started printing **south** on the **north/south axis**. Adjust the ``||Blocks:schreibe||``, so it reads **along South (positive Z)**.
Feinabstimmung und Testen. Sie müssen ein wenig in die Luft schreiben, um genügend Platz für alles zu lassen. Außerdem haben Sie angefangen, in Richtung **Süden** auf der **Nord/Süd-Achse** zu schreiben. Passen Sie den ``||Blocks: schreibe ||``-Block an, so dass er **entlang Süden (positive Z)** liest.

### ~ tutorialhint
```blocks
let Wort2 = ""
let Wort1 = ""
player.onChat("mix", function () {
    blocks.print(
    Wort1,
    REDSTONE_ORE,
    pos(0, 0, 0),
    SOUTH
    )
})
Wort1 = "Schiene"
Wort2 = "Strasse""
```

## Schritt 10
Deine beiden Wörter werden jetzt geschrieben, aber es gibt ein kleines Problem. Wenn du dich nach dem Tippen von **mix** nicht mehr bewegst, werden die beiden Wörter nicht ausgerichtet, wenn sie gedruckt werden.

## Schritt 11
Um das zu beheben, speichern Sie die Weltposition Ihres Spielers. Klicken Sie auf **Erstelle eine Variable** und geben Sie der neuen Variable den Namen **Startposition_Welt**.

Fügen Sie ``||Variables:setze auf||`` oben in ``||Player:bei Chat-Befehl mix||`` ein. Ändern Sie diesen Block so, dass er **Setze Startposition_Welt** liest.

## Schritt 12
Platzieren Sie ``||Player:Position des Spieler in der Welt||`` in ``||Variables:setze Startposition_Welt||``.

### ~ tutorialhint
``` blocks
let Wort2 = ""
let Startposition_Welt: Position = null
let Wort1 = ""
player.onChat("mix", function () {
    Startposition_Welt = player.position()
    blocks.print(
    Wort1,
    REDSTONE_ORE,
    pos(0, 30, 0),
    SOUTH
    )
    blocks.print(
    Wort2,
    REDSTONE_LAMP,
    pos(0, 20, 0),
    SOUTH
    )
})
Wort1 = "Schiene"
Wort2 = "Strasse""
```

## Schritt 13
Korrigieren Sie die Position des Schreibblocks.

### ~ tutorialhint
``` blocks
let Wort2 = ""
let Startposition_Welt: Position = null
let Wort1 = ""
player.onChat("mix", function () {
    Startposition_Welt = player.position()
    blocks.print(
    Wort1,
    REDSTONE_ORE,
    positions.add(
    Startposition_Welt,
    pos(0, 30, 0)
    ),
    SOUTH
    )
    blocks.print(
    Wort2,
    REDSTONE_LAMP,
    positions.add(
    Startposition_Welt,
    pos(0, 20, 0)
    ),
    SOUTH
    )
})
Wort1 = "Schiene"
Wort2 = "Strasse""
```

## Schritt 14
Verbinden und drucken Sie. Duplizieren Sie einen der ``||Blocks:schreibe||``-Blöcke und platzieren Sie ihn am unteren Rand von ``||Player:bei Chat-Befehl mix||``.

Passen Sie die Einstellungen so an, dass Sie mit **Block aus Redstone** schreiben.

## Schritt 15
Die relative **Y**-Koordinate sollte **5** sein.

## Schritt 16
Suchen Sie nach "verbinde". Platzieren Sie diesen ``||Text:TEXT||``-Block, damit der ``||Blocks:schreibe||``-Block **schreibe verbinde Wort1 Wort2** liest.

### ~ tutorialhint
``` blocks
let Wort2 = ""
let Wort1 = ""
let Startposition_Welt: Position = null
player.onChat("mix", function () {
    Startposition_Welt = player.position()
    blocks.print(
    Wort1,
    REDSTONE_ORE,
    positions.add(
    Startposition_Welt,
    pos(0, 30, 0)
    ),
    SOUTH
    )
    blocks.print(
    Wort2,
    REDSTONE_LAMP,
    positions.add(
    Startposition_Welt,
    pos(0, 20, 0)
    ),
    SOUTH
    )
    blocks.print(
    Wort1 + Wort2,
    REDSTONE_BLOCK,
    positions.add(
    Startposition_Welt,
    pos(0, 5, 0)
    ),
    SOUTH
    )
})
Wort1 = "Schiene"
Wort2 = "Strasse""
```

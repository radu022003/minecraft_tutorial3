### @explicitHints 1
# Aktivität: Wortzauberer 

## Schritt 1
Öffne ``||Variables: VARIABLEN ||`` und erstelle 2 neue Variablen mit den Namen **Wort1** und **Wort2**. 

## Schritt 2
Füge zwei ``||Variables: setze auf ||``-Blöcke in den ``|| Loops: beim Start ||``-Block hinein.

## Schritt 3
Wähle im ersten ``||Variables: setze auf ||``-Block die Variable ``||Variables:Wort1||`` aus.

Dann wähle im zweiten ``||Variables: setze auf ||``-Block die Variable ``||Variables:Wort2||`` aus.

### ~ tutorialhint
``` blocks
let Wort2 = ""
let Wort1 = ""
Wort1 = ""
Wort2 = ""
```

## Schritt 4
Schreibe, in die Lücke von den ``||Variables:setze Wort1/2 auf||``-Blöcken, zwei beliebige Wörter, mit Anführungszeichen(" "), hinein.0

Zum Beispiel: **setze Wort1 auf "Schiene"** und **setze Wort2 auf "Straße"**

### ~ tutorialhint
``` blocks
let Wort2 = ""
let Wort1 = ""
Wort1 = "Schiene"
Wort2 = "Straße"
```

## Schritt 5
Ziehe ein ``||Player:bei Chat-Befehl||``-Block in die Arbeitsfläche und schreibe **mix** in die Lücke.

Ziehen ein ``||Blocks:schreibe||``-Block in den ``||Player:bei Chat-Befehl mix||``-Block.

## Schritt 6
Platziere die ``||Variables: Wort1 ||``-Variable in den ``||Blocks: schreibe ||``-Block.

Ände das Gras zu **Redstone-Erz**.

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

##  Schritt 7
Dupliziere den ``||Blocks:schreibe||``-Block und ersätze die ``||Variables:Wort1||``-Variable mit ``||Variables:Wort2||``-Variable.

Dann ändere das **Redstone-Erz** in **Redstone-Lampe**.

## Schritt 8
Dupliziere den ``||Blocks:schreibe||``-Block noch einmal und ersätze die ``||Variables:Wort1||``-Variable mit dem ``||Text:verbinde||``-Block. 

Füge in die erste Lücke vom ``||Text:verbinde||``-Block die ``||Variables:Wort1||``-Variable und in die zweite Lücke ``||Variables:Wort2||``-Variable 

Dann ändere die **Redstone-Lampe** in **Redstone-Block**.

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
Erstelle eine neue ``||Variables:Variable||`` und nenne es **Startposition-Welt**.

Füge ein ``||Variables:setze auf||``_block in den ``||Player:bei Chat-Befehl mix||``-Block ein. Ändere diesen Block so, dass er **Setze Startposition-Welt** heißt.

## Schritt 12
Platziere ein ``||Player:Position des Spieler in der Welt||``-Block in den ``||Variables:setze Startposition-Welt||``-Block.

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
Verschiebe den **setze Startposition-Welt auf**-Block ganz nach Oben.

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


## Schritt 15
Die relative **Y**-Koordinate sollte von ``Variables:Wort1||``-Variable **30**, ``Variables:Wort2||``-Variable **20** und von ``Variables:Wort1 + Wort2||``-Variable **5**, sein.

Füge für die Koordinaten den ``||positions:"+"||``-Block hinzu und setze in die ersten Lücken die ``||Variables:Startposition_Welt||``-Variable hinzu.

Dann setze für  die **Y**-Koordinaten die Werte von oben ein.
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

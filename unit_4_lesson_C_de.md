### @explicitHints 1
# Aktivität: Wortzauberer 

## 1. Variable erstellen
Öffne ``||VARIABLES: VARIABLEN ||`` und erstelle 2 neue Variablen mit den Namen **Wort1** und **Wort2**. 

## 2. Variablenblöcke hinzufügen
Füge zwei ``||VARIABLES: setze auf ||``-Blöcke in den ``|| Loops: beim Start ||``-Block hinein.

## 3. Variable setzen
Wähle im ersten ``||VARIABLES: setze auf ||``-Block die Variable ``||VARIABLES:Wort1||`` aus.

Dann wähle im zweiten ``||VARIABLES: setze auf ||``-Block die Variable ``||VARIABLES:Wort2||`` aus.

### ~ tutorialhint
``` blocks
let Wort2 = ""
let Wort1 = ""
Wort1 = ""
Wort2 = ""
```

## 4. Variable setzen
Schreibe, in die Lücke von den ``||VARIABLES:setze Wort1/2 auf||``-Blöcken, zwei beliebige Wörter, mit dem ``||TEXT:Anführungszeichen-Block " "||`` in *FORTGESCHRITTEN*, hinein.

Zum Beispiel: **setze Wort1 auf "Schiene"** und **setze Wort2 auf "Straße"**

### ~ tutorialhint
``` blocks
let Wort2 = ""
let Wort1 = ""
Wort1 = "Schiene"
Wort2 = "Straße"
```

## 5. Chat-Befehl anlegen
Ziehe ein ``||PLAYER:bei Chat-Befehl||``-Block in die Arbeitsfläche und schreibe **mix** in die Lücke.

Ziehen ein ``||BLOCKS:schreibe||``-Block in den ``||PLAYER:bei Chat-Befehl mix||``-Block.

## 6. Text platzieren
Platziere die ``||VARIABLES: Wort1 ||``-Variable in den ``||BLOCKS: schreibe ||``-Block.

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
Wort2 = "Strasse"
```

## 7. Block duplizieren
Dupliziere den ``||BLOCKS:schreibe||``-Block und ersetze die ``||VARIABLES:Wort1||``-Variable mit ``||VARIABLES:Wort2||``-Variable.

Dann ändere das **Redstone-Erz** in **Redstone-Lampe**.

## 8. Block duplizieren
Dupliziere den ``||BLOCKS:schreibe||``-Block noch einmal und ersetze die ``||VARIABLES:Wort1||``-Variable mit dem ``||TEXT:verbinde||``-Block. 

Füge in die erste Lücke vom ``||TEXT:verbinde||``-Block die ``||VARIABLES:Wort1||``-Variable und in die zweite Lücke ``||VARIABLES:Wort2||``-Variable.

Dann ändere die **Redstone-Lampe** in **Redstone-Block**.

## 9. Code testen
Teste deinen Code in Minecraft: Gib im Chat **mix** ein. Die drei Wörter (Wort1, Wort2 und die Kombination) werden in verschiedenen Höhen in der Luft geschrieben.

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
Wort2 = "Strasse"
```

## 10. Position speichern
Deine beiden Wörter werden jetzt geschrieben, aber es gibt ein kleines Problem. Wenn du dich nach dem Tippen von **mix** nicht mehr bewegst, werden die Wörter möglicherweise falsch ausgerichtet.

## 11. Variable erstellen
Erstelle eine neue ``||VARIABLES:Variable||`` und nenne sie **Startposition-Welt**.

Füge einen ``||VARIABLES:setze auf||``-Block in den ``||PLAYER:bei Chat-Befehl mix||``-Block ein. Wähle **Startposition-Welt** als Variable aus.

## 12. Spieler-Position erfassen
Platziere einen ``||PLAYER:Position des Spielers in der Welt||``-Block in den ``||VARIABLES:setze Startposition-Welt||``-Block.

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
Wort2 = "Strasse"
```

## 13. Variable setzen
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
Wort2 = "Strasse"
```


## 15. Koordinaten setzen
Die relative **Y**-Koordinate sollte für ``||VARIABLES:Wort1||`` **30**, für ``||VARIABLES:Wort2||`` **20** und für ``||VARIABLES:Wort1 + Wort2||`` **5** betragen.

Füge für die Koordinaten den ``||positions:"+"||``-Block hinzu und setze in die erste Lücke die ``||VARIABLES:Startposition_Welt||``-Variable.

Dann setze die **Y**-Koordinaten in der zweiten Lücke auf die Werte von oben.
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
Wort2 = "Strasse"
```

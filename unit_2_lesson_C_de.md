### @explicitHints 1

# Der verknüpfte Wand

## 1. Start
Du hast einige Startercodes erhalten, die du für deinen Programm verwenden kannst. Nutze sie!
Füge nun einen neuen Ereignis``||Player: Bei Chat-Befehl||`` hinzu. Ändere den Text "jump" zu "wand".

```template
let PlayerPosition: Position = null
let from_position: Position = null
let to_position: Position = null
player.onChat("position", function () {
    PlayerPosition = player.position()
    from_position = positions.add(
    PlayerPosition,
    pos(6, 0, 0)
    )
    to_position = positions.add(
    PlayerPosition,
    pos(-6, 13, 0)
    )
})
```

## 2. Baue eine Wand
Wähle aus ``||Blocks:Blöcken||`` den ``||Blocks:fülle mit||``-Block und platziere es innerhalb des ``||Player:Bei Chat-Befehl "wand"||``.

### ~ tutorialhint
 ```blocks
        player.onChat("wall", function () {
                blocks.fill(
                GRASS,
                pos(0, 0, 0),
                pos(0, 0, 0),
                FillOperation.Replace
                )
})
```

## 3. GLAS statt Gras
Ändere **Gras** zu **Glas** im des Block ``||Blocks:fülle mit||``.

## 4. Variablen
Ziehe aus ``||Variables:VARIABLEN||`` den Block ``||Variables:from_position||``  in den **von**-Teil des Blocks ``||Blocks:fülle mit||``.

## 5. Variablen
Als nächstes ziehe ``||Variables:to_position||`` in den **nach**-Teil des Blocks ``||Blocks:fülle mit||``. Probiere den Code in Minecraft aus.

### ~ tutorialhint
 ```blocks
        player.onChat("wall", function () {
                blocks.fill(
                GLASS,
                from_position,
                to_position,
                FillOperation.Replace
                )
})
```

## 6. Blockabbau erkennen
Ziehe aus ``||Blocks:BLÖCKE||`` den ``||Blocks:wenn _ abgebaut||``-Block in den Arbeitsbereich.

## 7. GLAS statt Gras (wieder)
Ändere **Gras** zu **Glas**.

## 8. Block platzieren, wenn abgebaut
Aus ``||Blocks:BLÖCKE||`` platziere einen ``||Blocks:platziere _ bei||``-Block in den ``||Blocks:wenn Glas abgebaut||``-Block.

## 9. 💎 statt Gras
Ändere **Gras** zu einem **Diamantblock**.

### ~ tutorialhint
```blocks
blocks.onBlockBroken(GLASS, function () {
    blocks.place(DIAMOND_BLOCK, pos(0, 0, 0))
})
```
## 10. Zufällige Position
Platziere den ``||Positions:wähle zufällige Position||``-Block in den ``||Blocks:platziere Diamant||``-Block.

## 11. Variablen
Setze ``||Variables:from_position||`` in den **von**-Teil von diesem Block.

Setze ``||Variables:to_position||`` in den **bis**-Teil von diesem Block.

### ~ tutorialhint
```blocks
blocks.onBlockBroken(GLASS, function () {
    blocks.place(DIAMOND_BLOCK, randpos(
    from_position,
    to_position
    ))
})
```

## 12. Duplizieren
Dupliziere den ``||Blocks:wenn Glas abgebaut||``-Block und ändere einige Dinge.
Ersetze **Glas** durch einen **Diamantblock**.

## 13. Änderungen
Ändere dann ``||Blocks:platziere Diamant bei||`` zu ``||Blocks:platziere orange Wolle bei||``.

### ~ tutorialhint

```blocks

let to_position: Position = null
let from_position: Position = null
let PlayerPosition: Position = null
blocks.onBlockBroken(GLASS, function () {
    blocks.place(DIAMOND_BLOCK, randpos(
    from_position,
    to_position
    ))
})
blocks.onBlockBroken(DIAMOND_BLOCK, function () {
    blocks.place(ORANGE_WOOL, randpos(
    from_position,
    to_position
    ))
})
player.onChat("wall", function () {
    blocks.fill(
    GLASS,
    from_position,
    to_position,
    FillOperation.Replace
    )
})
player.onChat("position", function () {
    PlayerPosition = player.position()
    from_position = positions.add(
    PlayerPosition,
    pos(6, 0, 0)
    )
    to_position = positions.add(
    PlayerPosition,
    pos(-6, 13, 0)
    )
})
```
## 14. Code testen
Probiere es jetzt in Minecraft aus.
Rufe zuerst den Befehl "position" im Chat auf und anschließend den Befehl "wand".
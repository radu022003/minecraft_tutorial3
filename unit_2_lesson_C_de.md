### @explicitHints 1

# Die verknüpfte Wand

## 1. Start
Du hast einen Starter-Code erhalten, der bereits einen ``||PLAYER:bei Chat-Befehl "position"||``-Block enthält. Dieser speichert deine aktuelle Position und berechnet automatisch zwei Punkte für die Wand.

Füge jetzt einen **neuen** ``||PLAYER:bei Chat-Befehl||``-Block in die Arbeitsfläche ein und ändere den Text von **"run"** zu **"wand"**.

**Hinweis:** Den vorhandenen "position"-Block musst du **nicht** ändern – er wird später benötigt!

```template
let PlayerPosition: Position = null
let von_position: Position = null
let bis_position: Position = null
player.onChat("position", function () {
    PlayerPosition = player.position()
    von_position = positions.add(
    PlayerPosition,
    pos(6, 0, 0)
    )
    bis_position = positions.add(
    PlayerPosition,
    pos(-6, 13, 0)
    )
})
```

## 2. Baue eine Wand
Wähle aus ``||BLOCKS:Blöcken||`` den ``||BLOCKS:fülle mit||``-Block und platziere ihn innerhalb des ``||PLAYER:bei Chat-Befehl "wand"||``.

### ~ tutorialhint
 ```blocks
        player.onChat("wand", function () {
                blocks.fill(
                GRASS,
                pos(0, 0, 0),
                pos(0, 0, 0),
                FillOperation.Replace
                )
})
```

## 3. GLAS statt Gras
Ändere **Gras** zu **Glas** im Block ``||BLOCKS:fülle mit||``.

## 4. Variablen – Von-Position
Ziehe aus ``||VARIABLEN:VARIABLEN||`` den Block ``||VARIABLEN:von_position||`` in den **von**-Teil des Blocks ``||BLOCKS:fülle mit||``.

Diese Variable enthält die Position, die beim Ausführen des "position"-Befehls gespeichert wurde.

## 5. Variablen – Bis-Position
Ziehe als Nächstes ``||VARIABLEN:bis_position||`` in den **bis**-Teil des Blocks ``||BLOCKS:fülle mit||``.

**So testest du den Code in Minecraft:**
1. Drücke **T** um das Chat-Fenster zu öffnen.
2. Tippe **position** ein und drücke Enter – das speichert deine aktuelle Position.
3. Tippe dann **wand** ein und drücke Enter – die Glaswand erscheint!

**Tipp:** Der "position"-Befehl **muss zuerst** eingegeben werden, sonst weiß der Code nicht, wo die Wand entstehen soll.

### ~ tutorialhint
 ```blocks
    player.onChat("wand", function () {
                blocks.fill(
                GLASS,
        von_position,
        bis_position,
                FillOperation.Replace
                )
})
```

## 6. Blockabbau erkennen
Ziehe aus ``||BLOCKS:BLÖCKE||`` den ``||BLOCKS:wenn _ abgebaut||``-Block in den Arbeitsbereich.

## 7. GLAS statt Gras (wieder)
Ändere **Gras** zu **Glas**.

## 8. Block platzieren, wenn abgebaut
Aus ``||BLOCKS:BLÖCKE||`` platziere einen ``||BLOCKS:platziere _ bei||``-Block in den ``||BLOCKS:wenn Glas abgebaut||``-Block.

## 9. 💎 statt Gras
Ändere **Gras** zu einem **Diamantblock**.

### ~ tutorialhint
```blocks
blocks.onBlockBroken(GLASS, function () {
    blocks.place(DIAMOND_BLOCK, pos(0, 0, 0))
})
```
## 10. Zufällige Position
Platziere den ``||POSITIONEN:wähle zufällige Position||``-Block in den ``||BLOCKS:platziere Diamant||``-Block.

## 11. Variablen
Setze ``||VARIABLEN:von_position||`` in den **von**-Teil von diesem Block.

Setze ``||VARIABLEN:bis_position||`` in den **bis**-Teil von diesem Block.

### ~ tutorialhint
```blocks
blocks.onBlockBroken(GLASS, function () {
    blocks.place(DIAMOND_BLOCK, randpos(
    von_position,
    bis_position
    ))
})
```

## 12. Duplizieren
Dupliziere den ``||BLOCKS:wenn Glas abgebaut||``-Block:

**So duplizierst du in MakeCode:**
1. Klicke mit der **rechten Maustaste** auf den Block.
2. Wähle **"Duplizieren"** aus dem Menü.
3. Eine exakte Kopie des Blocks erscheint in der Arbeitsfläche.

Nach dem Duplizieren: Ändere im neuen Block **Glas** zu **Diamantblock** (als Auslöser).

## 13. Änderungen
Ändere dann ``||BLOCKS:platziere Diamant bei||`` zu ``||BLOCKS:platziere orange Wolle bei||``.

### ~ tutorialhint

```blocks

let bis_position: Position = null
let von_position: Position = null
let PlayerPosition: Position = null
blocks.onBlockBroken(GLASS, function () {
    blocks.place(DIAMOND_BLOCK, randpos(
    von_position,
    bis_position
    ))
})
blocks.onBlockBroken(DIAMOND_BLOCK, function () {
    blocks.place(ORANGE_WOOL, randpos(
    von_position,
    bis_position
    ))
})
player.onChat("wand", function () {
    blocks.fill(
    GLASS,
    von_position,
    bis_position,
    FillOperation.Replace
    )
})
player.onChat("position", function () {
    PlayerPosition = player.position()
    von_position = positions.add(
    PlayerPosition,
    pos(6, 0, 0)
    )
    bis_position = positions.add(
    PlayerPosition,
    pos(-6, 13, 0)
    )
})
```
## 14. Code testen
Probiere es jetzt in Minecraft aus.
Rufe zuerst den Befehl "position" im Chat auf und anschließend den Befehl "wand".

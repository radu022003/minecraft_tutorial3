### @explicitHints 1

# Der verknüpfte Wall

## Schritt 1
Hole dir einen Vorsprung. Du hast einige Startercodes erhalten, die du für diese Aktivität verwenden kannst. Füge nun einen neuen Ereignis-Handler ``||Player: Bei Chat-Befehl||`` hinzu. Ändere "jump" zu "wall".

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

## Schritt 2
Erbaue eine Wand: Wähle aus ``||Blocks:Blöcke||`` einen Block ``||Blocks:fülle mit||``und platziere ihn innerhalb des Ereignis-Handlers ``||Player:Bei Chat-Befehl "wall"||``.

## Schritt 3
Passe einige Dinge an: Ändere **Gras** zu **Glas** innerhalb des Blocks ``||Blocks:fülle mit||``.

## Schritt 4
Ziehe aus ``||Variables:VARIABLEN||`` den Block ``||Variables:from_position||``  in den **von** Block ``||Blocks:fülle mit||``.

## Schritt 5
Als nächstes ziehe ``||Variables:to_position||`` in den **nach**-Teil des Blocks ``||Blocks:fülle mit||``. Probiere den Befehl in Minecraft aus.

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

## Schritt 6
Reagiere, wenn Blöcke zerstört werden. Ziehe aus ``||Blocks:BLÖCKE||`` einen Block ``||Blocks:wenn abgebaut||`` in den Arbeitsbereich..

## Schritt 7
Ändere **Gras** zu **Glas**.

## Schritt 8
Aus ``||Blocks:BLÖCKE||`` platziere einen Block ``||Blocks:platziere an||`` in den Block ``||Blocks:wenn abgebaut||``.

## Schritt 9
Ändere **Gras** zu **Diamant**.

### ~ tutorialhint
```blocks
blocks.onBlockBroken(GLASS, function () {
    blocks.place(DIAMOND_BLOCK, pos(0, 0, 0))
})
```
## Schritt 10
Behebe den Positionscode. Platziere den Block ``||Positions:wähle zufällige Position||`` in den Block ``||Blocks:platziere Diamant||``. 

## Schritt 11
Setze ``||Variables:from_position||`` in den **von**-Teil in diesem Block.

Setze ``||Variables:to_position||`` in den **bis**-Teil in diesem Block.  

### ~ tutorialhint
```blocks
blocks.onBlockBroken(GLASS, function () {
    blocks.place(DIAMOND_BLOCK, randpos(
    from_position,
    to_position
    ))
})
```

## Schritt 12
Dupliziere den Block ``||Blocks:wenn abgebaut Glas||``und ändere einige Dinge. Ersetze **Glas** durch **Diamant**.

## Schritt 13
Ändere dann ``||Blocks:platziere Diamant||`` to ``||Blocks:platziere orange Wolle||``.  

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
## Schritt 14
Probiere es jetzt in Minecraft aus.
Ruff erstmal die Befehl "position" im Chat aus und dann ruff die Befehl "wall" im Chat
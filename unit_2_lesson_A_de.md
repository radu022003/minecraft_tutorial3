### @explicitHints 1

# Aktivität: Goldspur

## 1. Spieler-Bewegung erkennen
Ziehe den ``||PLAYER:bei gehen Spieler||`` Block in den Programmierbereich.

Dieser Block führt den Code darin aus, **jedes Mal wenn du dich bewegst**.

### ~ tutorialhint
``` blocks
player.onTravelled(WALK, function () {

})
```

## 2. Block platzieren
Ziehe den ``||BLOCKS:platziere bei||`` Block in den ``||PLAYER:bei gehen Spieler||`` Block.

Damit wird bei jeder Bewegung ein Block an einer bestimmten Position gesetzt.

### ~ tutorialhint
``` blocks
player.onTravelled(WALK, function () {
    blocks.place(GRASS, pos(0, 0, 0))
})
```

## 3. Was bedeuten die Koordinaten?
Im ``||BLOCKS:platziere bei||``-Block siehst du drei Zahlen: **~0, ~0, ~0**.

Das sind **relative Koordinaten** – sie geben an, wie weit der Block **relativ zu deinem Spieler** platziert wird:

- **X (~0)** = links / rechts
- **Y (~0)** = oben / unten
- **Z (~0)** = vor / zurück

Mit `~0, ~0, ~0` wird der Block genau **an deiner aktuellen Position** gesetzt.
Mit `~0, ~2, ~0` wäre er **2 Blöcke über dir**.
Mit `~0, ~-1, ~0` wäre er **1 Block unter dir** (im Boden).
Mit `~0, ~0, ~2` wäre er **2 Blöcke hinter dir**.

## 4. Blumen platzieren
Wähle den **Löwenzahn** (gelbe Blume) aus dem Dropdown-Menü im ``||BLOCKS:platziere bei||``, um den Gras-Block zu ersetzen.

### ~ tutorialhint
``` blocks
player.onTravelled(WALK, function () {
    blocks.place(YELLOW_FLOWER, pos(0, 0, 0))
})
```

## 5. Code testen
Wechsle zu Minecraft und laufe für ein paar Sekunden. Drehe dich um und schaue auf deinen Blumenpfad!

Wenn du rückwärts läufst, kannst du zusehen, wie die Blumen direkt aus dem Boden springen, während du dich bewegst.

## 6. Teste es mit Gold!
Im ``||BLOCKS:platziere bei||`` ersetze die Blume im Dropdown-Menü mit einem **Gold-Block**.

### ~ tutorialhint
``` blocks
player.onTravelled(TravelMethod.Walk, function () {
    blocks.place(GOLD_BLOCK, pos(0, 0, 0))
})
```

## 7. Problem entdeckt!
Schaue in Minecraft, was passiert: Du hinterlässt eine senkrechte **Goldwand** – das sieht ziemlich seltsam aus!

Das liegt daran, dass der Block **an deiner Spielerposition** (also auf gleicher Höhe wie du) platziert wird. Wie könntest du die Blöcke **eine Ebene tiefer** setzen, sodass sie einen Weg im Boden bilden?

**Tipp:** Denk an die Y-Koordinate!

## 8. Koordinaten anpassen
Ändere die **Y-Koordinate** auf **-1** (minus 1), damit die Blöcke eine Ebene tiefer liegen – direkt unter deinen Füßen.

### ~ tutorialhint
``` blocks
player.onTravelled(TravelMethod.Walk, function () {
    blocks.place(GOLD_BLOCK, pos(0, -1, 0))
})
```

## 9. Goldspur – es klappt!
Teste deinen Code erneut in Minecraft. Jetzt entsteht eine goldene Spur direkt im Boden! Probiere auch andere Koordinaten aus:

- `~0, ~1, ~0` → Block **über** dir
- `~2, ~-1, ~0` → Block **2 Felder rechts** von dir
- `~0, ~-1, ~3` → Block **3 Felder vor** dir

## 10. Erstelle eine goldene Straße
Ersetze den ``||BLOCKS:platziere bei||``-Block durch den ``||BLOCKS:fülle mit||``-Block aus dem Menü. Damit kannst du mehrere Blöcke auf einmal setzen und eine **3 Blöcke breite Goldstraße** bauen!

Setze die Koordinaten auf **von (~-1, ~-1, ~-1)** und **bis (~1, ~-1, ~1)**.

### ~ tutorialhint
``` blocks
player.onTravelled(TravelMethod.Walk, function () {
    blocks.fill(
        GOLD_BLOCK,
        pos(-1, -1, -1),
        pos(1, -1, 1),
        FillOperation.Replace
    )
})
```

## 11. Bonus: Nur beim Schleichen!
Möchtest du, dass die Goldspur **nur erscheint, wenn du schleichst**? Ändere im ``||PLAYER:bei gehen Spieler||``-Block das Dropdown-Menü von **Gehen** auf **Schleichen**.

Teste es in Minecraft: Halte die **Umschalttaste (Shift)** gedrückt – die Spur erscheint jetzt nur beim Schleichen!

### ~ tutorialhint
``` blocks
player.onTravelled(TravelMethod.Sneak, function () {
    blocks.fill(
        GOLD_BLOCK,
        pos(-1, -1, -1),
        pos(1, -1, 1),
        FillOperation.Replace
    )
})
```


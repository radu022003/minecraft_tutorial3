### @explicitHints 1

# Aktivität: Gelber Ziegelweg

## 1. Spieler-Bewegung erkennen
Ziehe den ``||Player: bei gehen Spieler||`` Block in den Programmierbereich.

### ~ tutorialhint
``` blocks
         player.onTravelled(WALK, function () {
	
})
```

## 2. Gras platzieren 
 Ziehe den ``||Blocks:platziere bei||`` Block in den ``||Player:bei gehen Spieler||`` Block.

### ~ tutorialhint      
``` blocks
         player.onTravelled(WALK, function () {
   		 blocks.place(GRASS, pos(0, 0, 0))
})
```

## 3. Blumen paltzieren
Wähle den Löwenzahn (gelbe Blume) aus dem Dropdown-Menü im ``||Blocks: platziere bei||``, um den **Grass-Block** zu ersetzen. 

### ~ tutorialhint
        ```blocks
         player.onTravelled(WALK, function () {
    blocks.place(YELLOW_FLOWER, pos(0, 0, 0))
})
        ```

## 4. Code testen
Gehe zu Minecraft und laufe für eine Sekunde oder zwei. Drehe dich um und schaue auf deinen Blumenpfad. Wenn du rückwärts läufst, kannst du zusehen, wie die Blumen aus dem Boden sprießen, während du dich bewegst.


## 5. Teste es mit Gold!

Im  ``||Blocks: Platziere bei||`` ersetze die Blume im Dropdown-Menü mit einem Gold-Block.

### ~ tutorialhint
``` blocks
player.onTravelled(TravelMethod.Walk, function () {
blocks.place(GOLD_BLOCK, pos(0, 0, 0))
})
```

## 6. Code testen
Schau, was passiert. Das ist die richtige Idee, aber nicht genau das, was du erreichen möchtest. Tatsächlich hinterlässt du eine Goldwand, was ziemlich unpraktisch ist. Wie könntest du diese Blöcke im Boden versenken, sodass sie einen gelben Ziegelweg bilden?

## 7. Koordinaten ändern   
Ändere die **Y-Koordinate**, indem du es mit 1 **subtrahierst** (-), damit die Blöcke eine Ebene tiefer liegen.

### ~ tutorialhint
``` blocks
player.onTravelled(TravelMethod.Walk, function () {
blocks.place(GOLD_BLOCK, pos(0, -1, 0))
})
```

## 8. Erstelle eine Straße  
Schaue, was im Spiel passiert, und **füge** einen anderen Block aus dem Menü ``||Blocks: fülle Mit||`` **hinzu**! (Ändere den Code so, dass du einen 3-Blöcke breiten Weg hast.)

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


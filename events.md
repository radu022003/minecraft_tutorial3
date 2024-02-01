### @explicitHints 1

# Aktivität: Gelber Ziegelweg

## Schritt 1 
Hören auf das Ereignis "Gehen". Ziehe ``||Player: on player walk||`` den Block in den Programmierbereich.

### ~ tutorialhint
``` blocks
         player.onTravelled(WALK, function () {
	
})
```

## Schritt 2 
Platziere etwas Gras. Ziehe den ``||Blocks: Place at||`` Block unter den ``||Player:On player walk||`` Block, bis du ein Einrasten hörst und siehst.

### ~ tutorialhint      
``` blocks
         player.onTravelled(WALK, function () {
   		 blocks.place(GRASS, pos(0, 0, 0))
})
```

## Schritt 3
Setze eine Blume. Wähle den Löwenzahn (gelbe Blume) aus dem Dropdown-Menü ``||Blocks: place at||``, um den **Grass-Block** zu ersetzen. 

### ~ tutorialhint
        ```blocks
         player.onTravelled(WALK, function () {
    blocks.place(YELLOW_FLOWER, pos(0, 0, 0))
})
        ```

## Schritt 4 
Gehe zu Minecraft und laufe für eine Sekunde oder zwei. Drehe dich um und schaue auf deinen Blumenpfad. Wenn du rückwärts läufst, kannst du zusehen, wie die Blumen aus dem Boden sprießen, während du dich bewegst.


## Schritt 5: Try with Gold!

Füge Gold hinzu. Ziehe den Block ``||Spieler: Beim Spieler gehen||`` in den Programmierbereich. Füge den Block ``||Blöcke: Platziere an||`` hinzu und platziere Gold anstelle einer Blume.

### ~ tutorialhint
``` blocks
player.onTravelled(TravelMethod.Walk, function () {
blocks.place(GOLD_BLOCK, pos(0, 0, 0))
})
```

## Schritt 6
Schau, was passiert. Das ist die richtige Idee, aber nicht genau das, was du erreichen möchtest. Tatsächlich hinterlässt du eine Goldwand, was ziemlich unpraktisch ist. Wie könntest du diese Blöcke im Boden versenken, sodass sie einen gelben Ziegelweg bilden?

## Schritt 7  
Ändere die Y-Koordinate. Modifiziere die **Y-Koordinate**, indem du 1 **subtrahierst**, damit die Unterteile der Ziegelsteine eine Ebene tiefer liegen.

### ~ tutorialhint
``` blocks
player.onTravelled(TravelMethod.Walk, function () {
blocks.place(GOLD_BLOCK, pos(0, -1, 0))
})
```

## Schritt 8 
Erstelle eine ordentliche Ziegelstraße. Schaue, was im Spiel passiert, und **füge** einen anderen Block aus dem Menü ``||Blocks: Blocks||`` **hinzu**!

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


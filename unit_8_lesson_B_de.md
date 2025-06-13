
### @explicitHints 1

# Aktivität: Wir bauen einen Zoo

## Schritt 1
Erstelle eine neue Variable und nenne sie **animalarray**.

Ziehe den ``||Variables:setze animalarray auf||``-Block in den ``||Loops:beim Start||``-Block.

## Schritt 2
Ziehe einen ``||Arrays:leeres Array||``-Block in den ``||Variables:setze animalarray auf||``-Block.

## Schritt 3
Füge Tiere zum Array hinzu. 

Klicke 7 mal auf das Pluszeichen **(+)** auf ``||Arrays:leeres Array||``. 

Die Gesamtlänge des Arrays sollte **7** sein.

## Schritt 4
Fülle alle Slots des Arrays mit  ``||Mobs:Tier||``-Blöcken.

## Schritt 5
Wähle 7 verschiedene Tiere aus. 

So kannst du einen Zoo mit **7** verschiedenen Arten von Tieren erstellen. Beachte, dass bestimmte Tiere andere Tiere fressen! Zum Beispiel verstehen sich Ozelote und Hühner nicht sehr gut. Überlege dir, welche Art von Zoo du möchtest, und plane Sie entsprechend. 

## Schritt 6
Lass uns ein Tiergehege bauen. 

Jetzt, da dein Tier-Array eingerichtet ist, arbeiten wir daran, ein eingezäuntes Gehege für deinen Zoo zu erstellen. Hierfür verwende die ``||Builder:BAUMEISTER||``-Blöcke. Der Baumeister ist wie ein unsichtbarer Cursor im Spiel, der sehr schnell Blöcke entlang eines Pfads platzieren kann. 

## Schritt 7
Ziehe einen ``||Player:Bei Chat-Befehl||``-Block in die Arbeitsfläche. Benenne den Befehl in "Stift" um.

Ziehe einen ``||Builder:Baumeister, teleportiere nach||``-Block in den ``||PLayer:Bei Chat-Befehl "Stift"||``-Block.

## Schritt 8
In ``||Builder:Baumeister, teleportiere nach||``, ändere die Positionswerte auf **(~5, ~0, ~-5)**.

## Schritt 9
Ziehe den Block ``||Builder:Baumeister, schaue nach||`` heraus und platziere es unter ``||Builder:Baumeister, teleportiere nach||``. Die Standardeinstellung "nach Westen schauen" ist in Ordnung.

## Schritt 10
Nehme einen ``||Builder:Baumeister, plaziere Markierung||``-Block und setze es nach dem ``||Builder:schaue nach||``-Block ein.

Zeichne die Umrisse des Stifts. Jetzt lasse den Baumeister einfach ein Quadrat zeichnen.

## Schritt 11
Ziehe eine ``||Loops:-mal wiederholen Schleife||`` und platziere sie nach dem ``||Builder:Baumeister, plaziere Markierung||``-Block. Ein Quadrat hat **vier** Seiten, also ist das Wiederholen **viermal** eine gute Idee.

## Schritt 12
Von ``||Builder:BAUMEISTER||``, ziehe ein ``||Builder:Baumeister, bewege dich||``-Block in die ``||Loops:4 -mal wiederholen||``-Schleife.

Gebe **10** in den ``||Builder:Baumeister, bewege dich vorwärts||``-Block ein, um die Seiten deines Stifts auf **10** Blöcke zu machen.

## Schritt 13
Ziehe einen ``||Builder:Baumeister, drehe dich nach||``-Block nach dem Block ``||Builder:Baumeister, bewege dich||``-Block.

## Schritt 14
Platziere einen ``||Builder:Baumeister, zeichne einen Weg von der Markierung mit||``-Block nach der ``||Loops:-mal wiederholen||``-Schleife. Wähle aus dem Dropdown-Menü einen Eichenzaun aus.

### ~ tutorialhint
``` blocks
player.onChat("pen", function () {
    builder.teleportTo(pos(5, 0, -5))
    builder.face(WEST)
    builder.mark()
    for (let index = 0; index < 4; index++) {
        builder.move(FORWARD, 10)
        builder.turn(LEFT_TURN)
    }
    builder.tracePath(OAK_FENCE)
})

```

## Schritt 15
"Teste den Befehl "Stift"."

## Schritt 16
Ziehe einen ``||Player:Bei Chat-Befehl||``-Block in den Programmierbereich und benenne es in „zoo“ um.

Ziehe einen ``||Loops:für Element||``-Block in den ``||Player:Bei Chat-Befehl "zoo"||``-Block.

## Schritt 17
Wähle im **2. Slot** des ``||Loops:für Element||``-Blocks **animalarray** aus.

## Schritt 18
Ziehe aus ``||Mobs:MOBS||`` einen ``||Mobs:spawne Tier bei||``-Block und platziere es in ``||Loops:für Element||``-Block.

## Schritt 19
Ziehe aus ``||Variables:VARIABLEN||`` die ``||Variables:Wert||``-Variable in den ``||Mobs:spawne Tier bei||``-Block. 
Es sollte jetzt **spawne Wert bei** heißen. 

Passen Sie die Koordinaten in ``||Mobs:spawn Wert bei||`` auf **(~3, ~0, ~0)** an, sodass die Tiere ein paar Blocks vom Spieler entfernt spawnen.

## Schritt 20
Um Tierpaare zu erstellen, klicke mit der rechten Maustaste auf den ``||Mobs:spawne Wert bei||``-Block, um ihn zu duplizieren. Wenn du möchtest, kannst du hier auch eine Schleife verwenden.

### ~ tutorialhint
``` blocks
player.onChat("zoo", function () {
    let animalarray: number[] = []
    for (let value of animalarray) {
        mobs.spawn(value, pos(3, 0, 0))
        mobs.spawn(value, pos(3, 0, 0))
    }
})
```

## Schritt 21 
Gebe den Befehl „zoo“ in das Chatfenster ein und beobachte, wie die Tiere erscheinen!

### ~ tutorialhint
``` blocks
let animalarray: number[] = []
player.onChat("pen", function () {
    builder.teleportTo(pos(5, 0, -5))
    builder.face(WEST)
    builder.mark()
    for (let i = 0; i < 4; i++) {
        builder.move(FORWARD, 10)
        builder.turn(TurnDirection.Left)
    }
    builder.tracePath(OAK_FENCE)
})
player.onChat("zoo", function () {
    for (let value of animalarray) {
        mobs.spawn(value, pos(3, 0, 0))
        mobs.spawn(value, pos(3, 0, 0))
    }
})
animalarray = [PIG, RABBIT, OCELOT,HORSE, DONKEY, MULE, LLAMA, POLAR_BEAR]
```


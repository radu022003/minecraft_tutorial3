
### @explicitHints 1

# Aktivität: Wir bauen einen Zoo

## 1. Variable erstellen
Erstelle eine neue Variable und nenne sie **animalarray**.

Ziehe den ``||VARIABLES:setze animalarray auf||``-Block in den ``||LOOPS:beim Start||``-Block.

## 2. Variable setzen
Ziehe einen ``||ARRAYS:leeres Array||``-Block in den ``||VARIABLES:setze animalarray auf||``-Block.

## 3. Array aufbauen
Füge Tiere zum Array hinzu. 

Klicke 7 mal auf das Pluszeichen **(+)** auf ``||ARRAYS:leeres Array||``. 

Die Gesamtlänge des Arrays sollte **7** sein.

## 4. Array aufbauen
Fülle alle Slots des Arrays mit  ``||MOBS:Tier||``-Blöcken.

## 5. Auswahl treffen
Wähle 7 verschiedene Tiere aus. 

So kannst du einen Zoo mit **7** verschiedenen Arten von Tieren erstellen. Beachte, dass bestimmte Tiere andere Tiere fressen! Zum Beispiel verstehen sich Ozelote und Hühner nicht sehr gut. Überlege dir, welche Art von Zoo du möchtest, und plane Sie entsprechend. 

## 6. Agent-Aktion einbauen
Lass uns ein Tiergehege bauen. 

Jetzt, da dein Tier-Array eingerichtet ist, arbeiten wir daran, ein eingezäuntes Gehege für deinen Zoo zu erstellen. Hierfür verwende die ``||BUILDER:BAUMEISTER||``-Blöcke. Der Baumeister ist wie ein unsichtbarer Cursor im Spiel, der sehr schnell Blöcke entlang eines Pfads platzieren kann. 

## 7. Chat-Befehl anlegen
Ziehe einen ``||PLAYER:Bei Chat-Befehl||``-Block in die Arbeitsfläche. Benenne den Befehl in "Stift" um.

Ziehe einen ``||BUILDER:Baumeister, teleportiere nach||``-Block in den ``||PLAYER:Bei Chat-Befehl "Stift"||``-Block.

## 8. Teleport einrichten
In ``||BUILDER:Baumeister, teleportiere nach||``, ändere die Positionswerte auf **(~5, ~0, ~-5)**.

## 9. Teleport einrichten
Ziehe den Block ``||BUILDER:Baumeister, schaue nach||`` heraus und platziere es unter ``||BUILDER:Baumeister, teleportiere nach||``. Die Standardeinstellung "nach Westen schauen" ist in Ordnung.

## 10. Variable konfigurieren
Nehme einen ``||BUILDER:Baumeister, plaziere Markierung||``-Block und setze es nach dem ``||BUILDER:schaue nach||``-Block ein.

Zeichne die Umrisse des Stifts. Jetzt lasse den Baumeister einfach ein Quadrat zeichnen.

## 11. Bedingung konfigurieren
Ziehe eine ``||LOOPS:-mal wiederholen Schleife||`` und platziere sie nach dem ``||BUILDER:Baumeister, plaziere Markierung||``-Block. Ein Quadrat hat **vier** Seiten, also ist das Wiederholen **viermal** eine gute Idee.

## 12. Bedingung konfigurieren
Von ``||BUILDER:BAUMEISTER||``, ziehe ein ``||BUILDER:Baumeister, bewege dich||``-Block in die ``||LOOPS:4 -mal wiederholen||``-Schleife.

Gebe **10** in den ``||BUILDER:Baumeister, bewege dich vorwärts||``-Block ein, um die Seiten deines Stifts auf **10** Blöcke zu machen.

## 13. Drehung einrichten
Ziehe einen ``||BUILDER:Baumeister, drehe dich nach||``-Block nach dem Block ``||BUILDER:Baumeister, bewege dich||``-Block.

## 14. Chat-Befehl erstellen
Platziere einen ``||BUILDER:Baumeister, zeichne einen Weg von der Markierung mit||``-Block nach der ``||LOOPS:-mal wiederholen||``-Schleife. Wähle aus dem Dropdown-Menü einen Eichenzaun aus.

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

## 15. Code testen
"Teste den Befehl "Stift"."

## 16. Chat-Befehl anlegen
Ziehe einen ``||PLAYER:Bei Chat-Befehl||``-Block in den Programmierbereich und benenne es in „zoo“ um.

Ziehe einen ``||LOOPS:für Element||``-Block in den ``||PLAYER:Bei Chat-Befehl "zoo"||``-Block.

## 17. Schleife konfigurieren
Wähle im **2. Slot** des ``||LOOPS:für Element||``-Blocks **animalarray** aus.

## 18. Spawn konfigurieren
Ziehe aus ``||MOBS:MOBS||`` einen ``||MOBS:spawne Tier bei||``-Block und platziere es in ``||LOOPS:für Element||``-Block.

## 19. Spawn konfigurieren
Ziehe aus ``||VARIABLES:VARIABLEN||`` die ``||VARIABLES:Wert||``-Variable in den ``||MOBS:spawne Tier bei||``-Block.
Es sollte jetzt **spawne Wert bei** heißen.

Passe die Koordinaten in ``||MOBS:spawn Wert bei||`` auf **(~3, ~0, ~0)** an, sodass die Tiere ein paar Blöcke vom Spieler entfernt spawnen.

## 20. Block duplizieren
Um Tierpaare zu erstellen, klicke mit der rechten Maustaste auf den ``||MOBS:spawne Wert bei||``-Block, um ihn zu duplizieren. Wenn du möchtest, kannst du hier auch eine Schleife verwenden.

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

## 21. Chat-Befehl erstellen
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


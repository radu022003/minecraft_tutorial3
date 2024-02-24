
### @explicitHints 1

# Aktivität: Wir bauen einen Zoo

## Schritt 1
Sie benötigen einen ``||Loops:beim Start||`` für das Projekt. Erstellen Sie eine neue Variable und nennen Sie sie **animalarray**.

Erstellen Sie ein Array für Tiere. Ziehen Sie den Block ``||Variables:setze||`` in den Block ``||Loops:beim Start||``.

## Schritt 2
Verwenden Sie das Dropdown-Menü in ``||Variables:setze||``, um die Variable **animalarray** auszuwählen.

Ziehen Sie einen Block ``||Arrays:erstelle Array mit||`` in den Block ``||Variables:setze "animalarray" nach||``.

## Schritt 3
Fügen Sie Tiere zum Array hinzu. Klicken Sie auf das Pluszeichen **(+)** auf ``||Arrays:erstelle Array mit||``, um 7 weitere Plätze in Ihrem Array hinzuzufügen. Die Gesamtlänge Ihres Arrays sollte **8** sein.

## Schritt 4
Ziehen Sie einen **Animal-Block** in den ersten Slot von ``||Arrays:erstelle Array mit||``.

Füllen Sie den Rest Ihres Arrays mit Tierblöcken. Sie können mit der rechten Maustaste auf ``||Mobs:Tier||`` klicken und **Duplizieren** auswählen, um Kopien dieses Blocks zu erstellen.

## Schritt 5
Wählen Sie Ihre Tiere aus. Erstellen Sie einen Zoo mit **8** verschiedenen Arten von Tieren. Beachten Sie, dass bestimmte Tiere andere Tiere fressen! Zum Beispiel verstehen sich Ozelote und Hühner nicht sehr gut. Überlegen Sie sich, welche Art von Zoo Sie möchten, und planen Sie entsprechend. Verwenden Sie die Dropdown-Menüs in den ``||Mobs:Tier||``-Blöcken, um verschiedene Arten von Tieren in Ihrem Array auszuwählen.

## Schritt 6
Lassen Sie uns ein Tiergehege bauen. Jetzt, da Ihr Tier-Array eingerichtet ist, arbeiten wir daran, ein eingezäuntes Gehege für Ihren Zoo zu erstellen. Hierfür verwenden Sie die ``||Builder:BAUMEISTER||``-Blöcke. Der Baumeister ist wie ein unsichtbarer Cursor im Spiel, der sehr schnell Blöcke entlang eines Pfads platzieren kann. Sie werden den Baumeister anweisen, zu einem Punkt in der südöstlichen Ecke zu gehen und eine Markierung zu setzen, die einen unsichtbaren Referenzpunkt darstellt. Dann geben Sie ihm eine Reihe von Befehlen, um ein Quadrat zu erstellen. Schließlich ist der Baumeister in der Lage, entlang dieses Pfads Zäune zu platzieren.

## Schritt 7
Ziehen Sie einen ``||Player:Bei Chat-Befehl||``-Block in die Arbeitsfläche. Benennen Sie den Befehl in "Stift" um.

Ziehen Sie einen ``||Builder:Baumeister, teleportiere nach||``-Block in den ``||PLayer:Bei Chat-Befehl "pen"||``-Block.

## Schritt 8
Finden Sie einen Platz für den Stift. Wir möchten, dass der Baumeister in der nordöstlichen Ecke des Geheges in Bezug auf den Spieler beginnt. Ändern Sie daher die Koordinaten so, dass sie eine Position **5** Blöcke östlich und **5** Blöcke nördlich Ihrer aktuellen Position angeben.

In ``||Builder:Baumeister, teleportiere nach||``, ändern Sie die Positionswerte auf **(~5, ~0, ~-5)**.

## Schritt 9
Setzen Sie die Startmarkierung. Stellen Sie sicher, dass der Baumeister in die richtige Richtung schaut, damit er den Stift um Sie herum zeichnet. Nachdem der Baumeister in die richtige Richtung schaut, können Sie ihn eine Startmarkierung platzieren lassen.

Ziehen Sie den Block ``||Builder:Baumeister, schaue nach||`` heraus und unter ``||Builder:Baumeister, teleportiere nach||``. Die Standardeinstellung "nach Westen schauen" ist in Ordnung.

## Schritt 10
Nehmen Sie einen ``||Builder:Baumeister, plaziere Markierung||``-Block und setzen Sie ihn nach dem ``||Builder:schaue nach||``-Block ein.

Zeichnen Sie die Umrisse des Stifts. Jetzt lassen Sie den Baumeister einfach ein Quadrat zeichnen.

## Schritt 11
Ziehen Sie eine ``||Loops:-mal wiederholen||`` Schleife und platzieren Sie sie nach dem ``||Builder:Baumeister, plaziere Markierung||``-Block. Ein Quadrat hat **vier** Seiten, also ist das Wiederholen **viermal** eine gute Idee.

## Schritt 12
Von ``||Builder:BAUMEISTER||``, ziehen Sie ein ``||Builder:Baumeister, bewege dich||``-Block in die ``||Loops:-mal wiederholen||``-Schleife.

Geben Sie **10** in den ``||Builder:Baumeister, bewege dich||``-Block ein, um die Seiten Ihres Stifts auf **10** Blöcke zu machen.

## Schritt 13
Ziehen Sie den Block ``||Builder:Baumeister, drehe dich nach||`` nach dem Block ``||Builder:Baumeister, bewege dich||``.

## Schritt 14
Errichten Sie Ihre Zäune. Der letzte Schritt besteht darin, den Baumeister Zäune entlang des von ihm nachgezeichneten Quadrats zu platzieren.

Platzieren Sie einen ``||Builder:Baumeister, zeichne einen Weg von der Markierung mit||``-Block nach der ``||Loops:-mal wiederholen||``-Schleife. Verwenden Sie das Dropdown-Menü in ``||Builder:Baumeister, zeichne einen Weg von der Markierung mit||``, um einen Eichenzaun auszuwählen.

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
"Versuche den Befehl "pen"." 

"Bereiten Sie sich darauf vor, die Tiere freizulassen. Jetzt kommt der Spaß. Das Array ist mit Tieren beladen, das Gehege wurde gebaut... es ist Zeit, sie loszulassen!"

## Schritt 16
Holen Sie sich einen ``||Player:Bei Chat-Befehl||`` und benennen Sie ihn in „zoo“ um.

Ziehen Sie ein ``||Loops:für Element||`` in Ihren ``||Player:Bei Chat-Befehl "zoo"||``.

## Schritt 17
Verwenden Sie im ``||Loops:für Element||`` das Dropdown-Menü für den **2. Slot**, um **animalarray** auszuwählen.

## Schritt 18
Lass sie gehen! Ziehen Sie aus ``||Mobs:MOBS||`` einen ``||Mobs:spawne Tier bei||``-Block und platzieren Sie ihn in ``||Loops:für Element||``.

## Schritt 19
Ziehen Sie aus ``||Variables:VARIABLES||`` die Wertvariable in den Block ``||Mobs:spawne Tier bei||`` und ersetzen Sie das Standard-Hühnertier.

Passen Sie die Koordinaten in ``||Mobs:spawn Tier bwi||`` auf **(~3, ~0, ~0)** an, sodass die Tiere ein paar Blocks vom Spieler entfernt spawnen.

## Schritt 20
Um Tierpaare zu erstellen, klicken Sie mit der rechten Maustaste auf den Block ``||Mobs:spawne Tier bei||``, um ihn zu duplizieren. Wenn Sie möchten, können Sie hier auch eine Schleife verwenden.

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
Versuchen Sie es mit dem Befehl „zoo“. Gehen Sie zurück in Ihre Minecraft-Welt, geben Sie den Befehl „zoo“ in das Chatfenster ein und beobachten Sie, wie die Tiere erscheinen!

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

### @explicitHints 1
# Aktivität: Herbst liegt in der Luft

## Schritt 1
Ziehen Sie einen ``||Player:bei Chat-Befehl||``-Block in die Arbeitsfläche.

## Schritt 2
Klicken Sie mit der rechten Maustaste auf den ``||Player:bei Chat-Befehl||`` und wählen Sie "Duplizieren". Wiederholen Sie dies zweimal, so dass Sie am Ende drei ``||Player:bei Chat-Befehl||``-Blöcke haben.

## Schritt 3
Benennen Sie diese Befehle in **"cr"** (Kreativ), **"su"** (Überleben) und **"pm"** (Postmortem) um.

## Schritt 4
Ziehen Sie zwei Ereignisblöcke heraus: ``||Player:bei gehen Spieler||`` und ``||Player:bei gestorbenem Spieler||``.

## Schritt 5
Ändern Sie ``||Player:bei gehen Spieler||`` in den Block ``||Player:bei fallen Spieler||``.

### ~ tutorialhint
``` blocks
    player.onChat("cr", function () {

    })
    player.onChat("su", function () {

    })
    player.onTravelled(TravelMethod.Walk, function () {

    })
    player.onChat("pm", function () {

    })
    player.onDied(function () {

    })
```

## Schritt 6
Seien Sie "Kreativ". Konstruieren Sie den ``||Player:bei Chat-Befehl||`` für **"cr"**. Dieser Befehl ändert den Spielmodus auf Kreativ. Sie können im Kreativmodus fliegen, daher ist dies sehr hilfreich, um an einen hohen Ort zu gelangen.
 
## Schritt 7
Ziehen Sie den ``||Gameplay:ändere Spielmodus zu||``-Block heraus und legen Sie ihn innerhalb des ``||Player:bei Chat-Befehl "cr"||``-Blocks ab.

## Schritt 8
In ``||Gameplay:ändere Spielmodus zu||``, wählen Sie den **Kreativ**-Modus und ändern Sie ``||Mobs:Ziel||`` auf sich selbst **@s**.

### ~ tutorialhint
``` blocks
player.onChat("cr", function () {
    gameplay.setGameMode(
    CREATIVE,
    mobs.target(LOCAL_PLAYER)
    )
})
```

## Schritt 9
Einfach überleben. Ziehen Sie den Block ``||Gameplay:ändere Spielmodus zu||`` heraus und legen Sie ihn innerhalb des Chat-Befehls "su" ab.

## Schritt 10
In ``||Gameplay:ändere Spielmodus zu||`` änderen Sie ``||Mobs:Ziel||`` als **du selbst @s**.

### ~ tutorialhint
``` blocks
player.onChat("su", function () {
    gameplay.setGameMode(
    SURVIVAL,
    mobs.target(LOCAL_PLAYER)
    )
})
```

## Schritt 11
In ``||Variables:VARIABLE||``, klicken Sie auf **Erstelle eine Variable**, und benennen Sie die neue Variable ``||Variable:fallen||``. Diese Variable wird jedes Mal, wenn der Spieler fällt, um einen Block inkrementiert )(hinzugefügt).

## Schritt 12
Erinnern die fallen. In ``||Variables:VARIABLES||``, klicken Sie auf **Erstelle eine Variable**, und benennen Sie die neue Variable ``||Variables:report||``.

## Schritt 13
Ziehen Sie den Block ``||Variables:ändere um||`` in das Ereignis ``||Player:bei Chat-Befehl fallen||``.

## Schritt 14
In ``||Variables:ändere um||``, wählen Sie Ihre Variable **fallen** anstelle des Standards, **item**.

## Schritt 15
Ziehen Sie ``||Variables:ändere um||`` heraus. Klicken Sie mit der rechten Maustaste darauf und wählen Sie Duplizieren. Jetzt sollten Sie zwei davon haben.

Legen Sie einen ``||Variables:ändere um||``-Block in den Block "bei gestorbem Spieler".

## Schritt 16
In diesem ``||Variables:ändere um||``-Block wählen Sie **report** anstelle von **item** aus.

## Schritt 17
Ziehen Sie **fallen** in den zweiten Slot und ersetzen Sie die **0**, damit der Block lautet **setze report auf fallen**.

## Schritt 18
Reset the fallen count. Move the other ``||Variable:setze auf||`` you duplicated in step 15. Put this inside ``||Player:bei Chat-Befehl gestorbenem||`` at the very bottom. Change the variable to **fallen**.
Setzen Sie den **fallen** Zähler zurück. Bewegen Sie das andere ``||Variable:setze auf||``, das Sie in Schritt 15 dupliziert haben. Platzieren Sie dies ganz unten innerhalb von ``||Player:bei Chat-Befehl gestorbenem||``. Ändern Sie die Variable auf **fallen**.

### ~ tutorialhint
``` blocks
let fallen = 0
let report = 0
player.onDied(function () {
    report = fallen
    fallen = 0
})
player.onTravelled(TravelMethod.fallen, function () {
    fallen += 1
})
```

## Schritt 19
Berichten Sie über Ihre **fallen** Anzahl. Ziehen Sie ``||Player:sag||`` in ``||Player:bei Chat-Befehl "pm"||``.

## Schritt 20
Klicken Sie auf **FORTGESCHRITTEN**, um die ``||Text:TEXT||``-Werkzeugkategorie anzuzeigen.

Ziehen Sie ``||Text:verbinde||`` in ``||PLayer:sag||`` und ersetzen Sie **"Hi!"**.

### ~ tutorialhint
``` blocks
let report = 0
player.onChat("pm", function () {
    player.say("Hallo" + "Welt")
})
```

## Schritt 21
Verbinden Sie die Variable mit der Nachricht. Geben Sie in ``||Text:verbinde||`` **"Du hast gefallen"** im ersten Slot ein, um *"Hallo"* zu ersetzen.

## Schritt 22
Ziehen Sie ``||Variables:report||`` in den zweiten ``||Text:verbinde||``-Slot und ersetzen Sie *"Welt"*.

### ~ tutorialhint
```blocks
let report = 0
player.onChat("pm", function () {
    player.say("You fell " + report)
})
```

### @explicitHints 1
# Aktivität: Freier Fall

## 1. Block duplizieren
Klicke mit der rechten Maustaste auf den ``||PLAYER:bei Chat-Befehl||``-Block und wähle "Duplizieren". Wiederhole dies zweimal, so dass du am Ende drei ``||PLAYER:bei Chat-Befehl||``-Blöcke hast.

## 2. Chat-Befehle umbenennen
Benenne diese Befehle in **"kr"** (Kreativ), **"üb"** (Überleben) und **"an"** (Anzahl) um.

## 3. Ereignis hinzufügen
Ziehe zwei Ereignisblöcke heraus: ``||PLAYER:bei gehen Spieler||`` und ``||PLAYER:bei gestorbenem Spieler||``.

## 4. Fall-Ereignis einstellen
Ändere ``||PLAYER:bei gehen Spieler||`` in den Block ``||PLAYER:bei fallen Spieler||``.

### ~ tutorialhint
``` blocks
    player.onChat("kr", function () {

    })
    player.onChat("üb", function () {

    })
    player.onTravelled(TravelMethod.Fall, function () {

    })
    player.onChat("an", function () {

    })
    player.onDied(function () {

    })
``` 
 
## 5. Spielmodus festlegen
Ziehe den ``||GAMEPLAY:ändere Spielmodus zu||``-Block in den ``||PLAYER:bei Chat-Befehl "kr"||``-Block hinein.

## 6. Spielmodus festlegen
In ``||GAMEPLAY:ändere Spielmodus zu||``-Block, wähle den **Kreativ**-Modus und ändere ``||MOBS:Ziel||`` auf dich selbst **@s**. So kannst du den Spielmodus auf Kreativ setzen.

### ~ tutorialhint
``` blocks
player.onChat("kr", function () {
    gameplay.setGameMode(
    CREATIVE,
    mobs.target(LOCAL_PLAYER)
    )
})
```

## 7. Spielmodus festlegen
Ziehe den ``||GAMEPLAY:ändere Spielmodus zu||``-Block in den ``||PLAYER:bei Chat-Befehl "üb"||``-Block.

## 8. Spielmodus festlegen
In ``||GAMEPLAY:ändere Spielmodus zu||``, wähle den **Überleben**-Modus und ändere ``||MOBS:Ziel||`` auf dich selbst **@s**. So kannst du den Spielmodus auf Überleben setzen.

### ~ tutorialhint
``` blocks
player.onChat("üb", function () {
    gameplay.setGameMode(
    SURVIVAL,
    mobs.target(LOCAL_PLAYER)
    )
})
```

## 9. Variable erstellen
In ``||VARIABLES:VARIABLEN||``, klicke auf **Erstelle eine Variable**, und benenne sie ``||VARIABLES:fallen||``.

## 10. Variable erstellen
In ``||VARIABLES:VARIABLEN||``, klicke auf **Erstelle eine Variable**, und benenne sie ``||VARIABLES:report||``.

## 11. Fallen mitzählen
Ziehe einen ``||VARIABLES:ändere um||``-Block in den ``||PLAYER:bei fallen Spieler||``-Block.

## 12. "fallen" auswählen
In ``||VARIABLES:ändere um||``-Block, wähle die Variable ``||VARIABLES:fallen||``. **"ändere fallen um 1"**

## 13. Variablen-Blöcke hinzufügen
Ziehe zwei ``||VARIABLES:setze auf||``-Blöcke in den ``||PLAYER:bei gestorbem Spieler||``-Block hinein.

## 14. Variable setzen
Im ersten ``||VARIABLES:setze auf||``-Block, wähle die Variable ``||VARIABLES:report||``. Dann füge in die Lücke, die ``||VARIABLES:fallen||``-Variable hinzu.

Es sollte jetzt **setze report auf fallen** heißen. 

## 15. Variable setzen
Im zweiten ``||VARIABLES:setze auf||``-Block, wähle die Variable ``||VARIABLES:fallen||``. 

Es sollte jetzt **setze fallen auf 0** heißen. 

### ~ tutorialhint
``` blocks
let fallen = 0
let report = 0
player.onDied(function () {
    report = fallen
    fallen = 0
})
player.onTravelled(TravelMethod.Fall, function () {
    fallen += 1
})
```

## 16. Nachrichtenblock hinzufügen
Ziehe ein ``||PLAYER:sag||``-Block in den ``||PLAYER:bei Chat-Befehl "an"||``-Block.

## 17. Text-Verbindung erstellen
Ziehe ein ``||TEXT:verbinde||``-Block in den ``||PLayer:sag||``-Block und klicke **einmal auf das "+"** bei ``||TEXT:verbinde||``-Block.

### ~ tutorialhint
``` blocks
let report = 0
player.onChat("an", function () {
    player.say("Hallo" + "Welt")
})
```

## 18. Text platzieren
Schreibe in die erste Lücke von ``||TEXT:verbinde||``-Block **"Du bist "** und in die dritte Lücke **" Blöcke gefallen"**.

## 19. Variable in Text einbinden
Ziehe die ``||VARIABLES:report||``-Variable in die zweite Lücke vom ``||TEXT:verbinde||``-Block.

### ~ tutorialhint
```blocks
let report = 0
player.onChat("an", function () {
    player.say("Du bist " + report + " Blöcke gefallen")
})
```
## 20. Code testen
Teste deinen Code aus


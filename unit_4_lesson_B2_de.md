### @explicitHints 1
# Aktivität: Herbst liegt in der Luft

## Schritt 1
Klicke mit der rechten Maustaste auf den ``||Player:bei Chat-Befehl||``-Block und wähle "Duplizieren". Wiederhole dies zweimal, so dass du am Ende drei ``||Player:bei Chat-Befehl||``-Blöcke hast.

## Schritt 2
Benenne diese Befehle in **"cr"** (Kreativ), **"su"** (Überleben) und **"an"** (Anzahl) um.

## Schritt 3
Ziehe zwei Ereignisblöcke heraus: ``||Player:bei gehen Spieler||`` und ``||Player:bei gestorbenem Spieler||``.

## Schritt 4
Ändere``||Player:bei gehen Spieler||`` in den Block ``||Player:bei fallen Spieler||``.

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
 
## Schritt 5
Ziehe den ``||Gameplay:ändere Spielmodus zu||``-Block in den ``||Player:bei Chat-Befehl "cr"||``-Block hinein.

## Schritt 6
In ``||Gameplay:ändere Spielmodus zu||``-Block, wähle den **Kreativ**-Modus und ändere ``||Mobs:Ziel||`` auf dich selbst **@s**. So kannst du den Spielmodus auf Kreativ setzen.

### ~ tutorialhint
``` blocks
player.onChat("cr", function () {
    gameplay.setGameMode(
    CREATIVE,
    mobs.target(LOCAL_PLAYER)
    )
})
```

## Schritt 7
Ziehe den ``||Gameplay:ändere Spielmodus zu||``-Block in den ``||Player:bei Chat-Befehl "su"||``-Block.

## Schritt 8
In ``||Gameplay:ändere Spielmodus zu||``, wähle den **Überleben**-Modus und ändere ``||Mobs:Ziel||`` auf dich selbst **@s**. So kannst du den Spielmodus auf Überleben setzen.

### ~ tutorialhint
``` blocks
player.onChat("su", function () {
    gameplay.setGameMode(
    SURVIVAL,
    mobs.target(LOCAL_PLAYER)
    )
})
```

## Schritt 9
In ``||Variables:VARIABLEN||``, klicke auf **Erstelle eine Variable**, und benennen Sie ``||Variables:fallen||``.

## Schritt 10
In ``||Variables:VARIABLEn||``, klicken auf **Erstelle eine Variable**, und benennen Sie ``||Variables:report||``.

## Schritt 11
Ziehe einen ``||Variables:ändere um||``-Block in den ``||Player:bei Chat-Befehl fallen||``-Block.

## Schritt 12
In ``||Variables:ändere um||``-Block, wähle die Variable ``||Variables:fallen||``. **"ändere fallen um 1"**

## Schritt 13
Ziehe zwei ``||Variables:setze auf||``-Blöcke in den ``||Player:bei gestorbem Spieler||``-Block hinein.

## Schritt 14
Im ersten ``||Variables:setze auf||``-Block, wähle die Variable ``||Variables:report||``. Dann füge in die Lücke, die ``||Variables:fallen||``-Variable hinzu.

Es sollte jetzt **setze report auf fallen** heißen. 

## Schritt 15
Im zweiten ``||Variables:setze auf||``-Block, wähle die Variable ``||Variables:fallen||``. 

Es sollte jetzt **setze fallen auf 0** heißen. 

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

## Schritt 16
Ziehe ein ``||Player:sag||``-Block in den ``||Player:bei Chat-Befehl "pm"||``-Block.

## Schritt 17
Ziehe ein ``||Text:verbinde||``-Block in den ``||PLayer:sag||``-Block und drücke auf das "+" bei ``||Text:verbinde||``-Block.

### ~ tutorialhint
``` blocks
let report = 0
player.onChat("pm", function () {
    player.say("Hallo" + "Welt")
})
```

## Schritt 18
Schreibe in die erste Lücke von ``||Text:verbinde||``-Block **"Du bist"** und die dei dritte Lücke **Blöcke gefallen**.

## Schritt 19
Ziehe die ``||Variables:report||``-Variable in die zweite Lücke vom ``||Text:verbinde||``-Block.

### ~ tutorialhint
```blocks
let report = 0
player.onChat("pm", function () {
    player.say("Du bist " + report + " Blöcke gefallen")
})
```
## Schritt 20
Teste deinen Code aus


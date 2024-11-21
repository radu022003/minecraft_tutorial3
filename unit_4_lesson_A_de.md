### @explicitHints 1
# Aktivität: Hühnerregen 

## Schritt 1
Ziehe einen ``||Player:bei Chat-Befehl||``-Block in den Programmierbereich und schreibe **"huehner"** rein. 

## Schritt 2
Füge eine ``||Loops:mache -mal wiederholen||``-Schleife innerhalb von ``||Player:Bei Chat-Befehl||`` "huehner" hinzu.

## Schritt 3
Füge einen ``||Mobs:spawne ___ bei||``-Block innerhalb der ``||Loops:mache -mal wiederholen||``-Schleife hinzu.

## Schritt 4
Innerhalb des ``||Mobs:spawne ___ bei||``-Blocks, ändere die **Y**-Koordinate auf **10** . 
So erscheinen Hühner 10 Blöcke über deinem Kopf.

### ~ tutorialhint
``` blocks
player.onChat("huehner", function () {
    for (let index = 0; index < 4; index++) {
        mobs.spawn(CHICKEN, pos(0, 10, 0))
    }
})
```
## Schritt 5: Variable hinzufügen
Drücke auf das "+" Symbol biem ``||Player:Bei Chat-Befehl huehner||``-Block. Dann füge in ``||Loops:mache -mal wiederholen||``-Schleife, die ``||Variables:num1||``-Variable hinzu.

## Schritt 6: Code testen
Gebe im Chat-Fenster "**huehner** 15" ein. Es regnet Hühner! Die Variable **num1** hat den Wert **15** angenommen.


### ~ tutorialhint
``` blocks
player.onChat("huehner", function (num1) {
    for (let i = 0; i < num1; i++) {
        mobs.spawn(CHICKEN, pos(0, 10, 0))
    }
})
```

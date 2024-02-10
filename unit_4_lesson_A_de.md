### @explicitHints 1
# Aktivität: Hühnersturm 

## Schritt 1
Ziehen Sie einen ``||Player:Bei Chat-Befehl||`` in den Programmierbereich und ändern Sie den Befehl in **"huehner"**.

## Schritt 2
Fügen Sie eine ``||Loops:mache -mal wiederholen||`` Schleife innerhalb von ``||Player:Bei Chat-Befehl||`` "huehner" hinzu.

## Schritt 3
Fügen Sie einen ``||Mobs:spawne bei||``-Block innerhalb der ``||Loops:mache -mal wiederholen||``-Schleife hinzu.

## Schritt 4
Ändern Sie die **Y**-Koordinate auf **10** innerhalb des ``||Mobs:spawne bei||``-Blocks. Hühner werden 10 Blöcke über Ihrem Kopf erscheinen.

### ~ tutorialhint
``` blocks
player.onChat("huehner", function () {
    for (let index = 0; index < 4; index++) {
        mobs.spawn(CHICKEN, pos(0, 10, 0))
    }
})
```

## Schritt 5
Gehen Sie in Minecraft, drücken Sie **T**, um das Chat-Fenster zu öffnen, und geben Sie **huehner** im Chat-Fenster ein. Es regnet Hühner! Wenn Sie nun **huehner 15** im Chat-Fenster eingeben, wird die Variable **num1** den Wert **15** annehmen.

## Schritt 6
Drücken Sie auf den **Plus** von ``||Player:Bei Chat-Befehl||`` um die neue Variable zu erstellen.
Mehr Hühner! Ersetzen Sie die Zahl **4** in ``||Loops:mache -mal wiederholen||`` durch ``||Variables:num1||`` aus ``||Variables:VARIABLE||``.

### ~ tutorialhint
``` blocks
player.onChat("huehner", function (num1) {
    for (let i = 0; i < num1; i++) {
        mobs.spawn(CHICKEN, pos(0, 10, 0))
    }
})
```

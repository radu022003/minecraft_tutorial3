### @explicitHints 1
# Aktivität: Hühnerregen

## 1. Chat-Befehl anlegen
Ziehe einen ``||PLAYER:bei Chat-Befehl||``-Block in den Programmierbereich und schreibe **"hühner"** hinein.

## 2. Schleife hinzufügen
Füge eine ``||LOOPS:_-mal wiederholen||``-Schleife in den ``||PLAYER:Bei Chat-Befehl||``-Block **hühner** ein.

## 3. Spawn konfigurieren
Füge einen ``||MOBS:spawne ___ bei||``-Block in die ``||LOOPS:mache _-mal wiederholen||``-Schleife ein.

## 4. Koordinaten setzen
Ändere im ``||MOBS:spawne ___ bei||``-Block die **Y**-Koordinate auf **10**.
So erscheinen Hühner 10 Blöcke über deinem Kopf.

### ~ tutorialhint
``` blocks
player.onChat("hühner", function () {
    for (let index = 0; index < 4; index++) {
        mobs.spawn(CHICKEN, pos(0, 10, 0))
    }
})
```

## 5. Parameter hinzufügen
Drücke auf das "+"-Symbol beim ``||PLAYER:Bei Chat-Befehl hühner||``-Block.
Füge dann in der ``||LOOPS:mache _-mal wiederholen||``-Schleife die ``||VARIABLES:num1||``-Variable hinzu.

## 6. Code testen
Gib im Chat-Fenster "**hühner** 15" ein. Es regnet Hühner!
Die Variable **num1** hat dabei den Wert **15**.

### ~ tutorialhint
``` blocks
player.onChat("hühner", function (num1) {
    for (let i = 0; i < num1; i++) {
        mobs.spawn(CHICKEN, pos(0, 10, 0))
    }
})
```

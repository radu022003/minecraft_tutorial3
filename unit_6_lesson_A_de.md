### @explicitHints 1

# Aktivität: Sprung ins Wasser Minispiel

## 1. Pool-Funktion erstellen
Klicke im Werkzeugkasten auf den Reiter "Fortgeschritten", um weitere Kategorien anzuzeigen.
Erstelle eine ``||FUNCTIONS:Funktion||`` mit dem Namen **pool**. 

## 2. Zusatzfunktionen erstellen
Erstelle zwei weitere ``||FUNCTIONS:Funktionen||`` mit den Namen **plattform** und **teleport**.

## 3. Chat-Befehl anlegen
Ziehe eine ``||PLAYER:Bei Chat-Befehl||``-Block in die Arbeitsfläche. Benenne dies in **"play"** um.

## 4. Funktionsaufrufe verbinden
Ziehe die drei Blöcke ``||FUNCTIONS:Aufruf pool||``, ``||FUNCTIONS:Aufruf platform||`` und ``||FUNCTIONS:Aufruf teleport||`` in den ``||PLAYER:bei Chat-Befehl "play"||``-Block.

### ~ tutorialhint
``` blocks
pool()
platform()
teleport()
function pool(){}
function platform(){}
function teleport(){}
```

## 5. Fläche bauen
Ziehe einen ``||BLOCKS:Fülle mit||``-Block in den ``||FUNCTIONS:function pool||``.

## 6. Fläche bauen
Im Dropdown-Menü von ``||BLOCKS:Fülle mit||``-Block, wähle einen **Wasserblock**.

Im ``||BLOCKS:Fülle mit||``-Block, gebe die folgenden Werte für die Koordinaten ein: **(0, -1, 0)** und **(2, -3, 2)**.

### ~ tutorialhint
``` blocks
function pool() {
    blocks.fill(
    WATER,
    pos(0, -1, 0),
    pos(2, -3, 2),
    FillOperation.Replace
    )
}
pool()
```

## 7. Fläche bauen
Ziehe einen weiteren ``||BLOCKS:Fülle mit||``-Block in ``||FUNCTIONS:function platform||``. Im Dropdown-Menü von ``||BLOCKS:Fülle mit||``-Block, wähle eine **Doppelte Holzstufe**. 

Im ``||BLOCKS:Fülle mit||``-Block, gebe die folgenden Werte für die Koordinaten ein: **(1, 64, 1)** und **(3, 64, 3)**.



### ~ tutorialhint
``` blocks
function platform() {
    blocks.fill(
    DOUBLE_WOODEN_SLAB,
    pos(1, 64, 1),
    pos(3, 64, 3),
    FillOperation.Replace
    )
}
platform()
```

## 8. Teleport einrichten
Der letzte Schritt besteht darin, den Spieler an einen Ort knapp über der Mitte der Plattform zu teleportieren. 

Ziehe einen ``||PLAYER:teleportiere nach||`` Block in ``||FUNCTIONS:function teleport||``.

## 9. Koordinaten setzen
Im ``||PLAYER:teleportiere nach||``-Block gebe die folgenden Werte für die Koordinaten ein: **(2, 65, 2)**.

## 10. Spielmodus festlegen
Setze den Spielmodus auf Überleben. 

Ziehe dazu einen ``||GAMEPLAY:ändere Spielmodus zu||``-Block in die ``||FUNCTIONS:Funktion teleport||``.


### ~ tutorialhint
``` blocks

function teleport() {
    player.teleport(pos(2, 65, 2))
    gameplay.setGameMode(
        SURVIVAL,
        mobs.target(LOCAL_PLAYER)
    )
}
teleport()

```

## 11. Code testen
Teste jetzt dein Minispiel, indem du play in den Chat eingibst. 

### ~ tutorialhint
``` blocks

function pool() {
    blocks.fill(
    WATER,
    pos(0, -1, 0),
    pos(2, -3, 2),
    FillOperation.Replace
    )
}
function teleport() {
    player.teleport(pos(2, 65, 2))
    gameplay.setGameMode(
    SURVIVAL,
    mobs.target(LOCAL_PLAYER)
    )
}
function platform() {
    blocks.fill(
    DOUBLE_WOODEN_SLAB,
    pos(1, 64, 1),
    pos(3, 64, 3),
    FillOperation.Replace
    )
}
player.onChat("play", function () {
pool()
platform()
teleport()
})
```

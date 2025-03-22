### @explicitHints 1

# Aktivität: Sprung des Glaubens Minispiel

## Schritt 1
Klicke im Werkzeugkasten auf den Reiter "Erweitert", um weitere Kategorien anzuzeigen.
Erstelle eine ``||Functions:Funktion||`` mit dem Namen **pool**. 

## Schritt 2
Erstelle zwei weitere ``||Functions:Funktionen||`` mit den Namen **plattform** und **teleport**.

## Schritt 3
Ziehe eine ``||Player:Bei Chat-Befehl||``-Block in die Arbeitsfläche. Benenne dies in **"play"** um.

## Schritt 4
Ziehe die drei Blöcke ``||Functions:Aufruf pool||``, ``||Functions:Aufruf platform||`` und ``||Functions:Aufruf teleport||`` in den ``||Player:bei Chat-Befehl "play"||``-Block.

### ~ tutorialhint
``` blocks
pool()
platform()
teleport()
function pool(){}
function platform(){}
function teleport(){}
```

## Schritt 5: Pool erstellen
Ziehe einen ``||Blocks:Fülle mit||``-Block in den ``||Functions:function pool||``.

## Schritt 6
Im Dropdown-Menü von ``||Blocks:Fülle mit||``-Block, wähle einen **Wasserblock**.

Im ``||Blocks:Fülle mit||``-Block, gebe die folgenden Werte für die Koordinaten ein: **(0, -1, 0)** und **(2, -3, 2)**.

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

## Schritt 7: Plattform bauen 
Ziehe einen weiteren ``||Blocks:Fülle mit||``-Block in ``||Functions:function platform||``. Im Dropdown-Menü von ``||Blocks:Fülle mit||``-Block, wähle eine **Doppelte Holzstufe**. 

Im ``||Blocks:Fühle mit||``-Block, gebe die folgenden Werte für die Koordinaten ein: **(1, 64, 1)** und **(3, 64, 3)**.



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

## Schritt 8
Der letzte Schritt besteht darin, den Spieler an einen Ort knapp über der Mitte der Plattform zu teleportieren. 

Ziehe einen ``||Player:teleportiere nach||`` Block in ``||Functions:function teleport||``.

## Schritt 9
Im ``||Player:teleportiere nach||``-Block gebe die folgenden Werte für die Koordinaten ein: **(2, 65, 2)**.

## Schritt 10
Setze den Spielmodus auf Überleben. 

Ziehe dazu einen ``||Player:teleportiere nach||``-Block in ``||Functions:function teleport||``.


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

## Schritt 13
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

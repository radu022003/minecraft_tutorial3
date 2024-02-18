### @explicitHints 1

# Aktivität: Sprung des Glaubens Minispiel

## Schritt 1
Klicken Sie auf die Registerkarte **FORTGESCHRITTEN** in der Werkzeugleiste, um weitere Kategorien anzuzeigen

In der ``||Functions:FUNKTIONEN||`` Toolbox-Schublade klicken Sie auf die Schaltfläche **Erstelle eine Funktion**. Benennen Sie die Funktion **pool**, und klicken Sie auf **Fertig**.

## Schritt 2
"Erstellen Sie die Funktionen platform() und teleport(). Wiederholen Sie den vorherigen Schritt, um zwei weitere Funktionen mit den Namen **platform** und **teleport** zu erstellen."

## Schritt 3

Ziehen Sie ``||Player:Bei Chat-Befehl||`` auf die Arbeitsfläche. Benennen Sie dies um zu **"play"**.

## Schritt 4
"Ziehen Sie die drei Blöcke ``||Functions:aufruf function pool||``, ``||Functions:aufruf function platform||`` und ``||Functions:aufruf function teleport||`` in ``||Loops:beim start||``."

### ~ tutorialhint
``` blocks
pool()
platform()
teleport()
function pool(){}
function platform(){}
function teleport(){}
```

## Schritt 5
Der ``||Loops:beim start||``-Block wird ausgeführt, wenn das Programm startet. Dies kann manchmal lästig sein, wenn Sie Code testen oder das Programm neu starten möchten. Verwenden Sie die Schaltflächen in der unteren linken Ecke, um Ihren Code in diesen Fällen neu zu starten. Klicken Sie auf die Stopp-Schaltfläche in der unteren linken Ecke Ihres Code-Verbindungsfensters.

## Schritt 6
Füllen Sie den Pool. Ziehen Sie den ``||Blocks:Fühle mit||`` Block in den ``||Functions:pool||``. Der ``||Blocks:Fühle mit||`` Block füllt eine dreidimensionale Box von den ersten Koordinaten bis zu den zweiten Koordinaten.

## Schritt 7
Verwenden Sie das Dropdown-Menü in ``||Blocks:Fühle mit||``, um einen Wasserblock auszuwählen.

In ``||Blocks:Fühle mit||``, geben Sie die folgenden Werte für die ersten Koordinaten ein: **(0, -1, 0)** und **(2, -3, 2)** als die zweiten Koordinaten.

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

## Schritt 8
Bauen Sie eine Plattform. Ziehen Sie einen weiteren ``||Blocks:Fühle mit||`` Block in ``||Functions:platform||``. Verwenden Sie das Dropdown-Menü in ``||Blocks:Fühle mit||``, um eine **Doppelte Holzstufe** auszuwählen.

## Schritt 9
Im ``||Blocks:Fühle mit||`` Block geben Sie die folgenden Werte für die ersten Koordinaten ein: **(1, 64, 1)**.

Geben Sie die folgenden Werte für die zweiten Koordinaten ein: **(3, 64, 3)**.

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

## Schritt 10
Teleportieren Sie sich selbst. Der letzte Schritt besteht darin, den Spieler an einen Ort knapp über der Mitte der Plattform zu teleportieren. Ziehen Sie einen ``||Player:teleportiere nach||`` Block in ``||Functions:teleport||``.

## Schritt 11
Im ``||Player:teleportiere nach||`` Block geben Sie die folgenden Werte für die Koordinaten ein: **(2, 65, 2)**.

## Schritt 12
Setzen Sie den Spielmodus auf Überleben, indem Sie zu ``||Gameplay:SPIELMECHANIK||`` gehen und einen ``||Gameplay:ändere Spielmodus zu||`` Block herausziehen. Probieren Sie Ihr Minispiel aus!

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
Finden Sie eine Stelle mit offenem Boden. Denken Sie daran, dass Ihr Spiel praktisch startet, sobald die ``||Loops:beim start||`` Schleife ausgeführt wird. Möglicherweise müssen Sie also den Code starten und stoppen, um ihn zurückzusetzen. Dann machen Sie einen Sprung des Glaubens! Denken Sie daran, dass Sie, wenn Sie auf der Plattform sind, die Umschalttaste gedrückt halten können, während Sie sich bewegen, um nicht herunterzufallen, während Sie nach einem guten Sprungplatz suchen.

Klicken Sie auf die Stopp-Schaltfläche in der unteren linken Ecke Ihres Code-Verbindungsfensters.

## Schritt 14
Starten Sie die Codierumgebung neu. Klicken Sie auf die Wiedergabe-Schaltfläche. Wenn die Wiedergabe-Schaltfläche nicht aktiviert ist, wird Ihr Code nicht in Minecraft ausgeführt.

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
pool()
platform()
teleport()
```

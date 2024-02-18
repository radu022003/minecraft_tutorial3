### @explicitHints 1
# Aktivität: Burger 

## Schritt 1
Um eine Funktion zu erstellen, klicken Sie in der ``||Functions:FUNKTIONEN||`` Werkzeugleisten-Schublade auf die Schaltfläche **Erstelle eine Funktion**.

Benennen Sie die Funktion. Benennen Sie diese Funktion *unteresBrotchen()*, und klicken Sie auf **Fertig**.

## Schritt 2
Erstellen Sie die Funktionen fleisch(), salat(), tomate() und oberesBrotchen(). Wiederholen Sie den vorherigen Schritt, um zwei weitere Funktionen mit den Namen **Fleisch**, **Salat** und **Tomate** sowie **oberesBrotchen** zu erstellen.

## Schritt 3
Ziehen Sie einen ``||Player:Bei Chat-Befehl||`` Block auf die Arbeitsfläche.

Benennen Sie ``||Player:Bei Chat-Befehl||``um zu **"burger"**.

## Schritt 4
Ziehen Sie fünf Blöcke ``||Functions:aufruf Funktion unteresBrotchen||``, ``||Functions:aufruf Funktion fleisch||``, ``||Functions:aufruf Funktion salat||``, ``||Functions:aufruf Funktion tomate||`` und ``||Functions:aufruf Funktion oberesBrotchen||`` in ``||Player:Bei Chat-Befehl "burger"||``.

**HINWEIS**: Die Reihenfolge dieser Funktionsaufrufe ist wichtig.

### ~ tutorialhint
```blocks
function salat()  {

}
function unteresBrotchen()  {

}
function oberesBrotchen()  {

}
player.onChat("burger", function () {
    unteresBrotchen()
    fleisch()
    salat()
    tomate()
    oberesBrotchen()
})
function fleisch()  {

}
function tomate()  {

}
```

## Schritt 5
Erstellen Sie das untere Brötchen. Das erste, was Sie tun werden, ist, das untere Brötchen zu erstellen.

Ziehen Sie einen ``||Blocks:Fühle mit||`` Block in ``||Functions:unteresBrotchen||``. Ändern Sie den Block, indem Sie **Eichenholzbretter** aus dem Dropdown-Menü auswählen.

## Schritt 6
Geben Sie die Koordinaten für das obere Brötchen mit einer Startposition von **(~3, ~0, ~3)** und einer Endposition von **(~8, ~0, ~8)** ein.

### ~ tutorialhint
```blocks
function unteresBrotchen() {
    blocks.fill(
    PLANKS_OAK,
    pos(3, 0, 3),
    pos(8, 0, 8),
    FillOperation.Replace
    )
}
function salat() {
}
player.onChat("burger", function () {
    unteresBrotchen()
    fleisch()
    salat()
    tomate()
    oberesBrotchen()
})
function oberesBrotchen() {

}
function fleisch() {

}
function tomate() {

}
```

## Schritt 7
"Bereiten" Sie das Fleisch zu. Lassen Sie uns eine Schicht Fleisch erstellen. Ziehen Sie einen ``||Blocks:Fühle mit||`` Block in ``||Functions:Fleisch||``. 

Passen Sie das Material an, indem Sie **Braune Terrakotta** aus dem Dropdown-Menü auswählen. Ändern Sie dann die Position im Koordinatenbereich zu einer Startposition von **(~4, ~1, ~4)** und einer Endposition von **(~7, ~1, ~7)**.

Duplizieren Sie es.

### ~ tutorialhint
```blocks
function unteresBrotchen() {
    blocks.fill(
    PLANKS_OAK,
    pos(3, 0, 3),
    pos(8, 0, 8),
    FillOperation.Replace
    )
}
function salat() {

}
player.onChat("burger", function () {
    unteresBrotchen()
    fleisch()
    salat()
    tomate()
    oberesBrotchen()
})
function oberesBrotchen() {

}
function fleisch() {
    blocks.fill(
    BROWN_TERRACOTTA,
    pos(4, 1, 4),
    pos(7, 1, 7),
    FillOperation.Replace
    )
}
function tomate() {

}
```
## Schritt 8
Create the lettuce. Let's create a layer of lettuce. Drag a ``||Blocks:fühle mit||`` into the ``||Functions:lettuce||`` function.

Change the material selecting **Lime Concrete** from the drop-down menu. Then change the position in the coordinates to a starting position of **(~4, ~2, ~4)** and a finishing position of **(~7, ~2, ~7)**.

### ~ tutorialhint
```blocks
function unteresBrotchen() {
    blocks.fill(
    PLANKS_OAK,
    pos(3, 0, 3),
    pos(8, 0, 8),
    FillOperation.Replace
    )
}
function salat() {
     blocks.fill(
    LIME_CONCRETE,
    pos(4, 2, 4),
    pos(7, 2, 7),
    FillOperation.Replace
    )
}
player.onChat("burger", function () {
    unteresBrotchen()
    fleisch()
    salat()
    tomate()
    oberesBrotchen()
})
function oberesBrotchen() {

}
function fleisch() {
    blocks.fill(
    BROWN_TERRACOTTA,
    pos(4, 1, 4),
    pos(7, 1, 7),
    FillOperation.Replace
    )
}
function tomate() {

}
```

## Schritt 9
Erstellen Sie die Tomate. Erstellen wir eine Schicht Tomate. Ziehen Sie einen ``||Blocks:Fühle mit||`` Block in die ``||Functions:tomato||`` Funktion.

Ändern Sie das Material, indem Sie **Roter Beton** aus dem Dropdown-Menü auswählen. Ändern Sie dann die Position im Koordinatenbereich zu einer Startposition von **(~4, ~3, ~4)** und einer Endposition von **(~7, ~3, ~7)**.

### ~ tutorialhint
```blocks
function tomate() {
    blocks.fill(
    RED_CONCRETE,
    pos(4, 3, 4),
    pos(7, 3, 7),
    FillOperation.Replace
    )
}
tomate()
```

## Schritt 10
Erstellen Sie das obere Brötchen. Die letzte Funktion ist das **obere Brötchen**. Um dem Burger ein realistischeres Aussehen zu geben, füllt diese Funktion zwei Schichten anstelle von nur einer. Ziehen Sie zwei ``||Blocks:Fühle mit||`` Blöcke in die ``||Functions:oberesBrotchen||`` Funktion.

Ändern Sie das Material für jede Füllung auf **Eichenholzbretter**.

## Schritt 11
Ändern Sie zuerst die Koordinaten für die obere Füllung. Die Position für die Koordinaten sollte eine Startposition von **(~3, ~4, ~3)** und eine Endposition von **(~8, ~4, ~8)** haben.

## Schritt 12
Die untere Füllung sollte eine Startposition von **(~4, ~5, ~4)** und eine Endposition von **(~7, ~5, ~7)** haben.

### ~ tutorialhint
``` blocks
function oberesBrotchen() {
    blocks.fill(
    PLANKS_OAK,
    pos(3, 4, 3),
    pos(8, 4, 8),
    FillOperation.Replace
    )
    blocks.fill(
    PLANKS_OAK,
    pos(4, 5, 4),
    pos(7, 5, 7),
    FillOperation.Replace
    )
}
oberesBrotchen()
```

## Schritt 13

Vervollständigen Sie das Programm!

### ~ tutorialhint
```blocks
function fleisch() {
    blocks.fill(
    BROWN_TERRACOTTA,
    pos(4, 1, 4),
    pos(7, 1, 7),
    FillOperation.Replace
    )
}
player.onChat("burger", function () {
    unteresBrotchen()
    fleisch()
    salat()
    tomate()
    oberesBrotchen()
})
function oberesBrotchen() {
    blocks.fill(
    PLANKS_OAK,
    pos(3, 4, 3),
    pos(8, 4, 8),
    FillOperation.Replace
    )
    blocks.fill(
    PLANKS_OAK,
    pos(4, 5, 4),
    pos(7, 5, 7),
    FillOperation.Replace
    )
}
function tomate() {
    blocks.fill(
    RED_CONCRETE,
    pos(4, 3, 4),
    pos(7, 3, 7),
    FillOperation.Replace
    )
}
function unteresBrotchen() {
    blocks.fill(
    PLANKS_OAK,
    pos(3, 0, 3),
    pos(8, 0, 8),
    FillOperation.Replace
    )
}
function salat() {
    blocks.fill(
    LIME_CONCRETE,
    pos(4, 2, 4),
    pos(7, 2, 7),
    FillOperation.Replace
    )
}
```

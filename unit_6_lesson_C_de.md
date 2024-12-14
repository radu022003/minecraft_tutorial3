### @explicitHints 1
# Aktivität: Burger 

## Schritt 1: Buregerzutaten
Erstelle fünf Funktionen mit den Namen **unteresBrotchen**, **Fleisch**, **Salat**, **Tomate** und **oberesBrotchen**.

## Schritt 2
Ziehe einen ``||Player:Bei Chat-Befehl||``-Block auf die Arbeitsfläche und benenne es **"burger"**.

## Schritt 3
Füge die folgenden Blöcke in den ``||Player:Bei Chat-Befehl "burger"||``-Block hinzu:

 ``||Functions:aufruf unteresBrotchen||``, 

 ``||Functions:aufruf fleisch||``, 

 ``||Functions:aufruf salat||``, 

 ``||Functions:aufruf tomate||`` und 

 ``||Functions:aufruf oberesBrotchen||``

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

## Schritt 4: unteresBrotchen
Ziehen Sie einen ``||Blocks:Fülle mit||`` Block in ``||Functions:function unteresBrotchen||``. 

Ändere den Block, indem du **Eichenholzbretter** aus dem Dropdown-Menü auswählst.

Gebe folgende Koordinaten ein: von **(~3, ~0, ~3)** nach **(~8, ~0, ~8)** 

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

## Schritt 5: Fleisch
Ziehe einen ``||Blocks:Fülle mit||``-Block in ``||Functions:function Fleisch||``. 

Ändere den Block, indem du **Braune Terrakotta** aus dem Dropdown-Menü auswählst.

Gebe folgende Koordinaten ein: von **(~4, ~1, ~4)** nach **(~7, ~1, ~7)**.


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
## Schritt 6: Salat
Ziehe einen ``||Blocks:Fülle mit||``-Block in ``||Functions:function Salat||``. 

Ändere den Block, indem du **Lime Concrete** aus dem Dropdown-Menü auswählst.

Gebe folgende Koordinaten ein: von **(~4, ~2, ~4)** nach **(~7, ~2, ~7)**.

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

## Schritt 7: Tomate 
Ziehe einen ``||Blocks:Fülle mit||``-Block in ``||Functions:function Tomate||``. 

Ändere den Block, indem du **Roter Beton** aus dem Dropdown-Menü auswählst.

Gebe folgende Koordinaten ein: von **(~4, ~3, ~4)** nach **(~7, ~3, ~7)**.

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

## Schritt 8: oberesBrotchen
Ziehe zwei ``||Blocks:Fülle mit||``-Blöcke in ``||Functions:function oberesBrotchen||``. 

Ändere den Block, indem du **Eichenholzbretter** aus dem Dropdown-Menü auswählst.

## Schritt 9
Gebe folgende Koordinaten für den ersten ``||Blocks:Fülle mit||``-Block: von **(~3, ~4, ~3)** nach **(~8, ~4, ~8)**.

## Schritt 10
Gebe folgende Koordinaten für den zweiten ``||Blocks:Fülle mit||``-Block: von **(~4, ~5, ~4)** nach **(~7, ~5, ~7)**.

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

## Schritt 11

Teste deinen Code, indem du **Burger** im Chat eingibst.

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

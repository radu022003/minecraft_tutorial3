### @explicitHints 1
# Aktivität: Riesenburger bauen

## 1. Burger-Schicht-Funktionen erstellen
Erstelle fünf Funktionen mit den Namen **unteresBrotchen**, **Fleisch**, **Salat**, **Tomate** und **oberesBrotchen**.

## 2. Burger-Chat-Befehl erstellen
Ziehe einen ``||PLAYER:Bei Chat-Befehl||``-Block auf die Arbeitsfläche und benenne ihn **"burger"**.

## 3. Funktionsaufrufe in Reihenfolge
Füge die folgenden Blöcke in den ``||PLAYER:Bei Chat-Befehl "burger"||``-Block hinzu:

 ``||FUNCTIONS:aufruf unteresBrotchen||``, 

 ``||FUNCTIONS:aufruf fleisch||``, 

 ``||FUNCTIONS:aufruf salat||``, 

 ``||FUNCTIONS:aufruf tomate||`` und 

 ``||FUNCTIONS:aufruf oberesBrotchen||``

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

## 4. Fläche bauen
Ziehe einen ``||BLOCKS:Fülle mit||``-Block in ``||FUNCTIONS:function unteresBrotchen||``.

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

## 5. Fläche bauen
Ziehe einen ``||BLOCKS:Fülle mit||``-Block in ``||FUNCTIONS:function Fleisch||``. 

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
## 6. Fläche bauen
Ziehe einen ``||BLOCKS:Fülle mit||``-Block in ``||FUNCTIONS:function Salat||``. 

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

## 7. Fläche bauen
Ziehe einen ``||BLOCKS:Fülle mit||``-Block in ``||FUNCTIONS:function Tomate||``. 

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

## 8. Fläche bauen
Ziehe zwei ``||BLOCKS:Fülle mit||``-Blöcke in ``||FUNCTIONS:function oberesBrotchen||``. 

Ändere den Block, indem du **Eichenholzbretter** aus dem Dropdown-Menü auswählst.

## 9. Koordinaten setzen
Gebe folgende Koordinaten für den ersten ``||BLOCKS:Fülle mit||``-Block: von **(~3, ~4, ~3)** nach **(~8, ~4, ~8)**.

## 10. Koordinaten setzen
Gebe folgende Koordinaten für den zweiten ``||BLOCKS:Fülle mit||``-Block: von **(~4, ~5, ~4)** nach **(~7, ~5, ~7)**.

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

## 11. Code testen

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

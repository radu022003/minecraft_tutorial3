### @explicitHints 1
# Aktivität: Pfeilzähler

## Schritt 1
Erstelle eine neue ``||Variables:Variable||`` und nenne es **pfeil**.

## Schritt 2
Ziehe den ``||Player:bei Pfeilschuss||``-Block in den Arbeitsbereich.

## Schritt 3
Ziehe die ``||Variables:ändere um||``-Variable in den ``||Player:bei Pfeilschuss||``-Block hinein.

## Schritt 4
In ``||Variables:ändere um||``, wähle dei Variable ``||Variables:pfeil||``. Die Variable sollte jetzt ``||Variables:ändere pfeil um||`` heißen.

## Schritt 5
Ziehe den ``||Player:sag||``-Block in den ``||Player:bei Pfeilschuss||``-Block hinein. Ziehe danach den ``||Text:verbinde||``-Block in den ``||Player:sag||``-Block hinein. 

### ~ tutorialhint
 ``` blocks
 let arrows = 0
player.onArrowShot(function () {
    arrows += 1
    player.say("Hello" + "World")
})
```

## Schritt 6
Ziehe die ``||Variables:pfeil||``-Variable in den ersten Slot von ``||Text:verbinde||``.

## Schritt 7
Gebe im zweiten Feld von ``||Text:verbinde||`` **"Pfeile abgeschossen"** ein. 

### ~ tutorialhint
``` blocks
let arrows = 0
player.onArrowShot(function () {
    arrows += 1
    player.say("Arrows Shot: " + arrows)
})
```

## Schritt 8
Schieße ein paar Pfeile und schaue, ob dein Code funktioniert.
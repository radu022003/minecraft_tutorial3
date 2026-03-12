### @explicitHints 1
# Aktivität: Pfeilzähler

## 1. Variable erstellen
Erstelle eine neue ``||VARIABLES:Variable||`` und nenne es **pfeil**.

## 2. Pfeilschuss-Event hinzufügen
Ziehe den ``||PLAYER:bei Pfeilschuss||``-Block in den Arbeitsbereich.

## 3. Zähler-Variable hinzufügen
Ziehe den ``||VARIABLES:ändere pfeil um||``-Block in den ``||PLAYER:bei Pfeilschuss||``-Block hinein.

## 4. Nachricht-Blöcke hinzufügen
Ziehe den ``||PLAYER:sag||``-Block in den ``||PLAYER:bei Pfeilschuss||``-Block hinein.

Ziehe danach den ``||TEXT:verbinde||``-Block in den ``||PLAYER:sag||``-Block hinein. 

**Hinweis:** Der ``||TEXT:verbinde||``-Block ist ein *FORTGESCHRITTENER* Block und im entsprechenden Reiter.

### ~ tutorialhint
 ``` blocks
 let arrows = 0
player.onArrowShot(function () {
    arrows += 1
    player.say("Hello" + "World")
})
```

## 5. Variable in Text einbinden
Ziehe die ``||VARIABLES:pfeil||``-Variable in den ersten Slot von ``||TEXT:verbinde||``.

## 6. Nachricht anpassen
Gib im zweiten Feld von ``||TEXT:verbinde||`` **" Pfeile abgeschossen"** ein (mit einem Leerzeichen am Anfang, sodass es schön aussieht)
.
### ~ tutorialhint
``` blocks
let arrows = 0
player.onArrowShot(function () {
    arrows += 1
    player.say("Arrows Shot: " + arrows)
})
```

## 7. Code testen
Schieße ein paar Pfeile und schaue, ob dein Code funktioniert.

### @explicitHints 1
# Aktivität: Pfeilzähler

## Schritt 1
Erstellen Sie eine neue Variable und nennen Sie sie **pfeil**.

## Schritt 2
Registrieren Sie abgeschossene Pfeile. Ziehen Sie den ``||Player:bei Pfeilschuss||``-Block in den Arbeitsbereich.

## Schritt 3
Ziehen Sie die ``||Variables:ändere um||``-Variable in den ``||Player:bei Pfeilschuss||``-Block.

## Schritt 4
In ``||Variables:ändere um||``, wählen Sie ``||Variables:pfeil||``.

## Schritt 5
Um den Text zusammenzufügen, klicken Sie auf die Kategorie **Erweitert** in der Werkzeugleiste, um die ``||Text:TEXT||``-Werkzeugleiste anzuzeigen. Ziehen Sie den ``||Text:verbinde||``-Block in den ``||Player:sag||``-Block, um den **"Hi"**-String zu ersetzen.

### ~ tutorialhint
 ``` blocks
 let arrows = 0
player.onArrowShot(function () {
    arrows += 1
    player.say("Hello" + "World")
})
```
## Schritt 6
Verbinden Sie die Variable mit der Nachricht. Geben Sie im ersten Feld von ``||Text:verbinde||`` **"Pfeile abgeschossen"** ein.

## Schritt 7
Ziehen Sie aus ``||Variables:VARIABLE||`` die Variable **pfeil** in den zweiten Slot von ``||Text:verbinde||``, um den String "World" zu ersetzen. Dieser Block wird den String "Pfeile abgeschossen: " mit der Nummervariable verbinden. ``||Player:sag||`` wird die Nachricht jedes Mal am oberen Bildschirmrand ausgeben, wenn Sie einen Pfeil abschießen.

### ~ tutorialhint
``` blocks
let arrows = 0
player.onArrowShot(function () {
    arrows += 1
    player.say("Arrows Shot: " + arrows)
})
```

## Schritt 8
Probieren Sie es aus! Gehen Sie in Minecraft und versuchen Sie es! Geben Sie sich selbst einen Bogen und Pfeile, indem Sie die folgenden Befehle in das Chatfenster eingeben:
* /give @p bow
* /give @p arrows 64

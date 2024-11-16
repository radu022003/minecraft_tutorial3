### @explicitHints 1

# Aktivität: Erstelle einen Kompassstern

## Schritt 1
Erstelle einen neuen ``||Player: Spieler||``-Befehl. Ziehe einen ``||Player:bei Chat-Befehl||``-Block heraus und ändere den Befehl zu **"Kompassstern"**.

### ~ tutorialhint
``` blocks
player.onChat("Kompassstern", function () {
})

```

## Schritt 2
Als Nächstes platziere einen ``||Blocks:fülle mit||``-Block innerhalb des ``||Player:bei Chat-Befehl||``-Blocks. Passe den ``||Blocks:fülle mit||``-Block von **Gras** auf das Material an, das du für die Achsen verwenden möchtest. In unserem Beispiel verwenden wir **Hellgraue Woll** für die Achsen.

## Schritt 3
Setze die Werte **(~ -10 ~ -1 ~ 0)** für **von** und **(~ 10 ~ -1 ~ 0)** für **bis** ein. Dies wird eine Linie aus 21 Blöcken entlang der X-Achse erstellen. Die Linie wird unter deinen Füßen sein und du wirst genau in der Mitte stehen.

### ~ tutorialhint
``` blocks
    player.onChat("Kompassstern", function () {
        blocks.fill(
        GRAY_WOOL,
        pos(-10, -1, 0),
        pos(10, -1, 0),
        FillOperation.Replace
        )
})
```
## Schritt 4
Schreibe die Richtungen "Ost" und "West". Suche nach dem ``||Blocks:schreibe||``-Block. Dieser Block schreibt Wörter durch den von dir gewählten Block, in die von dir gewählte Richtung.

## Schritt 5
Ziehe zwei ``||Blocks:schreibe||``-Blöcke heraus und platziere sie nach dem ``||Blocks:fülle mit||``-Block. Gib "W" im ersten ``||Blocks:schreibe||`` ein und **"O"** im zweiten ``||Blocks:schreibe||``, um West und Ost anzugeben.

## Schritt 6
Wähle einen Block aus, um die Buchstaben mit ``||Blocks:schreibe||`` zu platzieren. In diesem Beispiel wird **Hellgrüne Wolle** für Westen und **Gelbe Wolle** für Osten verwendet.

## Schritt 7
Im ``||Blocks:schreibe||``-Block für **W** gib die Koordinaten **(~-11 ~0 ~0)** ein.

Im ``||Blocks:schreibe||``-Block für **O** gib die Koordinaten **(~11 ~0 ~0)** ein.

### ~ tutorialhint
``` blocks
    player.onChat("Kompassstern", function () {
        blocks.fill(
        GRAY_WOOL,
        pos(-10, 0, 0),
        pos(10, 0, 0),
        FillOperation.Replace
        )
        blocks.print(
        "W",
        LIME_WOOL,
        pos(-11, 0, 0),
        WEST
        )
        blocks.print(
        "O",
        YELLOW_WOOL,
        pos(11, 0, 0),
        WEST
        )
})
```

## Schritt 8
Wiederhole das für Nord und Süd. Platziere einen ``||Blocks:fülle mit||``-Block in den ``||Player:Bei Chat-Befehl||``-Block.

Passe den ``||Blocks:fülle mit||``-Block von **Gras** auf das Material an, das du für die Achse verwenden möchtest. In diesem Beispiel wird **Schwarze Wolle** für die Achse verwendet.

## Schritt 9
Setze die Werte **(~0 ~-1 ~-10)** für **von** und **(~0 ~-1 ~10)** für **bis** ein. Dies wird eine Linie von Blöcken entlang der **Z**-Achse erstellen.

## Schritt 10
Ziehe zwei ``||Blocks:schreibe||``-Blöcke heraus und platziere sie nach dem neuesten ``||Blocks:fülle mit||``-Block.

## Schritt 11
Gib **"N"** im ersten ``||Blocks:schreibe||``-Block ein und **"S"** im zweiten ``||Blocks:schreibe||``-Block ein, um Nord und Süd anzugeben.

## Schritt 12
Wähle einen Block aus, um die Buchstaben mit ``||Blocks:schreibe||`` zu platzieren. In diesem Beispiel wird **Blaue Wolle** für den Norden und **Rote Wolle** für den Süden verwendet.

## Schritt 13
Im ``||Blocks:schreibe||``-Block für **N** gib die Koordinaten **(~0 ~0 ~-11)** ein.

Im ``||Blocks:schreibe||``-Block für **S** gib die Koordinaten **(~0 ~0 ~11)** ein.

### ~ tutorialhint
    ``` blocks
        player.onChat("Kompassstern", function () {
            blocks.fill(
            GRAY_WOOL,
            pos(-10, -1, 0),
            pos(10, -1, 0),
            FillOperation.Replace
            )
            blocks.print(
            "W",
            LIME_WOOL,
            pos(-11, 0, 0),
            WEST
            )
            blocks.print(
            "O",
            YELLOW_WOOL,
            pos(11, 0, 0),
            WEST
            )
            blocks.fill(
            GRAY_WOOL,
            pos(0, -1, -10),
            pos(0, -1, 10),
            FillOperation.Replace
            )
            blocks.print(
            "N",
            BLUE_WOOL,
            pos(0, 0, -11),
            WEST
            )
            blocks.print(
            "S",
            RED_WOOL,
            pos(0, 0, 11),
            WEST
            )
})
```

### @explicitHints 1

# Aktivität: Erstelle einen Kompassstern

## 1. Chat-Befehl anlegen
Erstelle einen neuen ``||PLAYER:bei Chat-Befehl||``-Block und ändere den Befehl zu **"Kompassstern"**.

> **Hintergrundwissen – Koordinaten und Himmelsrichtungen in Minecraft:**
> In Minecraft entsprechen die Koordinatenwerte bestimmten Himmelsrichtungen:
> - **X positiv (+X)** = Osten (O)
> - **X negativ (-X)** = Westen (W)
> - **Z positiv (+Z)** = Süden (S)
> - **Z negativ (-Z)** = Norden (N)
>
> Mit `(~ -10, ~ -1, ~ 0)` setzt du also einen Block **10 Felder westlich** von dir.

### ~ tutorialhint
``` blocks
player.onChat("Kompassstern", function () {
})

```

## 2. X-Achse bauen
Platziere einen ``||BLOCKS:fülle mit||``-Block innerhalb des ``||PLAYER:bei Chat-Befehl||``-Blocks. Passe den Block von **Gras** auf das Material an, das du für die Achsen verwenden möchtest. In unserem Beispiel verwenden wir **Hellgraue Wolle**.

## 3. X-Koordinaten setzen
Setze die Werte **(~ -10, ~ -1, ~ 0)** für **von** und **(~ 10, ~ -1, ~ 0)** für **bis** ein. Dies erstellt eine Linie aus 21 Blöcken entlang der X-Achse.

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
## 4. West und Ost beschriften
Suche nach dem ``||BLOCKS:schreibe||``-Block. Dieser Block schreibt Wörter aus Blöcken in eine Richtung.

## 5. W und O setzen
Ziehe zwei ``||BLOCKS:schreibe||``-Blöcke heraus und platziere sie nach dem ``||BLOCKS:fülle mit||``-Block. Gib **"W"** im ersten und **"O"** im zweiten Block ein.

**Beachte die Himmelsrichtungen:**
- **W** (Westen) liegt in **negativer X-Richtung** (→ X-Koordinate negativ)
- **O** (Osten) liegt in **positiver X-Richtung** (→ X-Koordinate positiv)

## 6. Farben wählen
Wähle die Blöcke für die Buchstaben. In diesem Beispiel wird **Hellgrüne Wolle** für Westen und **Gelbe Wolle** für Osten verwendet.

## 7. Positionen für W und O
Im ``||BLOCKS:schreibe||``-Block für **W** gib die Koordinaten **(~ -11, ~ 0, ~ 0)** ein.

Im ``||BLOCKS:schreibe||``-Block für **O** gib die Koordinaten **(~ 11, ~ 0, ~ 0)** ein.

Stelle die Schreibrichtung für **beide** Blöcke auf **Süden**, damit die Buchstaben zum Spieler zeigen.

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
        SOUTH
        )
        blocks.print(
        "O",
        YELLOW_WOOL,
        pos(11, 0, 0),
        SOUTH
        )
})
```

## 8. Z-Achse bauen
Platziere einen ``||BLOCKS:fülle mit||``-Block in den ``||PLAYER:bei Chat-Befehl||``-Block.

Passe den ``||BLOCKS:fülle mit||``-Block von **Gras** auf das Material an, das du für die Achse verwenden möchtest. In diesem Beispiel wird **Schwarze Wolle** verwendet.

## 9. Z-Koordinaten setzen
Setze die Werte **(~ 0, ~ -1, ~ -10)** für **von** und **(~ 0, ~ -1, ~ 10)** für **bis** ein. Dies erstellt eine Linie entlang der Z-Achse.

## 10. N und S vorbereiten
Als nächstes erstellen wir die fehlenden zwei Achsen. 
Ziehe zwei ``||BLOCKS:schreibe||``-Blöcke heraus und platziere sie nach dem zweiten ``||BLOCKS:fülle mit||``-Block.

## 11. N und S setzen
Gib **"N"** im ersten ``||BLOCKS:schreibe||``-Block ein und **"S"** im zweiten ``||BLOCKS:schreibe||``-Block ein.

**Beachte die Himmelsrichtungen:**
- **N** (Norden) liegt in **negativer Z-Richtung** (→ Z-Koordinate negativ)
- **S** (Süden) liegt in **positiver Z-Richtung** (→ Z-Koordinate positiv)

## 12. Farben für N und S
Wähle einen Block aus, um die Buchstaben zu platzieren. In diesem Beispiel wird **Blaue Wolle** für Norden und **Rote Wolle** für Süden verwendet.

## 13. Positionen für N und S
Im ``||BLOCKS:schreibe||``-Block für **N** gib die Koordinaten **(~ 0, ~ 0, ~ -11)** ein.

Im ``||BLOCKS:schreibe||``-Block für **S** gib die Koordinaten **(~ 0, ~ 0, ~ 11)** ein.

Stelle auch hier die Schreibrichtung auf **Süden** für beide Blöcke.

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
            SOUTH
            )
            blocks.print(
            "O",
            YELLOW_WOOL,
            pos(11, 0, 0),
            SOUTH
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
            SOUTH
            )
            blocks.print(
            "S",
            RED_WOOL,
            pos(0, 0, 11),
            SOUTH
            )
})
```

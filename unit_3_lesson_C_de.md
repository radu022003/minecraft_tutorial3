### @explicitHints 1

# Aktivität: Schafstall-Bauer

## 1. Schaf bei Bewegung spawnen
Hol dir den Block ``||PLAYER:bei gehen Spieler||`` und ziehe ihn in die Arbeitsfläche.

Ziehe den Block ``||MOBS:spawne||`` in den Block ``||PLAYER:bei gehen Spieler||``. Wähle **Schaf** oder ein anderes Tier.

## 2. Spawn-Koordinate setzen
Setze die Koordinaten **(~ 0, ~ 0, ~ 1)** im ``||MOBS:spawne||``-Block. Das Schaf erscheint 1 Block südlich vom Spieler.

**Erinnerung:** Positives Z = Süden, negatives Z = Norden.

### ~ tutorialhint
``` blocks
player.onTravelled(WALK, function () {
    mobs.spawn(SHEEP, pos(0, 0, 1))
})
```

## 3. Befehl für den Stall anlegen
Ziehe einen neuen ``||PLAYER:bei Chat-Befehl||`` in die Arbeitsfläche und ändere den Befehl zu **"stall"**.

## 4. Südwand bauen
Platziere einen ``||BLOCKS:fülle mit||``-Block innerhalb des ``||PLAYER:bei Chat-Befehl "stall"||``.

Passe den Block auf **Netherziegelzaun** an. Setze die Koordinaten auf **(~ 5, ~ 0, ~ 1)** und **(~ -5, ~ 4, ~ 1)**.

### ~ tutorialhint
``` blocks
player.onTravelled(WALK, function () {
    mobs.spawn(SHEEP, pos(0, 0, 1))
})
player.onChat("stall", function () {
    blocks.fill(
    NETHER_BRICK_FENCE,
    pos(5, 0, 1),
    pos(-5, 4, 1),
    FillOperation.Replace
    )
})
```

## 5. Seiten mit zwei Zauntypen bauen
Klicke mit der rechten Maustaste auf den ``||BLOCKS:fülle mit||``-Block, der deine Südwand erstellt, und dupliziere ihn **zweimal**. Diese neuen Duplikate werden deine Seitenwände sein.

- Linke Seite: **Birkenzaun**
- Rechte Seite: **Akazienzaun**

## 6. Seitenkoordinaten korrekt setzen
Setze die Koordinaten:

- **Birkenzaun**: von **(~ -5, ~ 0, ~ 1)** bis **(~ -5, ~ 4, ~ 20)**
- **Akazienzaun**: von **(~ 5, ~ 0, ~ 1)** bis **(~ 5, ~ 4, ~ 20)**

### ~ tutorialhint
``` blocks 
player.onTravelled(WALK, function () {
    mobs.spawn(SHEEP, pos(0, 0, 1))
})
player.onChat("stall", function () {
    blocks.fill(
    NETHER_BRICK_FENCE,
    pos(5, 0, 1),
    pos(-5, 4, 1),
    FillOperation.Replace
    )
    blocks.fill(
    BIRCH_FENCE,
    pos(-5, 0, 1),
    pos(-5, 4, 20),
    FillOperation.Replace
    )
    blocks.fill(
    ACACIA_FENCE,
    pos(5, 0, 1),
    pos(5, 4, 20),
    FillOperation.Replace
    )
})
```

## 7. Nordwand schließen
Schließe den Schafstall mit einem Nordzugang. **Z** sollte genau **20** Blöcke von deiner Südwand entfernt sein, weil das die Länge deiner Seitenwände ist. Probiere es in Minecraft aus und spawne so viele Schafe wie du möchtest!

### ~ tutorialhint
``` blocks
player.onChat("stall", function () {
    blocks.fill(
    NETHER_BRICK_FENCE,
    positions.create(5, 0, -1),
    positions.create(-5, 4, -1),
    FillOperation.Replace
    )
    blocks.fill(
    ACACIA_FENCE,
    positions.create(-5, 0, -1),
    positions.create(-5, 4, 20),
    FillOperation.Replace
    )
    blocks.fill(
    BIRCH_FENCE,
    positions.create(5, 0, -1),
    positions.create(5, 4, 20),
    FillOperation.Replace
    )
    blocks.fill(
    NETHER_BRICK_FENCE,
    positions.create(5, 0, 20),
    positions.create(-5, 4, 20),
    FillOperation.Replace
    )
})
```

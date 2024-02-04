### @explicitHints 1

# Aktivität: Auto Farmer

## Schritt 1
Hol dir den Block ``||Player:bei gehen Spieler||`` und ziehe ihn in die Arbeitsfläche.

Ziehe den Block ``||Mobs:spawne||`` in den Block ``||Player:bei gehen Spieler||``. Wähle das **Schaf** oder ein anderes Tier für deine Farm im Block ``||Mobs:spawne||`` aus.

## Schritt 2
Setze die Koordinaten **(~0, ~0, ~1)** im ``||Mobs:spawne||``-Block. Das Schaf wird einen Block südlich des Spielers entlang der **Z**-Achse erscheinen.

### ~ tutorialhint
``` blocks
player.onTravelled(WALK, function () {
    mobs.spawn(SHEEP, pos(0, 0, 1))
})
```

## Schritt 3
Starte den Schafstall. Ziehe einen neuen ``||Player:Bei Chat-Befehl||`` in die Arbeitsfläche und ändere den Befehl zu **"pen"**.

## Schritt 4
Platziere einen ``||Blocks:fülle mit||``-Block innerhalb des ``||Player:Bei Chat-Befehl "pen"||``.

Passe den ``||Blocks:fülle mit||``-Block auf **Netherziegelzaun** an. Und ändere die Koordinaten zu **~5, ~0, ~1** und **~-5, ~4, ~1**.

### ~ tutorialhint
``` blocks
player.onTravelled(WALK, function () {
    mobs.spawn(SHEEP, pos(0, 0, 1))
})
player.onChat("pen", function () {
    blocks.fill(
    NETHER_BRICK_FENCE,
    pos(5, 0, 1),
    pos(-5, 4, 1),
    FillOperation.Replace
    )
})
```

## Schritt 5
Erstelle Seitenwände. Klicke mit der rechten Maustaste auf den ``||Blocks:fülle mit||``-Block, der deine Südwand erstellt, und dupliziere ihn zweimal. Diese neuen Duplikate werden deine Seitenwände sein.

## Schritt 6
Passe das Material für die Seitenwände an. Eine Seite kann aus **Akazienzaun**, und die andere aus **Birkenzaun** sein.

## Schritt 7
Passe die Koordinaten für den **Akazienzaun** auf **~5, ~0, ~1** und **~-5, ~4, ~20** an; und für den **Birkenzaun** auf **~5, ~0, ~1** und **~-5, ~4, ~20**.

### ~ tutorialhint
``` blocks 
player.onTravelled(WALK, function () {
    mobs.spawn(SHEEP, pos(0, 0, 1))
})
player.onChat("pen", function () {
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
## Schritt 8
Schließe den Schafstall mit einem Nordzugang. **Z** sollte genau **20** Blöcke von deiner Südwand entfernt sein, weil das die Länge deiner Seitenwände ist. Probiere es in Minecraft aus und spawne so viele Schafe wie du möchtest!

### ~ tutorialhint
``` blocks
player.onChat("pen", function () {
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

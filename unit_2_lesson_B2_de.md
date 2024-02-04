### @explicitHints 1

# Letzte Schlacht am Alamo. 

## Schritt 1
Reaktion auf ein Ereignis, bei dem eine Menge ``||Mobs:KREATUREN||`` getötet wurde: Ziehen Sie aus dem Werkzeugkasten für Mobs einen ``||Mobs:wenn getötet||`` in die Codierungsarbeitsfläche.

### ~ tutorialhint
```blocks
mobs.onMobKilled(CHICKEN, function () {
})
```

## Schritt 2
Überprüfen Sie, ob es sich um ein Monster handelt: Ziehen Sie aus dem ``||Mobs:KREATUREN||`` einen ``||Mobs:Monster||`` heraus, um den Standardwert Tier zu ersetzen. Verwenden Sie das Dropdown-Menü im ``||Mobs:Monster||``, um das **Zombie**-Spawn-Ei auszuwählen.

## Schritt 3
Richten Sie sich ein, um neue Zombies erscheinen zu lassen! Ziehen Sie aus dem ``||Mobs:KREATUREN||`` ein ``||Mobs:spawne||``-Block unter den ``||Mobs:wenn getötet||`` Ereignis-Handler-Block.

### ~ tutorialhint
```blocks
mobs.onMobKilled(mobs.monster(ZOMBIE), function () {
mobs.spawn(CHICKEN, pos(0, 0, 0))
})
```

## Schritt 4
Wählen Sie das Zombie-Ei aus. Ähnlich wie im Schritt 2 müssen Sie hier die Standard-Einstellung **Tier** im Spawn-Block durch Zombie ersetzen.

### ~ tutorialhint
```blocks
mobs.onMobKilled(mobs.monster(ZOMBIE), function () {
mobs.spawn(mobs.monster(ZOMBIE), pos(0, 0, 0))
})
```

## Schritt 5
Zwei Zombies sind besser als einer. Sie möchten für jeden getöteten Zombie zwei neue erscheinen lassen. Ziehen Sie aus dem ||Loops:Schleifen||-Werkzeugkasten eine ``||Loops:Schleifen||``-Schleife in die Arbeitsfläche. Diese ``||Loops:wiederholen||``-Schleife sollte innerhalb des ``||Mobs:wenn getötet||`` Ereignisses sein, und Ihr ``||Mobs:spawne||``-Block sollte innerhalb der ``||Loops:wiederholen||``-Schleife liegen.

Geben Sie in der ``||Blocks:wiederholen||``-Schleife die Zahl **2** ein.

### ~ tutorialhint
```blocks
mobs.onMobKilled(mobs.monster(ZOMBIE), function () {
    for (let index = 0; index < 2; index++) {
        mobs.spawn(mobs.monster(ZOMBIE), pos(0, 0, 0))
    }
})
```

## Schritt 6
Wo sollen die Zombies erscheinen? Ersetzen Sie die Standardposition **(~0 ~0 ~0)** durch einen ``||Positions:Wähle zufällige Position||``-Block.

## Schritt 7
Stellen Sie den Bereich für die zufällige Position ein: Geben Sie im ``||Blocks:Wähle zufällige Position||``-Block die **von**-Koordinaten als **(~10 ~0 ~10)** und die **bis**-Koordinaten als **(~-10 ~0 ~-10)** ein.

### ~ tutorialhint
```blocks
mobs.onMobKilled(mobs.monster(ZOMBIE), function () {
    for (let i = 0; i < 2; i++) {
        mobs.spawn(mobs.monster(ZOMBIE), randpos(
            pos(10, 0, 10),
            pos(-10, 0, -10)
        ))
    }
})
```

## Schritt 8

Probierst du es im Spiel aus!

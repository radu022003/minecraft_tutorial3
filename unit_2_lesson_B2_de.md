### @explicitHints 1

# Letzte Schlacht am Alamo. 

## 1. Kreaturen erkennen
Ziehe einen ``||Mobs:wenn getötet||``-Block auf die Arbeitsfläche.

### ~ tutorialhint
```blocks
mobs.onMobKilled(CHICKEN, function () {
})
```

## 2. Monnster erkennen
Ziehe aus dem ``||Mobs:KREATUREN||``-Blöcken einen ``||Mobs:Monster||``-Block heraus, um den Standardwert Tier zu ersetzen. Verwende das Dropdown-Menü im ``||Mobs:Monster||`` und wähle **Zombie**-Spawn-Ei aus.

## 3. Neue Zombies erstellen 
Ziehe aus den ``||Mobs:KREATUREN||``-Blöcken einen ``||Mobs:spawne||``-Block in den ``||Mobs:wenn getötet||``-Block.

### ~ tutorialhint
```blocks
mobs.onMobKilled(mobs.monster(ZOMBIE), function () {
mobs.spawn(CHICKEN, pos(0, 0, 0))
})
```

## 4. Zombies auswählen
Ersätze die Standard-Einstellung **Tier** im Spawn-Block durch Zombie-Ei.

### ~ tutorialhint
```blocks
mobs.onMobKilled(mobs.monster(ZOMBIE), function () {
mobs.spawn(mobs.monster(ZOMBIE), pos(0, 0, 0))
})
```

## 5. Mehr Zombies
Zwei Zombies sind besser als einer. Sie möchten für jeden getöteten Zombie zwei neue erscheinen lassen. 

Ziehen Sie aus dem ``||Loops:Schleifen||`` eine ``||Loops:Schleife||`` in die Arbeitsfläche. Diese ``||Loops:wiederholen||``-Schleife sollte innerhalb des ``||Mobs:wenn getötet||`` Ereignisses sein, und der ``||Mobs:spawne||``-Block sollte innerhalb der ``||Loops:wiederholen||``-Schleife liegen.

Geben Sie in der ``||Loops:wiederholen||``-Schleife die Zahl **2** ein.

### ~ tutorialhint
```blocks
mobs.onMobKilled(mobs.monster(ZOMBIE), function () {
    for (let index = 0; index < 2; index++) {
        mobs.spawn(mobs.monster(ZOMBIE), pos(0, 0, 0))
    }
})
```

## 6. Wo sollen die Zombies erscheienen? 
Ersetze die Standardposition **(~0 ~0 ~0)** durch einen ``||Positions:Wähle zufällige Position||``-Block.

## 7. Zufällige Position einstellen
Gib im ``||Positions:Wähle zufällige Position||``-Block die **von**-Koordinaten als **(~10 ~0 ~10)** und die **bis**-Koordinaten als **(~-10 ~0 ~-10)** ein.

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

## 8. Code testen

Probiere deinen Code aus!

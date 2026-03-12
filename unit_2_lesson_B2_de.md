### @explicitHints 1

# Zombies! Sie werden immer mehr!

## Vorbereitung
- Stelle den Schwierigkeitsgrad von **Friedlich** auf **Einfach**, damit Zombies spawnen können! (Pausemenü → Einstellungen → Schwierigkeitsgrad)
- Lege zuerst folgende Gegenstände in dein Inventar: **Wüstenzombie-Spawn-Ei**, **Rüstung** und ein **Schwert**.
- Stelle danach den Spielmodus auf **Überleben**.

Hinweis: Wir verwenden **Wüstenzombies**. Diese verbrennen tagsüber nicht, daher musst du die Tageszeit nicht manuell ändern.

## 1. Ereignis bei getötetem Monster
Ziehe einen ``||MOBS:wenn _ getötet||``-Block auf die Arbeitsfläche.

Dieser Block führt den Code darin aus, **jedes Mal wenn eine bestimmte Kreatur getötet wird**.

### ~ tutorialhint
```blocks
mobs.onMobKilled(CHICKEN, function () {
})
```

## 2. Wüstenzombie auswählen
Standardmäßig ist ein Huhn eingestellt. Wir wollen auf **Wüstenzombies** reagieren.

Ziehe aus ``||MOBS:KREATUREN||`` einen ``||MOBS:Monster||``-Block und ersetze damit das Huhn im ``||MOBS:wenn _ getötet||``-Block. Klicke dann auf das Dropdown-Menü und wähle **Wüstenzombie** aus.

## 3. Spawn-Block hinzufügen
Ziehe aus ``||MOBS:KREATUREN||`` einen ``||MOBS:spawne _ bei||``-Block in den ``||MOBS:wenn Wüstenzombie getötet||``-Block.

Damit wird jedes Mal, wenn ein Wüstenzombie getötet wird, eine neue Kreatur gespawnt. Im nächsten Schritt legen wir fest, was gespawnt werden soll.

### ~ tutorialhint
```blocks
mobs.onMobKilled(mobs.monster(HUSK), function () {
mobs.spawn(CHICKEN, pos(0, 0, 0))
})
```

## 4. Husk spawnen
Ersetze im Spawn-Block das Tier durch einen ``||MOBS:Monster||``-**Wüstenzombie**-Block.

Jetzt spawnt beim Tod eines Wüstenzombie ein neuer Wüstenzombie.

### ~ tutorialhint
```blocks
mobs.onMobKilled(mobs.monster(HUSK), function () {
mobs.spawn(mobs.monster(HUSK), pos(0, 0, 0))
})
```

## 5. Zwei neue Monster pro Kill
Jetzt sollen beim Tod eines Husks **zwei neue** erscheinen.

Ziehe den ``||SCHLEIFEN:_-mal wiederholen||``-Block um den ``||MOBS:spawne Wüstenzombie bei||``-Block herum. Setze die Zahl auf **2**.

Die Schleife sorgt dafür, dass der Spawn-Block **zweimal** ausgeführt wird – also immer 2 neue Zombies erscheinen.

### ~ tutorialhint
```blocks
mobs.onMobKilled(mobs.monster(HUSK), function () {
    for (let index = 0; index < 2; index++) {
        mobs.spawn(mobs.monster(HUSK), pos(0, 0, 0))
    }
})
```

## 6. Zufällige Spawn-Position
Mit der aktuellen Koordinate `~0, ~0, ~0` spawnen alle Monster genau auf deiner Position. Das ist zu gefährlich!

Ersetze die Standardposition **(~ 0, ~ 0, ~ 0)** durch einen ``||POSITIONEN:wähle zufällige Position||``-Block aus ``||POSITIONEN:Positionen||``.

## 7. Zufälligen Bereich einstellen
Setze im ``||POSITIONEN:wähle zufällige Position||``-Block:
- **von**: **(~ 10, ~ 0, ~ 10)**
- **bis**: **(~ -10, ~ 0, ~ -10)**

Damit spawnen die Wüstenzombies an einem zufälligen Punkt in einem Bereich von 10 Blöcken um dich herum.

### ~ tutorialhint
```blocks
mobs.onMobKilled(mobs.monster(HUSK), function () {
    for (let i = 0; i < 2; i++) {
        mobs.spawn(mobs.monster(HUSK), randpos(
            pos(10, 0, 10),
            pos(-10, 0, -10)
        ))
    }
})
```

## 8. Testen
Probiere deinen Code in Minecraft aus! 

**So funktioniert es:**
1. Platziere mit dem Wüstenzombie-Spawn-Ei einen Wüstenzombie in der Welt.
2. Töte ihn mit deinem Schwert.
3. Beobachte, wie **2 neue Wüstenzombies** erscheinen.
4. Töte diese – und es werden **4** – dann **8** – dann **16**...

> Es werden immer mehr! Kannst du das Zombie-Problem unter Kontrolle behalten?

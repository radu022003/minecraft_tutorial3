### @explicitHints 1

# Versteckte Spinnen

## Vorbereitung
- Stelle den Schwierigkeitsgrad von **Friedlich** auf **Einfach**, damit Spinnen spawnen können! (Pausenmenü → Einstellungen → Schwierigkeitsgrad)
- Lege ein **Spinnennetz** in dein Inventar.

## 1. Blockabbau erkennen
Ziehe den ``||BLOCKS:wenn _ abgebaut||``-Block aus ``||BLOCKS:Blöcke||`` in die Arbeitsfläche.

Dieser Block führt den Code darin aus, **jedes Mal wenn ein bestimmter Block abgebaut wird**.

### ~ tutorialhint
```blocks
blocks.onBlockBroken(GRASS, function () {
	
})
```

## 2. Spinnennetz auswählen
Klicke auf das Dropdown-Menü im ``||BLOCKS:wenn _ abgebaut||``-Block und wähle **Spinnennetz** aus.

Jetzt reagiert dein Code, sobald ein Spinnennetz abgebaut wird.

## 3. Spinnen-Spawn hinzufügen
Ziehe aus ``||MOBS:Kreaturen||`` den ``||MOBS:spawne _ bei||``-Block in den ``||BLOCKS:wenn Spinnennetz abgebaut||``-Block.

Im Spawn-Block siehst du zunächst ein **Tier** (z.B. Huhn). Wir wollen aber eine Spinne spawnen, die unter den **Monstern** zu finden ist – das änderst du im nächsten Schritt.

### ~ tutorialhint
```blocks
blocks.onBlockBroken(COBWEB, function () {
    mobs.spawn(SPIDER, pos(0, 0, 0))
})
```

## 4. Spinne und Höhe einstellen
Klicke auf das Dropdown-Menü im ``||MOBS:spawne _ bei||``-Block und wähle **Spinne** aus.

**Wichtig:** Ändere außerdem die **Y-Koordinate** auf **1**, damit die Spinne 1 Block über dem Boden erscheint und nicht in der Erde steckt.

## 5. Mehr Spinnen mit einer Schleife
Ziehe den ``||SCHLEIFEN:_-mal wiederholen||``-Block um den ``||MOBS:spawne _ bei||``-Block herum. Ändere die Zahl auf **10**.

**Was macht eine Schleife?** Eine Schleife wiederholt den Code darin mehrmals. Mit der Zahl **10** werden **10 Spinnen** gespawnt – statt nur einer!

### ~ tutorialhint
```blocks
blocks.onBlockBroken(COBWEB, function () {
    for (let index = 0; index < 10; index++) {
        mobs.spawn(SPIDER, pos(0, 1, 0))
    }
})
```

## 6. Testen
Platziere ein **Spinnennetz** aus deinem Inventar in der Spielwelt. Baue es dann ab – dabei sollten **10 Spinnen** erscheinen!

> **Tipp:** Falls keine Spinnen erscheinen, überprüfe ob der Schwierigkeitsgrad auf **Einfach** oder höher gestellt ist. Auf **Friedlich** spawnen keine Monster.

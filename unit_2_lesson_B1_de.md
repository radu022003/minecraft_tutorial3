### @explicitHints 1

# Versteckte Spinnen

## 1. Abbau von Blöcken erkennen
Ziehe den ``||Blocks: wenn _ abgebaut||``-Befehl aus ``||Blocks: Blöcke||`` in die Arbeitsfläche.

### ~ tutorialhint
```blocks
blocks.onBlockBroken(GRASS, function () {
	
})
```

## 2. Spinnennetz abbauen
Wähle aus dem Dropdown-Menü das **Spinnennetz**-Element aus.
        
## 3. Tiere spawnen
Ziehe aus ``||Mobs:Kreaturen||`` den ``||Mobs:spawne _ bei||``-Block in den ``||Blocks:wenn _ abgebaut||``-Block.

### ~ tutorialhint     

```blocks
blocks.onBlockBroken(COBWEB, function () {
    mobs.spawn(SPIDER, pos(0, 0, 0))
})
```

## 4. Spinne spawnen
Wähle aus dem Dropdown-Menü im ``||Mobs:spawne _ bei||``-Block **Spinne** aus und ändere die **Y**-Koordinate auf **1**.

## 5. Mehr Spinnen
Platziere eine ``||Loops:Schleife||`` um ``||Mobs:spawne _ bei||``. Gebe in der ``||Loops:Schleife||`` die Zahl **10** ein.

### ~ tutorialhint
```blocks
blocks.onBlockBroken(COBWEB, function () {
    for (let index = 0; index < 10; index++) {
        mobs.spawn(SPIDER, pos(0, 1, 0))
    }
})
```

## 6. Code testen
Platziere ein Spinnenetz und baue ihn wieder ab. Dabei sollten Spinnen erscheinen.

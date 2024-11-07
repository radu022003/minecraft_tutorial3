### @explicitHints 1

# Singen Sie ein Lied von Sixpence

## 1. Blockabbau erkennen
Ziehe den ``||Blocks: wenn abgebaut||``-Befehl aus ``||Blocks: Blöcke||`` in die Arbeitsfläche.

### ~ tutorialhint
```blocks
blocks.onBlockBroken(GRASS, function () {
	
})
```

## 2. Kuchen abbauen
Wähle aus dem Dropdown-Menü das **Kuchen**-Element aus.
        
## 3. Tiere spawnen
Ziehen Sie aus ``||Mobs:Kreaturen||`` den ``||Mobs:spawne bei||``-Block in den ``||Blocks:wenn abgebaut||``-Block.

### ~ tutorialhint     

```blocks
blocks.onBlockBroken(CAKE, function () {
    mobs.spawn(CHICKEN, pos(0, 0, 0))
})
```

## 4. Papagei spawnen
Wählen Sie aus dem Dropdown-Menü im ``||Mobs:spawne bei||``-Block **Papagei** aus und ändern Sie die **Y**-Koordinate auf **1**.

## 5. Mehr Papageien
Platzieren Sie eine ``||Loops:Schleife||`` um ``||Mobs:spawne bei||``. Geben Sie in der ``||Loops:Schleife||`` die Zahl **24** ein.

### ~ tutorialhint
```blocks
blocks.onBlockBroken(CAKE, function () {
    for (let index = 0; index < 24; index++) {
        mobs.spawn(CHICKEN, pos(0, 1, 0))
    }
})
```

## 6. Code testen
Platziere einen Kuchen und baue ihn wieder ab. Dabei sollten Papageien erscheinen.

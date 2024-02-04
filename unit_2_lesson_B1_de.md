### @explicitHints 1

# Singen Sie ein Lied von Sixpence

## Schritt 1
Überprüfen Sie auf zerstörte Blöcke. Ziehen Sie den ``||Blocks: wenn abgebaut||``-Befehl aus ``||Blocks: Blöcke||`` in die Arbeitsfläche.

### ~ tutorialhint
```blocks
blocks.onBlockBroken(GRASS, function () {
	
})
```

## Schritt 2
Wählen Sie den **Kuchen** aus. Verwenden Sie das Dropdown-Menü und wählen Sie das **Kuchen**-Element aus.
        
## Schritt 3
Spawne ein Tier. Ziehen Sie aus ``||Mobs:Kreaturen||`` den ``||Mobs:spawne bei||``-Block unter den ``||Blocks:wenn abgebaut||``-Block, bis er an Ort und Stelle einrastet.

### ~ tutorialhint     

```blocks
blocks.onBlockBroken(CAKE, function () {
    mobs.spawn(CHICKEN, pos(0, 0, 0))
})
```

## Schritt 4
Machen Sie es zu einem Papagei. Wählen Sie aus dem Dropdown-Menü im ``||Mobs:spawne bei||``-Block **Papagei** aus und ändern Sie die **Y**-Koordinate auf **1**.

## Schritt 5
Add more parrots. From loops, place a ``||Blocks:Schleifen||`` loop around ``||Mobs:spawne bei||``. In the ``||Blocks:Schleifen||`` loop, enter the number **24**.
Fügen Sie mehr Papageien hinzu. Platzieren Sie eine ``||Blocks:Schleifen||`` um ``||Mobs:spawne bei||``. Geben Sie in der ``||Blocks:Schleifen||`` die Zahl **24** ein.

### ~ tutorialhint
```blocks
blocks.onBlockBroken(CAKE, function () {
    for (let index = 0; index < 24; index++) {
        mobs.spawn(CHICKEN, pos(0, 1, 0))
    }
})
```

## Schritt 6
Führen Sie den Code aus. Um dies im Spiel auszuführen, fügen Sie einen Kuchen zu Ihrem Inventar hinzu (drücken Sie E, um Ihr Inventar zu öffnen), wählen Sie den Kuchen in Ihrer Symbolleiste aus (verwenden Sie das Mausrad oder die Nummerntasten) und klicken Sie mit der rechten Maustaste, um den Kuchen auf den Boden zu legen. Wechseln Sie dann wieder zu Ihren Händen und verwenden Sie die linke Maustaste, um den Kuchen zu zerstören - Sie sollten eine Gruppe von Papageien erscheinen sehen!

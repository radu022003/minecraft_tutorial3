### @explicitHints 1

# Sing a Song of Sixpence

## Step 1
Check for Broken Blocks. Drag the ``|| Blocks: wenn abgebaut||`` coding command from ``||Blocks: Blöcke||`` into the workspace. 

### ~ tutorialhint
```blocks
blocks.onBlockBroken(GRASS, function () {
	
})
```

## Step 2
Select the **Kuchen**. Using the drop-down menu, select the **Kuchen** item. 
        
## Step 3
Spawn an animal. From ``||Mobs:Kreaturen||``, place ``||Mobs:spawne bei||`` under the ``||Blocks:wenn abgebaut||`` block until you see it snap into place.

### ~ tutorialhint     

```blocks
blocks.onBlockBroken(CAKE, function () {
    mobs.spawn(CHICKEN, pos(0, 0, 0))
})
```

## Step 4
Make it a parrot. From the drop-down menu in the ``||Mobs:spawne bei||`` block, select a **Papagei** and change **Y** coordinate to **1**.

## Step 5
Add more parrots. From loops, place a ``||Blocks:Schleifen||`` loop around ``||Mobs:spawne bei||``. In the ``||Blocks:Schleifen||`` loop, enter the number **24**.

### ~ tutorialhint
```blocks
blocks.onBlockBroken(CAKE, function () {
    for (let index = 0; index < 24; index++) {
        mobs.spawn(CHICKEN, pos(0, 1, 0))
    }
})
```

## Step 6
Run the code. To run this in the game, add a cake to your player inventory (press E to open your inventory), select the cake in your toolbar (use the mouse wheel or the number keys), and right-click to place the cake on the ground. Then change back to your hands and use the left mouse button to hit the cake to destroy it – you should see a flock of parrots appear!



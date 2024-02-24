### @explicitHints 1

# Aktivität: Warp Belt

## Schritt 1
Drag a ``||Loops:beim start||`` block onto the coding Workspace.
Create an empty array. 

## Schritt 2
Make a variable and name it **warp_array**. Drag a ``||Variables:setze||`` block into the on start.

From the ``||Variables:setze||`` drop-down menu, select the **warp_array** variable.

## Schritt 3
Drag ``||Arrays:leeres Array||`` into the ``||Variables:setze "warp_array" auf||``.

In ``||Arrays:leeres Array||``, click the minus sign **(–)** to empty it. You should see the title change to ``||Arrays:leeres Array||``.

### ~ tutorialhint
``` blocks
let warp_array: number[] = []
warp_array = []
```

## Schritt 4
Make the "delete" command. Drag an ``||Player:Bei Chat-Befehl||`` onto the Workspace.

Name this command **delete**.

## Schritt 5
Right-click the existing ``||Variables:setze||`` in ``||Loops:beim start||`` and select Duplicate.

Drag this new ``||Variables:setze||`` block into ``||Player:Bei Chat-Befehl "delete"||``.

## Schritt 6
Drag a ``||Player:sag||`` after ``||Variables:setze||``.

In ``||Player:sag||``, enter a message, for example, **"Array deleted"**.

### ~ tutorialhint
``` blocks
let warp_array: number[] = []
player.onChat("delete", function () {
    warp_array = []
    player.say("Array deleted")
})
warp_array = []
```
## Schritt 7
Make the "save" command. Drag another ``||Player:Bei Chat-Befehl||`` to the Workspace.

Name this command **save**.

## Schritt 8
Drag ``||Arrays:füge Wert am Ende hinzu||`` into ``||Player:Bei Chat-Befehl "save"||``.

Set the position into the warp array.From the ``||Arrays:füge Wert am Ende hinzu||`` drop-down menu, select **warp_array** as the array you want to add values to.

Drag a ``||Player:Position des Spielers in der Welt||`` into the Add value of ``||Arrays:füge Wert am Ende hinzu||``.

### ~ tutorialhint
``` blocks
let warp_array: Position[] = []
warp_array.push(player.position())
```

## Schritt 9
Drag a ``||Player:sag||`` block after the ``||Arrays:"warp_array" füge Wert "player world position" am Ende hinzu||`` block.

In the ``||Player:sag||`` block, enter a message, for example, **"position added"**.

### ~ tutorialhint
``` blocks
let warp_array: Position[] = [] 
player.onChat("delete", function () {
    warp_array = []
    player.say("Array deleted")
})
player.onChat("save", function () {
    warp_array.push(player.position())
    player.say("position added")
})
warp_array = []
```

## Schritt 10
Create a "warp" command. The player will use the warp command by passing in a number, such as "warp 1" or "warp 2", to teleport themselves to a saved location in the array.

Drag a ``||Player:Bei Chat-Befehl||`` to the Workspace and name it **warp**.

## Schritt 11
In ``||Player:Bei Chat-Befehl "warp"||``, click the plus sign **(+)** to add a parameter. It is called **num1** by default. This is a variable. This is the number of the location you want to warp to. Recall that in arrays, the number where something is stored is called the index or key. You will pass in the index here through ``||Player:Bei Chat-Befehl "warp"||``. Then you will get the information stored in that location.

## Schritt 12
If you wanted to warp to our third saved location, you would enter **warp 3** in the chat window. The computer goes to the third location and gets your coordinates for you!

You should always name variables something meaningful. Rename **num1** to **Warp_LocationNum**.

## Schritt 13
Drag ``||Player:teleportiere nach||`` into ``||Player:Bei Chat-Befehl "warp"||``.

## Schritt 14
Now we just need to get the information stored in our array. From ``||Arrays:ARRAYS||``, drag ``||Arrays:rufe Wert ab bei||`` into ``||Player:teleportiere nach||`` and replace the existing coordinates block.

### ~ tutorialhint
``` blocks
let warp_array: Position[] = []
player.teleport(warp_array[0])
```

## Schritt 15
From the ``||Arrays:rufe Wert ab bei||`` drop-down menu, select the **warp_array** variable.

Drag **Warp_LocationNum** into the second slot of the ``||Arrays:rufe Wert ab bei||``.

### ~ tutorialhint
``` blocks
let warp_array: Position[] = []
player.onChat("warp", function (Warp_LocationNum) {
    player.teleport(warp_array[Warp_LocationNum])
})
```
## Schritt 16
Now, when you call the warp command with a number, the code will grab the position in the spot you specify. Then you will teleport to the position stored in the array. 

### ~ tutorialhint
``` blocks
let warp_array: Position[] = []
player.onChat("delete", function () {
    warp_array = []
    player.say("Array deleted")
})
player.onChat("save", function () {
    warp_array.push(player.position())
    player.say("position added")
})
player.onChat("warp", function (Warp_LocationNum) {
    player.teleport(warp_array[Warp_LocationNum - 1])
})
warp_array = []
```

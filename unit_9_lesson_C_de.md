### @explicitHints 1
# Aktivität: Tree Hunter 

## Schritt 1
Use the starter code that has been provided. Make the “runchopper” command. Create a ``||Player:Bei Chat-Befehl||`` block and rename it **"runchopper"**.

```template
let flipturn = false
let height = 0
function chop() {
    height = 0
    while (agent.detect(AgentDetection.Block, SixDirection.Forward)) {
        height += 1
        agent.destroy(SixDirection.Up)
        agent.move(SixDirection.Up, 1)
    }
    for (let i = 0; i < height; i++) {
        agent.move(SixDirection.Down, 1)
        agent.destroy(SixDirection.Forward)
    }
    agent.collectAll()
}
function follow() {
    agent.move(SixDirection.Forward, 1)
    if (agent.inspect(AgentInspection.Block, SixDirection.Forward) == blocks.block(Block.Grass)) {
        agent.destroy(SixDirection.Up)
        agent.move(SixDirection.Up, 1)
    } else if (!(agent.detect(AgentDetection.Block, SixDirection.Down))) {
        agent.move(SixDirection.Down, 1)
    } else {
 
    }
}
player.onChat("tp", function () {
    agent.teleportToPlayer()
})
player.onChat("lt", function () {
    agent.turn(TurnDirection.Left)
})
function turn() {
    agent.setAssist(AgentAssist.DetroyObstacles, true)
    if (flipturn) {
        agent.turn(TurnDirection.Right)
        agent.move(SixDirection.Forward, 3)
        agent.turn(TurnDirection.Right)
    } else {
        agent.turn(TurnDirection.Left)
        agent.move(SixDirection.Forward, 3)
        agent.turn(TurnDirection.Left)
    }
    flipturn = !(flipturn)
}
```
## Schritt 2
To determine the size of the area to search, let’s attach a number as a parameter to our "runchopper" command block that will represent the length of one side of the square search area. 

Click the plus sign **(+)** in ``||Player:Bei Chat-Befehl "runchopper"||`` to add the **num1** parameter to our block. Use the dropdown to rename **num1** to **area**.

### ~ tutorialhint
``` blocks
player.onChat("runchopper", function(area) {

})
```

## Schritt 3
Create the “suchen()” function. Let’s create the remaining function that will make up our program. Then at the end we will call all of our functions from ``||Player:Bei Chat-Befehl "runchopper"||``. 

Create a new function and name it: **suchen**.

## Schritt 4
Add logic to the suchen() function. The **suchen()** function, which will have the agent check to see if there are any trees around it. The agent will check to the right, the left, and in front for wood blocks indicating a tree. If it finds a wood block, it will call the *chop()* function to chop the tree down.

## Schritt 5
Drag an ``||Logic:wenn dann ansonsten||`` into ``||Function:Funktion suchen||``.

In the ``||Logic:wenn dann ansonsten||``, click the plus sign **(+)** two times to create two additional ``||Logic:sonst wenn||`` clauses.

## Schritt 6
Look for some wood on the left. Let’s first see if there is a block of wood to the left of the agent.

Drag out a ``||Logic:0 = 0||`` comparison block. Put this comparison into the first conditional slot for the ``||Logic:wenn||`` statement.

## Schritt 7
Drag an ``||Agent:agent untersuche||`` block into the first slot of the ``||Logic:0 = 0||``.

In ``||Agent:agent untersuche||``, use the drop-down menu to select **links** as the direction to inspect.

Drag out a ``||Blocks:block||`` and drop this in the second slot of the ``||Logic:0 = 0||``.

In ``||Blocks:block||``, use the drop-down menu to select an **Oak Wood** block or a type of tree in the area you want to search. 

### ~ tutorialhint
This tests to see if there is Oak Wood and if there is the agent will need to chop it!

``` blocks
function suchen() {
    if (agent.inspect(AgentInspection.Block, LEFT) == LOG_OAK) {

    } else if (0 == 0) {

    } else if (0 == 0) {

    } else {

    }
}
```

## Schritt 8
Chop to the left. From ``||Agent:AGENT||``, put an ``||Agent:Agent, drehe dich nach||`` into the first branch of the ``||Logic:if then||``.

### ~ tutorialhint
If you do find some wood to the left of the agent, then you will want to turn the agent left and call the *chop()* function to chop down the tree. Finally, you will want the agent to turn back around and face forward again.

## Schritt 9
Place a ``||Functions:call function chop||`` under the ``||Agent:Agent, drehe dich nach||``.

Duplicate the ``||Agent:Agent,drehe dich nach||`` and place the copy below ``||Functions:call function chop||``.

In this new ``||Agent:Agent, drehe dich nach||``, use the drop-down menu to select **right**. 

### ~ tutorialhint

``` blocks
function search() {
    if (agent.inspect(AgentInspection.Block, LEFT) == LOG_OAK) {
        agent.turn(TurnDirection.Left)
        chop()
        agent.turn(TurnDirection.Right)
    } else if (false) {

    } else if (false) {

    } else {

    }
}
function chop()  {

}
```

## Schritt 10
Look for wood to chop straight ahead. Now, you want check for wood in front of your agent. In this case, you don’t need to turn the agent.

Click on the first condition we made and duplicate it. Snap the duplicate into the condition slot of the second branch of your ``||Logic:wenn||``.

## Schritt 11
Now just make a few adjustments. In ``||Agent:Agent, untersuche||`` change the direction to **forward**.

Duplicate ``||Functions:Aufruf function chop||`` and place it inside this branch(2nd branch) of the ``||Logic:wenn||``.

### ~ tutorialhint
``` blocks
function search() {
    if (agent.inspect(AgentInspection.Block, LEFT) == LOG_OAK) {
        agent.turn(TurnDirection.Left)
        chop()
        agent.turn(TurnDirection.Right)
    } else if (agent.inspect(AgentInspection.Block, FORWARD) == LOG_OAK) {
        chop()
    } else if (false) {

    } else {

    }
}
function chop() {

}
```

## Schritt 12
Look for wood to chop on the right. Finally, you should see if there is a block of wood to the right of the agent. 

Click on the first condition we made and duplicate it again. Place this in the third branch of the ``||Logic:sonst wenn||``.

### ~ tutorialhint
This is essentially the same as looking to the left but several things will be opposite.


## Schritt 13
Adjust the direction to **right**.

You will need two ``||Agent:Agent,drehe dich nach||`` blocks. Duplicate two and put them inside the third branch.

## Schritt 14
Duplicate ``||Function:Aufruf Funktion chop||`` and place it between the two ``||Agent:Agent,drehe dich nach||`` blocks.

Now, just adjust the turns. This time the agent turns right first, chops, and then turns back to the left.

## Schritt 15
The final else branch of your ``||Logic:wenn||`` will be left blank.

### ~ tutorialhint
``` blocks
function search() {
    if (agent.inspect(AgentInspection.Block, LEFT) == LOG_OAK) {
        agent.turn(TurnDirection.Left)
        chop()
        agent.turn(TurnDirection.Right)
    } else if (agent.inspect(AgentInspection.Block, FORWARD) == LOG_OAK) {
        chop()
    } else if (agent.inspect(AgentInspection.Block, RIGHT) == LOG_OAK) {
        agent.turn(TurnDirection.Right)
        chop()
        agent.turn(TurnDirection.Left)
    } else {

    }
}
function chop() {

}
```

## Schritt 16
Allow the agent to destroy obstacles in its path. The agent has a block that will give it some extra powers that are useful in this case. The block is called set Assist and it is located in the ``||Agent:AGENT||`` Toolbox drawer.

Drag a ``||Agent:setze assist||`` block into ``||Player:Bei Chat-Befehl "runchopper"||``. Use the drop-down menu to select **destroy obstacles**.

### ~ tutorialhint
Check out other cool things this block can do by searching for it in the help! It can allow your agent to place blocks automatically when it moves and also place blocks from any slot in its inventory instead of just using the upper left hand inventory slot.


##Step 17
Finally, select ``||Logic:Wahr||``.

## Schritt 18
Control the agent’s turn direction. You need the agent to turn around at the end of each row. 

Let’s create a Boolean variable to keep track of which direction to turn. We’ll use ``||Logic:Wahr||`` to denote a Right turn and ``||Logic:Falsch||`` to represent a Left turn. After we make our turn, we’ll switch the boolean variable.

The variable **flipturn** was created as part of the starter code at the beginning of this activity. This is meant to be your Boolean variable.

Drag a ``||Variables:setze||`` block into ``||Player:Bei Chat-Befehl "runchopper"||``. Use the drop-down menu to select **flipturn**

## Schritt 19
Drag a ``||Logic:Falsch||`` block into the set and replace the **0**.

### ~ tutorialhint
``` blocks
let flipturn = false
player.onChat("runchopper", function (area) {
    agent.setAssist(DESTROY_OBSTACLES, true)
    flipturn = false;
})
```

## Schritt 20
We have everything in place. Now we just need to build it out. To move the agent through its search you will: Get the agent to move down one row of the grid, Turn at the end, then Continue going down rows until the square area is complete.

## Schritt 21
Put *search()* and *follow()* into the chat command. Now that we have all our functions built, let’s bring it all together. For each step, we want our agent to Search for trees, and follow the ground terrain. By searching the agent will be actually searching three rows at a time because it searches left, right, and forward with each step.

## Schritt 22
Drag a ``||Loops:-mal wiederholen||`` block into ``||Player:Bei Chat-Befehl "runchopper"||``. Place this below ``||Variables:setze flipturn||`` block.

## Schritt 23
Remember, that the **area** parameter is the number of blocks in each row. Drag ``||Variables:area||`` into the ``||Loops:-mal wiederholen||`` block replacing the default **4**.

Now the agent will search for all the blocks in one row, how ever many the user specifies. Drag the ``||Functions:Aufruf Funktion search||``, and the ``||Functions:Aufruf Funktion follow||`` blocks into the **repeat loop**.

### ~ tutorialhint
``` blocks
let area = 0
let flipturn = false
player.onChat("runchopper", function (area) {
    agent.setAssist(DESTROY_OBSTACLES, true)
    flipturn = false
    for (let i = 0; i < area; i++) {
        search()
        follow()
    }
})
function search() {

}
function follow() {

}
```

## Schritt 24
Add the *turn()* function to turn at the end of a row. Now, at the end of each row, we want to turn our agent around. Drag the ``||Functions:Aufruf Funktion turn||`` and place this underneath the ``||Loops:-mal wiederholen||`` loop.

### ~ tutorialhint
``` blocks
let flipturn = false
player.onChat("runchopper", function (area) {
    agent.setAssist(DESTROY_OBSTACLES, true)
    flipturn = false
    for (let i = 0; i < area; i++) {
        search()
        follow()
    }
    turn()
})
function search() {

}
function follow() {

}
function turn() {

}
```

## Schritt 25
Complete a Square Search Grid. You will need to add one more ``||Loops:SCHLEIFEN||``, so the agent searches the complete grid and completes the square instead of just searching three rows.

## Schritt 26
Because the agent is searching three blocks every step, it will not need to loop for the full area given. We would divide the area given by 3. In the example below, the agent is searching a 9x9 grid but as you can see it only needs to walk down the rows 3 times to do so.

With that said, you need a ``||Loops:SCHLEIFEN||`` to handle this. Drag another ``||Loops:-mal wiederholen||`` loop out on the workspace. This new ``||Loops:-mal wiederholen||`` loop should enclose everything below ``||Variables:set flipturn||``.

## Schritt 27
Drag a ``||Math:0 ÷ 0 ||``block into the ``||Loops:-mal wiederholen||`` loop replacing the default **4**.

## Schritt 28
Drag ``||Variables:area||`` into the first slot of the ``||Math:0 ÷ 0||``.

In the ``||Math:area ÷ 0||`` block, type **3** in the second slot. 

To test this out be sure you first teleport your agent to your location using the provided ``||Player:Bei Chat-Befehl "tp"||`

### ~ tutorialhint
``` blocks
let flipturn = false
let height = 0
player.onChat("tp", function () {
    agent.teleportToPlayer()
})
player.onChat("lt", function () {
    agent.turn(TurnDirection.Left)
})
player.onChat("runchopper", function (area) {
    agent.setAssist(DESTROY_OBSTACLES, true)
    flipturn = false
    for (let i = 0; i < area / 3; i++) {
        for (let i = 0; i < area; i++) {
            search()
            follow()
        }
        turn()
    }
})
function search() {
    if (agent.inspect(AgentInspection.Block, LEFT) == LOG_OAK) {
        agent.turn(TurnDirection.Left)
        chop()
        agent.turn(TurnDirection.Right)
    } else if (agent.inspect(AgentInspection.Block, FORWARD) == LOG_OAK) {
        chop()
    } else if (agent.inspect(AgentInspection.Block, RIGHT) == LOG_OAK) {
        agent.turn(TurnDirection.Right)
        chop()
        agent.turn(TurnDirection.Left)
    } else {

    }
}
function follow() {
    agent.move(FORWARD, 1)
    if (agent.inspect(AgentInspection.Block, FORWARD) == GRASS) {
        agent.destroy(UP)
        agent.move(UP, 1)
    } else if (!(agent.detect(AgentDetection.Block, DOWN))) {
        agent.move(DOWN, 1)
    } else {

    }
}
function turn() {
    agent.setAssist(DESTROY_OBSTACLES, true)
    if (flipturn) {
        agent.turn(TurnDirection.Right)
        agent.move(FORWARD, 3)
        agent.turn(TurnDirection.Right)
    } else {
        agent.turn(TurnDirection.Left)
        agent.move(FORWARD, 3)
        agent.turn(TurnDirection.Left)
    }
    flipturn = !(flipturn)
}
function chop() {
    height = 0
    while (agent.detect(AgentDetection.Block, FORWARD)) {
        height += 1
        agent.destroy(UP)
        agent.move(UP, 1)
    }
    for (let i = 0; i < height; i++) {
        agent.move(DOWN, 1)
        agent.destroy(FORWARD)
    }
    agent.collectAll()
}
```

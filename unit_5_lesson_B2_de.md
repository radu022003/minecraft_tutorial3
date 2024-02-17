### @explicitHints 1

# Aktivität: Agent Baumfäller

## Schritt 1
Ändern Sie den vorhandenen ``||Player:Bei Chat-Befehl||`` in **"tp"** um.
Ziehen Sie einen ``||Agent:Agent teleportiere zu Spieler||`` Block in den ``||Player:Bei Chat-Befehl "tp"||`` Block.

## Schritt 2
Jetzt erstellen wir auch einen Richtungsbefehl, damit wir unseren Agenten umdrehen können. Sie können mit der rechten Maustaste auf ``||Player:Bei Chat-Befehl "tp"||`` klicken und **Duplizieren** auswählen, um eine Kopie zu erstellen.

Benennen Sie die Duplikate in **"ld"** um.

## Schritt 3
Löschen Sie den inneren Block für diese neue Kopie und ersetzen Sie ``||Agent:Agent teleportiere zu Spieler||`` durch ``||Agent:agent drehe dich nach 'links'||``.

### ~ tutorialhint
``` blocks
player.onChat("tp", function () {
    agent.teleportToPlayer()
})
player.onChat("ld", function () {
    agent.turn(TurnDirection.Left)
})
```

## Schritt 4
Erstellen Sie die Höhenvariable. Ziehen Sie einen ``||Player:Bei Chat-Befehl||``-Block in den Arbeitsbereich und benennen Sie ihn um in **"hacken"**.

Sie werden eine Variable verwenden, um die Höhe des Baumes zu verfolgen. Klicken Sie im Bereich ``||Variables:VARIABLE||`` auf die Schaltfläche **Erstelle eine Variable**. Benennen Sie die neue Variable **Hoehe**.

## Schritt 5
Ziehen Sie ``||Variables:setze auf||`` heraus und platzieren Sie es innerhalb von ``||Player:Bei Chat-Befehl "hacken"||``.

## Schritt 6
Im ``||Variables:setze auf||`` Block wählen Sie aus dem Dropdown-Menü **Hoehe** als Variable aus und setzen Sie **Hoehe** auf **0**.

### ~ tutorialhint
``` blocks
let Hoehe = 0
player.onChat("tp", function () {
    agent.teleportToPlayer()
})
player.onChat("ld", function () {
    agent.turn(TurnDirection.Left)
})
player.onChat("hacken", function () {
    Hoehe = 0
})
```

## Schritt 7

Beginnen Sie am Fuß eines Baumes. Nehmen Sie an, dass der Agent in Richtung des Baumstamms platziert ist, wenn der Befehl zum Hacken gegeben wird. Verwenden Sie die Befehle "tp" und "ld", um Ihren Agenten an die richtige Stelle zu bringen, und schließlich "hacken". Verwenden Sie eine ``||Loops:während||``-Schleife, die wie eine Kombination aus einer ``||Loops:-mal wiederholen||``-Schleife und einer bedingten Anweisung ist. Der Code wird so lange fortgesetzt, wie sich ein Block vor dem Agenten befindet. Wenn sich ein Block vor dem Agenten befindet, wird er weiter den Baum hinauf bewegt.

## Schritt 8
Ziehen Sie eine ``||Loops:während||``-Schleife heraus und legen Sie sie unter ``||Variables:setze auf 'Hoehe'||`` ab. Dies sollte innerhalb von ``||Player:Bei Chat-Befehl "hacken"||`` sein.

## Schritt 9
Ziehen Sie ``||Agent:agent untersuche 'Block' 'vorwärts'||`` heraus und legen Sie es in die ``||Loops:während||``-Schleife, wobei Sie ``||Logic:wahr||`` ersetzen.

### ~ tutorialhint
``` blocks
let Hoehe = 0
player.onChat("tp", function () {
    agent.teleportToPlayer()
})
player.onChat("ld", function () {
    agent.turn(TurnDirection.Left)
})
player.onChat("hacken", function () {
    Hoehe = 0
    while (agent.detect(AgentDetection.Block, FORWARD)) {

    }
})
```

## Schritt 10
Verschieben Sie sich den Baum hinauf und hacken Sie. Platzieren Sie einen ``||Variables:ändere um||``-Block innerhalb der ``||Loops:während||``-Schleife.

Der neue Block sollte wie folgt lauten: ``||Variables:ändere 'Höhe' um 1||``. Dadurch wird die Höhenvariable jedes Mal um 1 erhöht, wenn der Agent nach oben bewegt wird. Auf diese Weise können wir die Höhe des Baumes verfolgen.

## Schritt 11
Wenn Blätter oder Äste über dem Kopf des Agenten sind, müssen sie zerstört werden, um den Agenten nach oben zu bewegen. Platzieren Sie einen ``||Agent: agent zerstöre||``-Block unterhalb des ``||Variables:ändere 'Höhe' um 1||``-Blocks. Sie müssen diesen Block anpassen, indem Sie **nach oben** als Richtung aus dem Dropdown-Menü auswählen.

## Schritt 12
Finally, get your agent to move up. Grab an ``||Agent:agent bewege dich||`` block, and then use the drop-down menu to select up as the **Direktion** like you did in the previous step.Schließlich lassen Sie Ihren Agenten nach oben gehen. Nehmen Sie einen ``||Agent:agent bewege dich||``-Block und wählen Sie dann wie im vorherigen Schritt die Option **nach oben** aus dem Dropdown-Menü aus.

### ~ tutorialhint
``` blocks
let Hoehe = 0
player.onChat("tp", function () {
    agent.teleportToPlayer()
})
player.onChat("ld", function () {
    agent.turn(TurnDirection.Left)
})
player.onChat("hacken", function () {
    Hoehe = 0
    while (agent.detect(AgentDetection.Block, FORWARD)) {
        Hoehe += 1
        agent.destroy(UP)
        agent.move(UP, 1)
    }
})
```

## Schritt 13
Kommen Sie wieder nach unten. Ziehen Sie eine ``||Loops:-mal wiederholen||``-Schleife heraus und lassen Sie sie nach der ``||Loops:während||``-Schleife in Ihrem ``||Player:Bei Chat-Befehl "hacken"||`` fallen.

## Schritt 14
Ziehen Sie die Höhe heraus und ersetzen Sie die **4** in der ``||Loops:-mal wiederholen||``-Schleife.

### ~ tutorialhint
``` blocks
let Hoehe = 0
player.onChat("tp", function () {
    agent.teleportToPlayer()
})
player.onChat("ld", function () {
    agent.turn(TurnDirection.Left)
})
player.onChat("hacken", function () {
    Hoehe = 0
    while (agent.detect(AgentDetection.Block, FORWARD)) {
        Hoehe += 1
        agent.destroy(UP)
        agent.move(UP, 1)
    }
    for (let i = 0; i < Hoehe; i++) {

    }
})
```

## Schritt 15
Hacken, während Sie fallen. Zu diesem Zeitpunkt sollte der Agent oben auf einem Baum stehen. Sie müssen ihn dazu bringen, wieder hinunterzuklettern, den Baum zu fällen und das Holz zu sammeln. Platzieren Sie ein ``||Agent:agent bewege dich||`` und ``||Agent:agent zerstöre||`` innerhalb der ``||Loops:-mal wiederholen||``-Schleife.

## Schritt 16
Jetzt müssen Sie diese Blöcke für die Situation anpassen. Der Agent muss sich **nach unten** bewegen und jedes Stück des Baumes, das **vorwärts** liegt, fällen. Wählen Sie im ``||Agent:agent bewege dich||``-Block die Richtung **nach unten** aus. Der Agent wird sich nach unten bewegen. Dann sollte der Agent den Baumblock vor sich zerstören. Die Standardeinstellungen sind für ``||Agent:zerstöre||`` in Ordnung.

## Schritt 17
Schließlich möchten Sie, dass Ihr Agent das gesamte gefällte Holz sammelt. Platzieren Sie ein ``||Agent:agent sammle alles||`` nach der ``||Loops:-mal wiederholen||``-Schleife. Dies ist nun der letzte Block in unserem ``||Player:Bei Chat-Befehl||`` für **"hacken"**.

### ~ tutorialhint
``` blocks 
let Hoehe = 0
player.onChat("tp", function () {
    agent.teleportToPlayer()
})
player.onChat("ld", function () {
    agent.turn(TurnDirection.Left)
})
player.onChat("hacken", function () {
    Hoehe = 0
    while (agent.detect(AgentDetection.Block, FORWARD)) {
        Hoehe += 1
        agent.destroy(UP)
        agent.move(UP, 1)
    }
    for (let i = 0; i < Hoehe; i++) {
        agent.move(DOWN, 1)
        agent.destroy(FORWARD)
    }
    agent.collectAll()
})
```

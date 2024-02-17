### @explicitHints 1

# Aktivität: Alles meins!

## Schritt 1
Erstellen Sie Steuerelemente für den Agenten. Benennen Sie das vorhandene ``||Player:Bei Chat-Befehl||`` in **mach** um.

## Schritt 2
Sie können ein einfaches Menü erstellen, um alle Agentenbefehle zu verarbeiten. Ziehen Sie ein ``||Logic:wenn dann ansonsten||`` in ``||Player:Bei Chat-Befehl "mach"||``. Klicken Sie auf das **(+)** -Symbol auf dem ``||Logic:wenn dann ansonsten||``, um einen dritten Zweig hinzuzufügen, da Sie drei Bedingungen überprüfen werden.

## Schritt 3
Klicken Sie auf das **(+)**-Symbol bei ``||Player:Bei Chat-Befehl "mach"||`` und benennen Sie **num1** in **AgentOrder** um.

### ~ tutorialhint
``` blocks
player.onChat("mach", function (AgentOrder) {
    if (true) {

    } else if (false) {

    } else {

    }
})
```

## Schritt 4
Jetzt überprüfen Sie einfach, was der Benutzer eingegeben hat. Sie möchten, dass der Benutzer den Agenten teleportieren und drehen kann. Der dritte Zweig gibt dem Benutzer einige Informationen, wenn nichts eingegeben wird. Nehmen Sie den Vergleichsblock **'0 = 0'** und duplizieren Sie ihn, da Sie zwei benötigen.

Platzieren Sie diese in den ``||Logic:wenn dann ansonsten||`` Block.

## Schritt 5
Passen Sie diese an, damit Sie testen, was der Benutzer eingegeben hat. Wir müssen den Wert von ``||Variables:AgentOrder||`` überprüfen. Angenommen, ein Wert von **1** bedeutet, dass der Agent teleportiert wird, und ein Wert von **2** bedeutet, dass der Agent sich drehen soll.


### ~ tutorialhint
``` blocks
player.onChat("mach", function (AgentOrder) {
    if (AgentOrder == 1) {

    } else if (AgentOrder == 2) {

    } else {

    }
})

```

## Schritt 6
Zuletzt müssen Sie nur noch Blöcke zu den Zweigen hinzufügen, damit Ihr Agent die Aktionen ausführt. Fügen Sie einen ``||Agent: Agent teleportiere zu Spieler||``-Block in den ersten Zweig Ihres ``||Logik: wenn dann ansonsten||`` ein.

## Schritt 7
Fügen Sie einen ``||Agent: Agent drehe dich nach||``-Block in den zweiten Zweig Ihres ``||Logik: wenn dann ansonsten||`` ein.

## Schritt 8
Im letzten Zweig fügen Sie eine Nachricht hinzu, um dem Benutzer Anweisungen zu geben. Fügen Sie eine ``||Player: sag||``-Anweisung dem dritten Zweig Ihres ``||Logic: wenn dann ansonsten||``-Blocks hinzu.

## Schritt 9
Passen Sie den Text in der ``||Player:sag||``-Anweisung so an, dass er lautet: **Geben Sie 1 ein, um zu teleportieren, oder 2, um sich zu drehen**.

## Schritt 10
Erstelle den Befehl "grabe". Platziere einen ``||Player:Bei Chat-Befehl||``-Block im Programmierbereich und benenne ihn in **"grabe"** um.

## Schritt 11
Du kannst Diamanten nur im Überlebensmodus abbauen, daher solltest du als Erstes sicherstellen, dass du den Spielmodus auf Überleben änderst. Platziere ``||Gameplay:ändere Spielmodus zu||`` in den ``||Player:Bei Chat-Befehl "grabe"||`` Block.

## Schritt 12
Passe ``||Gameplay:ändere Spielmodus zu||`` an, indem du das Dropdown-Menü für die Spielerauswahl anklickst und **du selbst @s** auswählst.

## Schritt 13
Ziehen Sie ein ``||Logic:wenn dann ansonsten||`` heraus und platzieren Sie es nach dem Block ``||Gameplay:ändere Spielmodus zu||``.


### ~ tutorialhint
``` blocks
player.onChat("grabe", function () {
    gameplay.setGameMode(
    SURVIVAL,
    mobs.target(LOCAL_PLAYER)
    )
    if (true) {
    } else {
    }
})
```

## Schritt 14
Suchen Sie nach Diamanten. Sie möchten einen Alarm auslösen, wenn der Agent wertvolle Blöcke wie Diamanterz findet. Greifen Sie einen **Gleichheit (=)** Vergleichsblock, um das **wahr** in Ihrem ``||Logic:wenn dann ansonsten||`` zu ersetzen.

## Schritt 15
Ziehen Sie einen ``||Agent: Agent untersuche||`` in den ersten Slot des **Gleichheits**-Blocks, ``||Logic: 0 = 0||``, und ersetzen Sie die Zahl **0**. Der Block ``||Agent: Agent untersuche||`` wird den Block direkt vor dem Agenten überprüfen.

Ziehen Sie einen ``||Blocks:Block||`` heraus und lassen Sie ihn in den zweiten Steckplatz des **Gleichheits**-Blocks, ``||Logic: 0 = 0||``, fallen.

In ``||Blocks:Block||``, verwenden Sie das Dropdown-Menü, um **Diamant-Erz** als den Block auszuwählen, den Sie überprüfen möchten.


### ~ tutorialhint
``` blocks
player.onChat("grabe", function () {
    gameplay.setGameMode(
    SURVIVAL,
    mobs.target(LOCAL_PLAYER)
    )
    if (agent.inspect(AgentInspection.Block, FORWARD) == DIAMOND_ORE) {

    } else {

    }
})
```

## Schritt 16
Werde reich! Wenn du tatsächlich **Diamant-Erz** findest, möchtest du eine Nachricht auf dem Bildschirm anzeigen und das Erz abbauen. Ziehe dazu ``||Player:sage||`` und platziere es im ersten Zweig des ``||Logic:wenn dann ansonsten||``-Blocks.

Im ``||Player:sage||``-Block gib die Nachricht **Wir sind reich!** ein.

## Schritt 17
Ziehe die folgenden drei Blöcke und platziere sie der Reihe nach unter dem ``||Player:sage||``-Block: ``||Agent:agent zerstöre||``, ``||Agent:agent bewege dich||`` und ``||Agent:agent sammle alles||``.

### ~ tutorialhint
``` blocks
player.onChat("grabe", function () {
    gameplay.setGameMode(
    SURVIVAL,
    mobs.target(LOCAL_PLAYER)
    )
    if (agent.inspect(AgentInspection.Block, FORWARD) == DIAMOND_ORE) {
        player.say("Wir sind reich!")
        agent.destroy(FORWARD)
        agent.move(FORWARD, 1)
        agent.collectAll()
    } else {
    }
})
```

## Schritt 18
Zerstöre die anderen Blöcke und mach weiter mit dem Abbau. Wenn der Agent kein Diamanterz findet, sollte er einfach den wertlosen Block vor ihm zerstören und sich vorwärts bewegen, ohne etwas zu sammeln. Ziehe ``||Agent:agent zerstöre||`` und ``||Agent:agent bewege dich||`` aus ``||Agent:AGENT||`` in die ``||Logik:ansonsten||``-Klausel.

## Schritt 19
Du musst diesen Vorgang **64** Mal wiederholen, daher verwendest du eine Schleife. Ziehe eine ``||Loops:wiederhole||``-Schleife heraus und umschließe damit deinen ``||Logic:wenn dann ansonsten||``-Block.

In der ``||Loops:-mal wiederhole||`` Schleife gib die Zahl **64** ein.

### ~ tutorialhint
``` blocks
player.onChat("grabe", function () {
    gameplay.setGameMode(
    SURVIVAL,
    mobs.target(LOCAL_PLAYER)
    )
    for (let i = 0; i < 64; i++) {
        if (agent.inspect(AgentInspection.Block, FORWARD) == DIAMOND_ORE) {
            player.say("Wir sind reich!")
            agent.destroy(FORWARD)
            agent.move(FORWARD, 1)
            agent.collectAll()
        } else {
            agent.destroy(FORWARD)
            agent.move(FORWARD, 1)
        }
    }
})
```

## Schritt 20
Machen Sie eine Rückfahrt. Dadurch wird Ihr Agent vorwärts geschickt, um **64** Blöcke abzubauen, aber Sie müssen ihn umdrehen und zurückkommen lassen. Daher verwenden Sie eine weitere Schleife außerhalb Ihrer bestehenden ``||Loops:64-mal wiederholen||`` Schleife. Sie erstellen eine "geschachtelte Schleife", weil es eine Schleife innerhalb einer Schleife geben wird. Ziehen Sie eine weitere ``||Loops:-mal wiederholen||`` Schleife heraus und umgeben Sie Ihre bestehende ``||Loops:64-mal wiederholen ||`` Schleife.

## Schritt 21
In der ``||Loops:-mal wiederholen||``-Schleife geben Sie die Zahl **2** ein, da Sie möchten, dass Ihr Agent nur zwei Reihen von Blöcken abbaut. Am Ende der ersten Reihe möchten Sie, dass Ihr Agent nach oben geht und sich umdreht.

## Schritt 22
Ziehen Sie die folgenden vier Blöcke heraus und platzieren Sie sie in der angegebenen Reihenfolge unter der inneren ``||Loops:-mal wiederholen||``-Schleife: ``||Agent:agent zerstöre||``, ``||Agent:agent bewege dich||`` und zwei ``||Agent:agent drehe dich nach||``-Blöcke. Platzieren Sie sie hier, um Ihren Agenten für die Rückkehr zu positionieren. Sie müssen die Richtung für einige dieser Blöcke anpassen, indem Sie das Dropdown-Menü verwenden und nach oben auswählen.


### ~ tutorialhint
``` blocks 
player.onChat("grabe", function () {
    gameplay.setGameMode(
    SURVIVAL,
    mobs.target(LOCAL_PLAYER)
    )
    for (let i = 0; i < 2; i++) {
        for (let i = 0; i < 64; i++) {
            if (agent.inspect(AgentInspection.Block, FORWARD) == DIAMOND_ORE || agent.inspect(AgentInspection.Block, FORWARD) == GOLD_ORE) {
                player.say("Wir sind reich!")
                agent.destroy(FORWARD)
                agent.move(FORWARD, 1)
                agent.collectAll()
            } else {
                agent.destroy(FORWARD)
                agent.move(FORWARD, 1)
            }
        }
        agent.destroy(UP)
        agent.move(UP, 1)
        agent.turn(TurnDirection.Left)
        agent.turn(TurnDirection.Left)
    }
})
```



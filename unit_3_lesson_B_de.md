 ### @explicitHints 1
 
 # Activität: Minecraft-Umzugsunternehmen

## Schritt 1
Ziehe drei ``||Player:bei Chat-Befehl||``-Blöcke in den Arbeitsbereich.

Ändere die Namen dieser ``||Player:bei Chat-Befehl||``-Blöcke in **start**, **stop** und **kopieren**.

### ~ tutorialhint
```blocks
player.onChat("start", function () { })
player.onChat("stop", function () { })
player.onChat("kopieren", function () { })
```

## Schritt 2
Erstelle die Variablen. Öffne ``||Variables:VARIABLEN||`` und klicke auf die Schaltfläche **Erstelle eine Variable**.

Nenne die Variable **start** und klicke auf **Ok**.

## Schritt 3
Erstelle eine weitere Variable und nenne sie **stop**, und klicke auf **Ok**.

## Schritt 4
Setze die Variablen. Platziere einen ``||Variables:setze||``-Block in ``||Player:Bei Chat-Befehl||`` für "start".

Verwende das Dropdown-Menü und wähle die ``||Variables:start||`` aus.

## Schritt 5
Setze die Startposition auf die ``||Player:Position des Spielers in der Welt||``. Ziehe ``||Player:Position des Spielers in der Welt||`` in ``||Variables:setze start||`` um die **0** zu ersetzen.

### ~ tutorialhint
```blocks
let start: Position = null
player.onChat("start", function () {
    start = player.position()
})
```
## Schritt 6
Schreibe Nachrichten. Füge einen ``||Player:sag||``-Block nach ``||Variables:setze start||`` hinzu.

### ~ tutorialhint
```blocks
let start: Position = null
player.onChat("start", function () {
    start = player.position()
    player.say(":)")
})
```

## Schritt 7
Öffne ``||Text:TEXT||`` und platziere ``||Text:verbinde||`` im ``||Player:sag||``-Block, ersetze **":)"**.

Im ersten Feld von ``||Text:verbinde||`` gib **"Startpunkt"** ein.

``||Text:TEXT||`` befindet sich im **FORGESCHRITTEN**.

## Schritt 8
Öffne als nächstes ``||VARIABLES: VARIABLEN||`` und ziehe ``||Variables: start||`` in das zweite Feld des ``||Text:verbinde||``-Blocks.

### ~ tutorialhint
```blocks
let start: Position = null
player.onChat("start", function () {
    start = player.position()
    player.say("Startpunkt: " + start)
})

```

## Schritt 9
Wiederhole dies für den Stop-Befehl. Klicke mit der rechten Maustaste auf ``||Player:Bei Chat-Befehl||`` **"start"** und dupliziere es. Benenne den ``||Player:Bei Chat-Befehl||`` Befehl in **stop** um.

Ändere den Text des ``||Player:sag||``-Blocks in **"Stoppunkt"**. Füge eine ``||Variables: stop||``-Variable in den ``||Text:verbinde||``-Block ein.

### ~ tutorialhint
``` blocks
let stop: Position = null
player.onChat("stop", function () {
    stop = player.position()
    player.say("Stoppunkt: " + stop)
})
```

## Schritt 10
Lösche die leeren ``||Player:Bei Chat-Befehl||``-Blöcke für **"stop"** und **"kopieren"**.

## Schritt 11
Erstelle den Kopier-Befehl. Öffne ``||Blocks:BLÖCKE||`` und ziehe den ``||Blocks:klone||``-Block in den Block mit der Bezeichnung **"kopieren"**.

### ~ tutorialhint
``` blocks
player.onChat("kopieren", function () {
    blocks.clone(
    pos(0, 0, 0),
    pos(0, 0, 0),
    pos(0, 0, 0),
    CloneMask.Replace,
    CloneMode.Normal
    )
})
```

## Schritt 12
Ziehe ``||Variables:start||`` in den ersten Slot des ``||Blocks:klone||``-Blocks. Dein Block sollte jetzt **klonen von start** lauten.

## Schritt 13
From ``||Variables:VARIABLEN||``, ziehe ``||Variables:stop||`` in den zweiten Slot des ``||Blocks:klone||``-Blocks. Dein Block sollte jetzt **klonen von start bis stop** lauten.

### ~ tutorialhint
```blocks
player.onChat("kopieren", function () {
    let stop: Position = null
    let start: Position = null
    blocks.clone(
    start,
    stop,
    pos(0, 0, 0),
    CloneMask.Replace,
    CloneMode.Normal
    )
})
```

## Schritt 14
Teste deinen Code in Minecraft. Baue zuerst ein Haus oder eine Struktur, die du kopieren möchtest. Gehe zu einer der unteren Ecken der Struktur und gib im Chat den Befehl "start" ein.

## Schritt 15
Bewege deinen Spieler diagonal zur oberen Ecke vom Startpunkt. Im Chatfenster gib den Befehl "stop" ein.
Versetze deinen Spieler an einen freien Platz in der Welt, an dem du die Struktur kopieren möchtest, und gib im Chatfenster den Befehl "kopieren" ein.
Hat es dein Haus oder deine Struktur korrekt kopiert?

### ~ tutorialhint
``` blocks
let start: Position = null
let stop: Position = null
player.onChat("start", function () {
    start = player.position()
    player.say("Starting Point Set: " + start)
})
player.onChat("copy", function () {
    blocks.clone(
    start,
    stop,
    pos(0, 0, 0),
    CloneMask.Replace,
    CloneMode.Normal
    )
})
player.onChat("stop", function () {
    stop = player.position()
    player.say("Stopping Point Set: " + stop)
})
```

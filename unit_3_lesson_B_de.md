### @explicitHints 1

# Aktivität: Minecraft-Umzugsunternehmen

## Schritt 1
Ziehe drei ``||PLAYER:bei Chat-Befehl||``-Blöcke in den Arbeitsbereich.

Ändere die Namen dieser ``||PLAYER:bei Chat-Befehl||``-Blöcke in **start**, **stop** und **kopieren**.

### ~ tutorialhint
```blocks
player.onChat("start", function () { })
player.onChat("stop", function () { })
player.onChat("kopieren", function () { })
```

## Schritt 2
Erstelle die Variablen. Öffne ``||VARIABLEN:VARIABLEN||`` und klicke auf die Schaltfläche **Erstelle eine Variable**.

Nenne die Variable **start** und klicke auf **Ok**.

## Schritt 3
Erstelle eine weitere Variable und nenne sie **stop**, und klicke auf **Ok**.

## Schritt 4
Setze die Variablen. Platziere einen ``||VARIABLEN:setze||``-Block in ``||PLAYER:Bei Chat-Befehl||`` für "start".

Verwende das Dropdown-Menü und wähle die ``||VARIABLEN:start||`` aus.

## Schritt 5
Setze die Startposition auf die ``||PLAYER:Position des Spielers in der Welt||``. Ziehe ``||PLAYER:Position des Spielers in der Welt||`` in ``||VARIABLEN:setze start||`` um die **0** zu ersetzen.

### ~ tutorialhint
```blocks
let start: Position = null
player.onChat("start", function () {
    start = player.position()
})
```
## Schritt 6
Schreibe Nachrichten. Füge einen ``||PLAYER:sag||``-Block nach ``||VARIABLEN:setze start||`` hinzu.

### ~ tutorialhint
```blocks
let start: Position = null
player.onChat("start", function () {
    start = player.position()
    player.say(":)")
})
```

## Schritt 7
Als Nächstes öffne ``||TEXT:TEXT||`` und platziere ``||TEXT:verbinde||`` im ``||PLAYER:sag||``-Block, ersetze **":)"**.

Im ersten Feld von ``||TEXT:verbinde||`` gib **"Startpunkt"** ein.

``||TEXT:TEXT||`` befindet sich im **FORTGESCHRITTEN**.

## Schritt 8
Öffne als nächstes ``||VARIABLES: VARIABLEN||`` und ziehe ``||VARIABLEN: start||`` in das zweite Feld des ``||TEXT:verbinde||``-Blocks.

### ~ tutorialhint
```blocks
let start: Position = null
player.onChat("start", function () {
    start = player.position()
    player.say("Startpunkt: " + start)
})

```

## Schritt 9
Wiederhole dies für den Stop-Befehl. Klicke mit der rechten Maustaste auf ``||PLAYER:Bei Chat-Befehl||`` **"start"** und dupliziere es. Benenne den ``||PLAYER:Bei Chat-Befehl||``-Befehl in **stop** um.
Lösche dann den leeren ``||PLAYER:Bei Chat-Befehl||``-Block für **"stop"**.

Ändere den Text des ``||PLAYER:sag||``-Blocks in **"Stoppunkt"**. Füge eine ``||VARIABLEN: stop||``-Variable in den ``||TEXT:verbinde||``-Block ein.

### ~ tutorialhint
``` blocks
let stop: Position = null
player.onChat("stop", function () {
    stop = player.position()
    player.say("Stoppunkt: " + stop)
})
```

## Schritt 10
Erstelle den Kopier-Befehl. Öffne ``||BLOCKS:BLÖCKE||`` und ziehe den ``||BLOCKS:klone||``-Block in den Block mit der Bezeichnung **"kopieren"**.

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

## Schritt 11
Ziehe ``||VARIABLEN:start||`` in den ersten Slot des ``||BLOCKS:klone||``-Blocks. Dein Block sollte jetzt **klonen von start** lauten.

## Schritt 12
Ziehe ``||VARIABLEN:stop||`` in den zweiten Slot des ``||BLOCKS:klone||``-Blocks. Dein Block sollte jetzt **klonen von start bis stop** lauten.

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

## Schritt 13
Teste deinen Code in Minecraft. Baue zuerst ein Haus oder eine Struktur, die du kopieren möchtest. Gehe zu einer der unteren Ecken der Struktur und gib im Chat den Befehl "start" ein.

## Schritt 14
Bewege deinen Spieler diagonal zur oberen Ecke vom Startpunkt. Im Chatfenster gib den Befehl "stop" ein.
Versetze deinen Spieler an einen freien Platz in der Welt, an dem du die Struktur kopieren möchtest, und gib im Chatfenster den Befehl "kopieren" ein.
Hat es dein Haus oder deine Struktur korrekt kopiert?

### ~ tutorialhint
``` blocks
let start: Position = null
let stop: Position = null
player.onChat("start", function () {
    start = player.position()
    player.say("Startpunkt: " + start)
})
player.onChat("kopieren", function () {
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
    player.say("Stoppunkt: " + stop)
})
```

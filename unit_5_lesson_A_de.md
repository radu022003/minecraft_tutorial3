### @explicitHints 1

# Aktivität: Wie alt bist du?

---

## Schritt 1
Benenne den vorhandenen ``||Player:bei Chat-Befehl "run"||``-Block in **"alter"** um.

Klicke auf das Plus **(+)**-Symbol im ``||Player:bei Chat-Befehl "alter"||``, um einen **num1**-Variablenparameter zu erstellen.

Benenne **num1** in **Alter** um. Das macht deinen Code lesbarer. Verwende immer aussagekräftige Namen für Variablen, um das Auffinden von Fehlern zu erleichtern. Du kannst Variablen über das Dropdown-Menü umbenennen.

### ~ tutorialhint
```blocks
player.onChat("alter", function (Alter) {

})
```

---

## Schritt 2
Verwende eine Bedingung. Ziehe einen ``||Logic:wenn ... dann ... ansonsten||``-Block in den ``||Player:bei Chat-Befehl "alter"||``-Block.

Klicke auf das Plus **(+)**-Symbol im ``||Logic:wenn ... dann ... ansonsten||``-Block, um einen zusätzlichen ``||Logic:sonst wenn ... dann||``-Zweig zu erstellen.

---

## Schritt 3
Füge Vergleiche ein. Ziehe einen **kleiner als**, ``||Logic:0 < 0||``, Vergleichsblock in den ``||Logic:wenn||``-Platz und ersetze **wahr**.

---

## Schritt 4
Ziehe einen **gleich wie**, ``||Logic:0 = 0||``, Vergleichsblock in den ``||Logic:sonst wenn ... dann||``-Platz.

### ~ tutorialhint
```blocks
player.onChat("alter", function (Alter) {
    if (0 < 0) {
    } else if (0 == 0) {
    } else {
    }
})
```

---

## Schritt 5
Vergleiche mit deiner Variablen. Ziehe zwei ``||Variables:Alter||``-Blöcke in den ersten Platz jedes Vergleichsblocks.

Gib im zweiten Slot der Vergleichsblöcke dein Alter ein (z. B. **12**).

### ~ tutorialhint
```blocks
player.onChat("alter", function (Alter) {
    if (Alter < 12) {

    } else if (Alter == 12) {

    } else {

    }
})
```

---

## Schritt 6
Füge Schreibblöcke für jede Bedingung ein. Ziehe einen ``||Blocks:schreibe "HELLO"||``-Block in deinen Arbeitsbereich. Rechtsklicke auf diesen Block und wähle **Duplizieren**, um Kopien zu erstellen.

Platziere je einen in den ``||Logic:wenn ... dann||``, ``||Logic:sonst wenn ... dann||`` und ``||Logic:ansonsten||``-Abschnitten.

### ~ tutorialhint
```blocks
player.onChat("alter", function (Alter) {
    if (Alter < 12) {
        blocks.print(
        "HALLO",
        GRASS,
        pos(0, 0, 0),
        WEST
        )
    } else if (Alter == 12) {
        blocks.print(
        "HALLO",
        GRASS,
        pos(0, 0, 0),
        WEST
        )
    } else {
        blocks.print(
        "HALLO",
        GRASS,
        pos(0, 0, 0),
        WEST
        )
    }
})
```

---

## Schritt 7
Schreibe unterschiedliche Nachrichten. Gib in jedem ``||Blocks:schreibe "Hallo"||``-Block eine andere Nachricht ein. Eine für Personen, die jünger sind als du, eine für dein Alter und eine für ältere Personen.

---

## Schritt 8
Wähle in den ``||Blocks:schreibe||``-Blöcken über das Dropdown-Menü unterschiedliche Materialien aus, die für jede Nachricht verwendet werden.

Stelle in allen ``||Blocks:schreibe||``-Blöcken die **Y**-Koordinate auf **10** ein (damit die Nachrichten am Himmel angezeigt werden).

### ~ tutorialhint
```blocks
player.onChat("alter", function (Alter) {
    if (Alter < 12) {
        blocks.print(
        "Kleines Baby",
        SMOOTH_SANDSTONE,
        pos(0, 10, 0),
        WEST
        )
    } else if (Alter == 12) {
        blocks.print(
        "Gleichalt",
        ORANGE_TERRACOTTA,
        pos(0, 10, 0),
        WEST
        )
    } else {
        blocks.print(
        "Alter Opa oder alte Oma",
        STONECUTTER,
        pos(0, 10, 0),
        WEST
        )
    }
})
```

---

## Schritt 9
Teste die Altersnachrichten. Arbeite mit einem Partner, um diese Nachrichten auszuprobieren. Öffne im Minecraft-Spiel das Chatfenster mit der Taste **T**.

Frage deinen Nachbarn nach seinem Alter und gib den Befehl **alter x** ein – wobei **x** das Alter deines Nachbarn ist.

Schau in den Himmel über dir und ließ die Nachricht!

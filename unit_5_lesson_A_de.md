### @explicitHints 1

# Aktivität: Alterscheck mit Bedingungen

---

## 1. Chat-Befehl anlegen
Benenne den vorhandenen ``||PLAYER:bei Chat-Befehl "run"||``-Block in **"alter"** um.

Klicke auf das Plus **(+)**-Symbol im ``||PLAYER:bei Chat-Befehl "alter"||``, um einen **num1**-Variablenparameter zu erstellen.

Benenne **num1** in **Alter** um. Das macht deinen Code lesbarer. Verwende immer aussagekräftige Namen für Variablen, um das Auffinden von Fehlern zu erleichtern. Du kannst Variablen über das Dropdown-Menü umbenennen.

### ~ tutorialhint
```blocks
player.onChat("alter", function (Alter) {

})
```

---

## 2. Wenn-Dann-Struktur einfügen
Verwende eine Bedingung. Ziehe einen ``||LOGIC:wenn ... dann ... ansonsten||``-Block in den ``||PLAYER:bei Chat-Befehl "alter"||``-Block.

Klicke auf das Plus **(+)**-Symbol im ``||LOGIC:wenn ... dann ... ansonsten||``-Block, um einen zusätzlichen ``||LOGIC:sonst wenn ... dann||``-Zweig zu erstellen.

---

## 3. Ersten Vergleich einsetzen
Füge Vergleiche ein. Ziehe einen **kleiner als**, ``||LOGIC:0 < 0||``, Vergleichsblock in den ``||LOGIC:wenn||``-Platz und ersetze **wahr**.

---

## 4. Zweiten Vergleich einsetzen
Ziehe einen **gleich wie**, ``||LOGIC:0 = 0||``, Vergleichsblock in den ``||LOGIC:sonst wenn ... dann||``-Platz.

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

## 5. Alter mit Schwellen vergleichen
Vergleiche mit deiner Variablen. Ziehe zwei ``||VARIABLES:Alter||``-Blöcke in den ersten Platz jedes Vergleichsblocks.

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

## 6. Block duplizieren
Füge Schreibblöcke für jede Bedingung ein. Ziehe einen ``||BLOCKS:schreibe "HELLO"||``-Block in deinen Arbeitsbereich. Rechtsklicke auf diesen Block und wähle **Duplizieren**, um Kopien zu erstellen.

Platziere je einen in den ``||LOGIC:wenn ... dann||``, ``||LOGIC:sonst wenn ... dann||`` und ``||LOGIC:ansonsten||``-Abschnitten.

### ~ tutorialhint
```blocks
player.onChat("alter", function (Alter) {
    if (Alter < 12) {
        blocks.print(
        "HELLO",
        GRASS,
        pos(0, 0, 0),
        WEST
        )
    } else if (Alter == 12) {
        blocks.print(
        "HELLO",
        GRASS,
        pos(0, 0, 0),
        WEST
        )
    } else {
        blocks.print(
        "HELLO",
        GRASS,
        pos(0, 0, 0),
        WEST
        )
    }
})
```

---

## 7. Text platzieren
Schreibe unterschiedliche Nachrichten. Gib in jedem ``||BLOCKS:schreibe "HELLO"||``-Block eine andere Nachricht ein. Eine für Personen, die jünger sind als du, eine für dein Alter und eine für ältere Personen.

---

## 8. Text platzieren
Wähle in den ``||BLOCKS:schreibe||``-Blöcken über das Dropdown-Menü unterschiedliche Materialien aus, die für jede Nachricht verwendet werden.

Stelle in allen ``||BLOCKS:schreibe||``-Blöcken die **Y**-Koordinate auf **10** ein (damit die Nachrichten am Himmel angezeigt werden).

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

## 9. Code testen
Teste die Altersnachrichten. Arbeite mit einem Partner, um diese Nachrichten auszuprobieren. Öffne im Minecraft-Spiel das Chatfenster mit der Taste **T**.

Frage deinen Nachbarn nach seinem Alter und gib den Befehl **alter X** ein – wobei **X** das Alter deines Nachbarn ist.

Schau in den Himmel über dir und lies die Nachricht!

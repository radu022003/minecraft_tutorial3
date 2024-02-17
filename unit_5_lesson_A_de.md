### @explicitHints 1

# Aktivität: Wie alt bist du? 

## Schritt 1
Benennen Sie den vorhandenen ``||Player:Bei Chat-Befehl "run"||`` in **"alter"** um.

Klicken Sie auf das Pluszeichen **(+)** auf dem ``||Player:Bei Chat-Befehl "alt"||``, um einen **num1**-Variablenparameter zu erstellen.

Benennen Sie **num1** in **FreundAlter** um. Dies macht Ihren Code lesbarer. Verwenden Sie immer aussagekräftige Namen, wenn Sie Variablen im Code erstellen. Dadurch wird das Auffinden von Fehlern intuitiver. Sie können Variablen aus dem Dropdown-Menü umbenennen.

### ~ tutorialhint
``` blocks
player.onChat("alter", function(FreundAlter) {

})
```

## Schritt 2
Verwenden Sie eine Bedingung. Ziehen Sie einen ``||Logic:wenn dann ansonsten||``-Block in ``||Player:Bei Chat-Befehl "age"||``.

Klicken Sie auf das Pluszeichen **(+)** im ``||Logic:wenn dann ansonsten||``, um einen weiteren ``||Logic:ansonsten||``-Zweig zu erstellen.

## Schritt 3
Fügen Sie die Vergleiche ein. Ziehen Sie einen "kleiner als" -Block, ``||Logic:0 < 0||``, in den ``||Logic:wenn||`` -Slot und ersetzen Sie **wahr**.

## Schritt 4
Ziehen Sie einen **Egal**, ``||Logic:0 = 0||``, Vergleichsblock in den ``||Logic:sonst wenn||`` -Slot.

### ~ tutorialhint
``` blocks
player.onChat("alter", function (FreundAlter) {
    if (0 < 0) {
    } else if (0 == 0) {
    } else {
    }
})
```

## Schritt 5
Vergleichen Sie mit Ihrer Variablen. Ziehen Sie zwei der ``||Variables:FriendsAge||``-Blöcke in den ersten Slot jeder der **Vergleichs**-Blöcke.

Geben Sie in den zweiten Slot der Vergleichsblöcke Ihr Alter ein (zum Beispiel **12**).

### ~ tutorialhint
``` blocks
player.onChat("alter", function (FreundAlter) {
    if (FreundAlter < 12) {

    } else if (FreundAlter == 12) {

    } else {

    }
})
```

## Schritt 6
Drücken Sie für jede Bedingung einen Ausgabeblock ab. Ziehen Sie einen ``||Blocks:schreibe "Hallo"||``-Block auf Ihre Arbeitsfläche. Klicken Sie mit der rechten Maustaste auf den ``||Blocks:schreibe "Hallo"||``-Block und wählen Sie **Duplizieren**, um eine Kopie zu erstellen.

Platzieren Sie jeweils einen in jedem Ihrer ``||Logic:wenn||``, ``||Logic:sonst wenn||`` und ``||Logic:ansonsten||``-Klauseln.

### ~ tutorialhint
``` blocks
player.onChat("alter", function (FreundAlter) {
    if (FreundAlter < 12) {
        blocks.print(
        "HELLO",
        GRASS,
        pos(0, 0, 0),
        WEST
        )
    } else if (FreundAlter == 12) {
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

## Schritt 7
Drucken Sie verschiedene Nachrichten. Geben Sie in jedem ``||Blocks:schreibe "Hallo"||`` eine andere Nachricht für Personen ein, die jünger sind als Sie, Ihr gleiches Alter haben oder älter sind als Sie.

## Schritt 8
Verwenden Sie das Dropdown-Menü in den ``||Blocks:schreibe||``-Blöcken, um einen anderen Block für jede Nachricht auszuwählen.

In allen ``||Blocks:schreibe||``-Blöcken setzen Sie die **Y**-Koordinate auf 10 (damit diese Nachrichten am Himmel gedruckt werden).

### ~ tutorialhint
``` blocks
player.onChat("alter", function (FreundAlter) {
    if (FreundAlter < 12) {
        blocks.print(
        "Baby",
        SMOOTH_SANDSTONE,
        pos(0, 10, 0),
        WEST
        )
    } else if (FreundAlter == 12) {
        blocks.print(
        "Zufall?",
        ORANGE_TERRACOTTA,
        pos(0, 10, 0),
        WEST
        )
    } else {
        blocks.print(
        "Opa",
        STONECUTTER,
        pos(0, 10, 0),
        WEST
        )
    }
})
```

## Schritt 9
Viel Spaß beim Anzeigen der Altersnachrichten. Arbeiten Sie zusammen, um diese Nachrichten auszuführen. Im Minecraft-Spiel geben Sie **T** ein, um das Chat-Fenster zu öffnen.

Fragen Sie Ihren Kollege nach seinem Alter und geben Sie **alter x** ein, wobei x das Alter Ihres Kollege ist.

Schauen Sie in den Himmel über sich, um Ihre Nachricht zu sehen!
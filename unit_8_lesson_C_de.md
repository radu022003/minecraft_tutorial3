### @explicitHints 1

# Aktivität: Warp Belt

## Schritt 1
Ziehen Sie einen ``||Loops:beim start||`` Block auf die Programmierfläche.
Erstellen Sie ein leeres Array.

## Schritt 2
Erstellen Sie eine Variable und nennen Sie sie **warp_array**. Ziehen Sie einen ``||Variables:setze||`` Block in den beim Start-Block.

Aus dem Dropdown-Menü ``||Variables:setze||`` wählen Sie die Variable **warp_array** aus.

## Schritt 3
Ziehen Sie ein ``||Arrays:leeres Array||`` in den ``||Variables:setze "warp_array" auf||`` Block.

In ``||Arrays:leeres Array||``, klicken Sie auf das Minuszeichen **(–)**, um es zu leeren. Sie sollten sehen, dass sich der Titel zu ``||Arrays:leeres Array||`` ändert.

### ~ tutorialhint
``` blocks
let warp_array: number[] = []
warp_array = []
```

## Schritt 4
Erstellen Sie den Befehl "löschen". Ziehen Sie einen ``||Player:Bei Chat-Befehl||`` Block auf die Programmierfläche.

Nennen Sie diesen Befehl **delete**.

## Schritt 5
Klicken Sie mit der rechten Maustaste auf das vorhandene ``||Variables:setze||`` im ``||Loops:beim start||`` und wählen Sie Duplizieren aus.

Ziehen Sie diesen neuen ``||Variables:setze||`` Block in den ``||Player:Bei Chat-Befehl "delete"||``.

## Schritt 6
Ziehen Sie ein ``||Player:sag||`` nach dem ``||Variables:setze||``.

In ``||Player:sag||``, geben Sie eine Nachricht ein, zum Beispiel **"Array gelöscht"**.

### ~ tutorialhint
``` blocks
let warp_array: number[] = []
player.onChat("delete", function () {
    warp_array = []
    player.say("Array gelöscht")
})
warp_array = []
```
## Schritt 7
Erstellen Sie den Befehl "speichern". Ziehen Sie einen weiteren ``||Player:Bei Chat-Befehl||`` auf die Arbeitsfläche.

Nennen Sie diesen Befehl **save**.

## Schritt 8
Ziehen Sie ``||Arrays:füge Wert am Ende hinzu||`` in den ``||Player:Bei Chat-Befehl "save"||``.

Setzen Sie die Position in das Warp-Array. Wählen Sie aus dem Dropdown-Menü ``||Arrays:füge Wert am Ende hinzu||`` das **warp_array** als das Array aus, zu dem Sie Werte hinzufügen möchten.

Ziehen Sie einen ``||Player:Position des Spielers in der Welt||`` in das Hinzufügen des Werts von ``||Arrays:füge Wert am Ende hinzu||``.

### ~ tutorialhint
``` blocks
let warp_array: Position[] = []
warp_array.push(player.position())
```

## Schritt 9
Ziehen Sie einen ``||Player:sag||`` Block nach dem ``||Arrays:"warp_array" füge Wert "player world position" am Ende hinzu||`` Block.

Im ``||Player:sag||`` Block geben Sie eine Nachricht ein, zum Beispiel **"Position hinzugefügt"**.

### ~ tutorialhint
``` blocks
let warp_array: Position[] = [] 
player.onChat("delete", function () {
    warp_array = []
    player.say("Array gelöscht")
})
player.onChat("save", function () {
    warp_array.push(player.position())
    player.say("Position hinzugefügt")
})
warp_array = []
```

## Schritt 10
Erstellen Sie einen "warp" Befehl. Der Spieler wird den Warp-Befehl verwenden, indem er eine Nummer übergibt, wie z.B. "warp 1" oder "warp 2", um sich an einen gespeicherten Ort im Array zu teleportieren.

Ziehen Sie einen ``||Player:Bei Chat-Befehl||`` auf die Arbeitsfläche und nennen Sie ihn **warp**.

## Schritt 11
In ``||Player:Bei Chat-Befehl "warp"||``, klicken Sie auf das Pluszeichen **(+)**, um einen Parameter hinzuzufügen. Dies wird standardmäßig als **num1** bezeichnet. Dies ist eine Variable. Dies ist die Nummer des Ortes, zu dem Sie sich teleportieren möchten. Denken Sie daran, dass in Arrays die Nummer, an der etwas gespeichert ist, als Index oder Schlüssel bezeichnet wird. Sie werden hier den Index durch ``||Player:Bei Chat-Befehl "warp"||`` übergeben. Dann werden Sie die Informationen abrufen, die an diesem Ort gespeichert sind.

## Schritt 12
Wenn Sie sich zum dritten gespeicherten Ort teleportieren möchten, würden Sie **warp 3** im Chatfenster eingeben. Der Computer geht dann zum dritten Ort und holt Ihre Koordinaten für Sie!

Sie sollten Variablen immer sinnvoll benennen. Benennen Sie **num1** in **Warp_LocationNum** um.

## Schritt 13
Ziehen Sie ``||Player:teleportiere nach||`` in ``||Player:Bei Chat-Befehl "warp"||``.

## Schritt 14
Jetzt müssen wir nur noch die Informationen aus unserem Array abrufen. Ziehen Sie aus ``||Arrays:ARRAYS||`` den Block ``||Arrays:rufe Wert ab bei||`` in ``||Player:teleportiere nach||`` und ersetzen Sie den vorhandenen Koordinatenblock.

### ~ tutorialhint
``` blocks
let warp_array: Position[] = []
player.teleport(warp_array[0])
```

## Schritt 15
Aus dem Dropdown-Menü von ``||Arrays:rufe Wert ab bei||`` wählen Sie die Variable **warp_array** aus.

Ziehen Sie **Warp_LocationNum** in den zweiten Steckplatz von ``||Arrays:rufe Wert ab bei||``.

### ~ tutorialhint
``` blocks
let warp_array: Position[] = []
player.onChat("warp", function (Warp_LocationNum) {
    player.teleport(warp_array[Warp_LocationNum])
})
```
## Schritt 16
Jetzt, wenn Sie den Warp-Befehl mit einer Zahl aufrufen, wird der Code die Position an der Stelle abrufen, die Sie angeben. Dann teleportieren Sie sich zur Position, die im Array gespeichert ist.

### ~ tutorialhint
``` blocks
let warp_array: Position[] = []
player.onChat("delete", function () {
    warp_array = []
    player.say("Array gelöscht")
})
player.onChat("save", function () {
    warp_array.push(player.position())
    player.say("Position hinzugefügt")
})
player.onChat("warp", function (Warp_LocationNum) {
    player.teleport(warp_array[Warp_LocationNum - 1])
})
warp_array = []
```

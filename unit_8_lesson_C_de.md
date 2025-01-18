### @explicitHints 1

# Aktivität: Warp Belt

## Schritt 2
Erstelle eine Variable und nennen Sie sie **warp_array**. Ziehen Sie einen ``||Variables:setze||``-Block in den beim Start-Block.

Aus dem Dropdown-Menü ``||Variables:setze||`` wähle die Variable **warp_array** aus.

## Schritt 3
Ziehe ein ``||Arrays:leeres Array||`` in den ``||Variables:setze "warp_array" auf||``-Block.

In ``||Arrays:leeres Array||``, klicke auf das Minuszeichen **(–)**, um es zu leeren.

### ~ tutorialhint
``` blocks
let warp_array: number[] = []
warp_array = []
```

## Schritt 4
Ziehe einen ``||Player:Bei Chat-Befehl||``-Block auf die Programmierfläche.

Nenne diesen Befehl **delete**.

## Schritt 5
Klicke mit der rechten Maustaste auf das vorhandene ``||Variables:setze||``-Block im ``||Loops:beim start||`` und Dupliziere sie.

Ziehe diesen neuen ``||Variables:setze||``-Block in den ``||Player:Bei Chat-Befehl "delete"||``-Block.

## Schritt 6
Platziere einen ``||Player:sag||``-Block nach dem ``||Variables:setze||``-Block.

In ``||Player:sag||``-Block, gebe eine Nachricht ein, zum Beispiel **"Array gelöscht"**.

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
Erstelle den Befehl "speichern". Ziehe einen weiteren ``||Player:Bei Chat-Befehl||``-Block auf die Arbeitsfläche.

Nenne diesen Befehl **save**.

## Schritt 8
Ziehe ``||Arrays:füge Wert am Ende hinzu||``-Block in den ``||Player:Bei Chat-Befehl "save"||``_block.

Wähle aus dem Dropdown-Menü ``||Arrays:füge Wert am Ende hinzu||`` das **warp_array** aus.

Ziehe einen ``||Player:Position des Spielers in der Welt||``-Block in dem ``||Arrays:füge Wert am Ende hinzu||``-Block.

### ~ tutorialhint
``` blocks
let warp_array: Position[] = []
warp_array.push(player.position())
```

## Schritt 9
Ziehe einen ``||Player:sag||``-Block nach dem ``||Arrays:"warp_array" füge Wert "Position des Spielers in der Welt" am Ende hinzu||``-Block.

Im ``||Player:sag||``-Block gebe eine Nachricht ein, zum Beispiel **"Position hinzugefügt"**.

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
Ziehe einen ``||Player:Bei Chat-Befehl||``-Block auf die Arbeitsfläche und nenne es **warp**.

## Schritt 11
In ``||Player:Bei Chat-Befehl "warp"||``, klicke auf das Pluszeichen **(+)**, um einen Parameter hinzuzufügen. Dies wird standardmäßig als **num1** bezeichnet. Dies ist eine Variable. Dies ist die Nummer des Ortes, zu dem Sie sich teleportieren möchten. Denke daran, dass in Arrays die Nummer, an der etwas gespeichert ist, als Index oder Schlüssel bezeichnet wird. Du wirst hier den Index durch ``||Player:Bei Chat-Befehl "warp"||`` übergeben. Dann wirst du die Informationen abrufen, die an diesem Ort gespeichert sind.

## Schritt 12
Wenn Sie sich zum dritten gespeicherten Ort teleportieren möchten, würden Sie **warp 3** im Chatfenster eingeben. Der Computer geht dann zum dritten Ort und holt Ihre Koordinaten für Sie!

Sie sollten Variablen immer sinnvoll benennen. Benennen Sie **num1** in **Warp_LocationNum** um.

## Schritt 13
Ziehe ``||Player:teleportiere nach||``-Block in ``||Player:Bei Chat-Befehl "warp"||``.

## Schritt 14
Jetzt müssen wir nur noch die Informationen aus unserem Array abrufen. Ziehe aus ``||Arrays:ARRAYS||`` den Block ``||Arrays:rufe Wert ab bei||`` in ``||Player:teleportiere nach||`` und ersetze den vorhandenen Koordinatenblock.

### ~ tutorialhint
``` blocks
let warp_array: Position[] = []
player.teleport(warp_array[0])
```

## Schritt 15
Aus dem Dropdown-Menü von ``||Arrays:rufe Wert ab bei||`` wähle die Variable **warp_array** aus.

Ziehe **Warp_LocationNum** in den zweiten Steckplatz von ``||Arrays:rufe Wert ab bei||``.

### ~ tutorialhint
``` blocks
let warp_array: Position[] = []
player.onChat("warp", function (Warp_LocationNum) {
    player.teleport(warp_array[Warp_LocationNum])
})
```
## Schritt 16
Jetzt, wenn du den Warp-Befehl mit einer Zahl aufrufst, wird der Code die Position an der Stelle abrufen, die du angibst. Dann teleportierst du dich zur Position, die im Array gespeichert ist.

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

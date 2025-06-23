### @explicitHints 1

# Aktivität: Koordinaten speichern

## Schritt 1
Erstelle eine Variable und nenne sie **tp_array**. Ziehe einen ``||Variables:setze||``-Block in den beim ``||Loops:Start-Block||``.

Aus dem Dropdown-Menü ``||Variables:setze||`` wähle die Variable **tp_array** aus.

## Schritt 2
Ziehe ein ``||Arrays:leeres Array||`` in den ``||Variables:setze "tp_array" auf||``-Block.

### ~ tutorialhint
``` blocks
let tp_array: number[] = []
tp_array = []
```

## Schritt 3
Ziehe einen ``||Player:Bei Chat-Befehl||``-Block auf die Programmierfläche.

Nenne diesen Befehl **delete**.

## Schritt 4
Klicke mit der rechten Maustaste auf das vorhandene ``||Variables:setze||``-Block im ``||Loops:beim start||`` und Dupliziere sie.

Ziehe diesen neuen ``||Variables:setze||``-Block in den ``||Player:Bei Chat-Befehl "delete"||``-Block.

## Schritt 5
Platziere einen ``||Player:sag||``-Block nach dem ``||Variables:setze||``-Block.

In ``||Player:sag||``-Block, gebe eine Nachricht ein, zum Beispiel **"Array gelöscht"**.

### ~ tutorialhint
``` blocks
let tp_array: number[] = []
player.onChat("delete", function () {
    tp_array = []
    player.say("Array gelöscht")
})
tp_array = []
```
## Schritt 6: Erstelle den Befehl "save"(=speichern). 
Ziehe einen weiteren ``||Player:Bei Chat-Befehl||``-Block auf die Arbeitsfläche.

Nenne diesen Befehl **save**.

## Schritt 7
Ziehe ``||Arrays:füge Wert am Ende hinzu||``-Block in den ``||Player:Bei Chat-Befehl "save"||``_block.

Wähle aus dem Dropdown-Menü ``||Arrays:füge Wert am Ende hinzu||`` das **tp_array** aus.

Ziehe einen ``||Player:Position des Spielers in der Welt||``-Block in dem ``||Arrays:füge Wert am Ende hinzu||``-Block.

### ~ tutorialhint
``` blocks
let tp_array: Position[] = []
tp_array.push(player.position())
```

## Schritt 8
Ziehe einen ``||Player:sag||``-Block nach dem ``||Arrays:"tp_array" füge Wert "Position des Spielers in der Welt" am Ende hinzu||``-Block.

Im ``||Player:sag||``-Block gebe eine Nachricht ein, zum Beispiel **"Position hinzugefügt"**.

### ~ tutorialhint
``` blocks
let tp_array: Position[] = [] 
player.onChat("delete", function () {
    tp_array = []
    player.say("Array gelöscht")
})
player.onChat("save", function () {
    tp_array.push(player.position())
    player.say("Position hinzugefügt")
})
tp_array = []
```

## Schritt 9
Ziehe einen ``||Player:Bei Chat-Befehl||``-Block auf die Arbeitsfläche und nenne es **tp**.

## Schritt 10
In ``||Player:Bei Chat-Befehl "tp"||``, klicke auf das Pluszeichen **(+)**, um eine Veriable hinzuzufügen. Dies wird standardmäßig als **num1** bezeichnet. Dies ist die Nummer des Ortes, zu dem du dich teleportieren möchtest.

## Schritt 11
Wenn du dich zum **dritten** gespeicherten Ort teleportieren möchtest, musst du **tp 2** im Chatfenster eingeben. Der Computer geht dann zum **dritten** Ort und holt die Koordinaten für dich!

Du solltest die Variablen immer sinnvoll benennen. Benenne **num1** in **tp_LocationNum** um.

## Schritt 12
Ziehe ``||Player:teleportiere nach||``-Block in ``||Player:Bei Chat-Befehl "tp"||``.

## Schritt 13
Jetzt müssen wir nur noch die Informationen aus unserem Array abrufen. Ziehe aus ``||Arrays:ARRAYS||`` den Block ``||Arrays:rufe Wert ab bei||`` in ``||Player:teleportiere nach||`` und ersetze den vorhandenen Koordinatenblock.

### ~ tutorialhint
``` blocks
let tp_array: Position[] = []
player.teleport(tp_array[0])
```

## Schritt 14
Aus dem Dropdown-Menü von ``||Arrays:rufe Wert ab bei||`` wähle die Variable **tp_array** aus.

Ziehe **tp_LocationNum** in den zweiten Steckplatz von ``||Arrays:rufe Wert ab bei||``.

### ~ tutorialhint
``` blocks
let tp_array: Position[] = []
player.onChat("tp", function (tp_LocationNum) {
    player.teleport(tp_array[tp_LocationNum])
})
```
## Schritt 15
Jetzt, wenn du den tp-Befehl mit einer Zahl aufrufst, wird der Code die Position an der Stelle abrufen, die du angibst. Dann teleportierst du dich zur Position, die im Array gespeichert ist.

**Nicht vergessen:** Location1 = 0; Location2 = 1; ...

### ~ tutorialhint
``` blocks
let tp_array: Position[] = []
player.onChat("delete", function () {
    tp_array = []
    player.say("Array gelöscht")
})
player.onChat("save", function () {
    tp_array.push(player.position())
    player.say("Position hinzugefügt")
})
player.onChat("tp", function (tp_LocationNum) {
    player.teleport(tp_array[tp_LocationNum - 1])
})
tp_array = []
```

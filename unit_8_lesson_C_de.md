### @explicitHints 1

# Aktivität: Koordinaten speichern

## 1. tp_array initialisieren
Erstelle eine Variable und nenne sie **tp_array**. Ziehe einen ``||VARIABLES:setze||``-Block in den beim ``||LOOPS:Start-Block||``.

Aus dem Dropdown-Menü ``||VARIABLES:setze||`` wähle die Variable **tp_array** aus.

## 2. Leeres Array zuweisen
Ziehe ein ``||ARRAYS:leeres Array||`` in den ``||VARIABLES:setze "tp_array" auf||``-Block.

### ~ tutorialhint
``` blocks
let tp_array: number[] = []
tp_array = []
```

## 3. Delete-Befehl erstellen
Ziehe einen ``||PLAYER:Bei Chat-Befehl||``-Block auf die Programmierfläche.

Nenne diesen Befehl **delete**.

## 4. Block duplizieren
Klicke mit der rechten Maustaste auf den vorhandenen ``||VARIABLES:setze||``-Block im ``||LOOPS:beim Start||`` und dupliziere ihn.

Ziehe diesen neuen ``||VARIABLES:setze||``-Block in den ``||PLAYER:Bei Chat-Befehl "delete"||``-Block.

## 5. Löschmeldung ausgeben
Platziere einen ``||PLAYER:sag||``-Block nach dem ``||VARIABLES:setze||``-Block.

In ``||PLAYER:sag||``-Block, gebe eine Nachricht ein, zum Beispiel **"Array gelöscht"**.

### ~ tutorialhint
``` blocks
let tp_array: number[] = []
player.onChat("delete", function () {
    tp_array = []
    player.say("Array gelöscht")
})
tp_array = []
```
## 6. Save-Befehl erstellen
Ziehe einen weiteren ``||PLAYER:Bei Chat-Befehl||``-Block auf die Arbeitsfläche.

Nenne diesen Befehl **save**.

## 7. Array aufbauen
Ziehe ``||ARRAYS:füge Wert am Ende hinzu||``-Block in den ``||PLAYER:Bei Chat-Befehl "save"||``_block.

Wähle aus dem Dropdown-Menü ``||ARRAYS:füge Wert am Ende hinzu||`` das **tp_array** aus.

Ziehe einen ``||PLAYER:Position des Spielers in der Welt||``-Block in dem ``||ARRAYS:füge Wert am Ende hinzu||``-Block.

### ~ tutorialhint
``` blocks
let tp_array: Position[] = []
tp_array.push(player.position())
```

## 8. Array aufbauen
Ziehe einen ``||PLAYER:sag||``-Block nach dem ``||ARRAYS:"tp_array" füge Wert "Position des Spielers in der Welt" am Ende hinzu||``-Block.

Im ``||PLAYER:sag||``-Block gebe eine Nachricht ein, zum Beispiel **"Position hinzugefügt"**.

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

## 9. TP-Befehl erstellen
Ziehe einen ``||PLAYER:Bei Chat-Befehl||``-Block auf die Arbeitsfläche und nenne es **tp**.

## 10. Parameter hinzufügen
In ``||PLAYER:Bei Chat-Befehl "tp"||``, klicke auf das Pluszeichen **(+)**, um eine Variable hinzuzufügen. Diese wird standardmäßig als **num1** bezeichnet. Das ist die Nummer des Ortes, zu dem du dich teleportieren möchtest.

## 11. Parameter umbenennen
Wenn du dich zum **dritten** gespeicherten Ort teleportieren möchtest, musst du **tp 2** im Chatfenster eingeben. Der Computer geht dann zum **dritten** Ort und holt die Koordinaten für dich!

Du solltest die Variablen immer sinnvoll benennen. Benenne **num1** in **tp_LocationNum** um.

## 12. Teleport einrichten
Ziehe ``||PLAYER:teleportiere nach||``-Block in ``||PLAYER:Bei Chat-Befehl "tp"||``.

## 13. Koordinaten setzen
Jetzt müssen wir nur noch die Informationen aus unserem Array abrufen. Ziehe aus ``||ARRAYS:ARRAYS||`` den Block ``||ARRAYS:rufe Wert ab bei||`` in ``||PLAYER:teleportiere nach||`` und ersetze den vorhandenen Koordinatenblock.

### ~ tutorialhint
``` blocks
let tp_array: Position[] = []
player.teleport(tp_array[0])
```

## 14. Auswahl treffen
Aus dem Dropdown-Menü von ``||ARRAYS:rufe Wert ab bei||`` wähle die Variable **tp_array** aus.

Ziehe **tp_LocationNum** in den zweiten Steckplatz von ``||ARRAYS:rufe Wert ab bei||``.

### ~ tutorialhint
``` blocks
let tp_array: Position[] = []
player.onChat("tp", function (tp_LocationNum) {
    player.teleport(tp_array[tp_LocationNum])
})
```
## 15. Teleport aus Array ausführen
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

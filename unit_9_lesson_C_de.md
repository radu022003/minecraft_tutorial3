### @explicitHints 1  
# Aktivität: Baumjäger

## Schritt 1  
Verwende den bereitgestellten Starter-Code. Erstelle den Chat-Befehl „chopper“.  
Erzeuge einen ``||Player:Bei Chat-Befehl||``‑Block und benenne ihn in **"chopper"** um.

```template
let flipturn = false
let height = 0
function chop() {
    height = 0
    while (agent.detect(AgentDetection.Block, SixDirection.Forward)) {
        height += 1
        agent.destroy(SixDirection.Up)
        agent.move(SixDirection.Up, 1)
    }
    for (let i = 0; i < height; i++) {
        agent.move(SixDirection.Down, 1)
        agent.destroy(SixDirection.Forward)
    }
    agent.collectAll()
}
function follow() {
    agent.move(SixDirection.Forward, 1)
    if (agent.inspect(AgentInspection.Block, SixDirection.Forward) == blocks.block(Block.Grass)) {
        agent.destroy(SixDirection.Up)
        agent.move(SixDirection.Up, 1)
    } else if (!(agent.detect(AgentDetection.Block, SixDirection.Down))) {
        agent.move(SixDirection.Down, 1)
    } else {
 
    }
}
player.onChat("tp", function () {
    agent.teleportToPlayer()
})
player.onChat("lt", function () {
    agent.turn(TurnDirection.Left)
})
function turn() {
    agent.setAssist(DESTROY_OBSTACLES, true)
    if (flipturn) {
        agent.turn(TurnDirection.Right)
        agent.move(SixDirection.Forward, 3)
        agent.turn(TurnDirection.Right)
    } else {
        agent.turn(TurnDirection.Left)
        agent.move(SixDirection.Forward, 3)
        agent.turn(TurnDirection.Left)
    }
    flipturn = !(flipturn)
}
```

---

## Schritt 2  
Um die Größe des Suchgebiets festzulegen, fügen wir unserem „chopper“‑Chatbefehl einen Parameter hinzu, der die Länge einer Seite des quadratischen Suchgebiets darstellt.  
Klicke im Block ``||Player:Bei Chat-Befehl "chopper"||`` auf das Pluszeichen **(+)**, um den Parameter **num1** hinzuzufügen. Benenne diesen über das Dropdown-Menü in **area** um.

### ~ tutorialhint
``` blocks
player.onChat("chopper", function(area) {

})
```

---

## Schritt 3  
Erstelle die Funktion **suchen()**.  
Wir erstellen nun die restlichen Funktionen, die unser Programm bilden. Am Ende rufen wir alle Funktionen aus dem Block ``||Player:Bei Chat-Befehl "chopper"||`` auf.

---

## Schritt 4  
Füge Logik in die Funktion **suchen()** ein.  
Die Funktion **suchen()** soll den Agenten prüfen lassen, ob sich Bäume in seiner Umgebung befinden. Der Agent sucht dabei rechts, links und vor sich nach Holzblöcken, die auf einen Baum hinweisen. Findet er einen solchen Block, ruft er die Funktion *chop()* auf, um den Baum zu fällen.

---

## Schritt 5  
Ziehe einen ``||Logic:wenn dann ansonsten||``‑Block in die Funktion **suchen()**.  
Klicke in diesem Block zweimal auf das Pluszeichen **(+)**, um zwei zusätzliche ``||Logic:sonst wenn||``‑Klauseln zu erstellen.

---

## Schritt 6  
Suche nach Holz links:  
Ziehe einen ``||Logic:0 = 0||``‑Vergleichsblock heraus und platziere ihn in das erste Bedingungsfeld des ``||Logic:wenn||``‑Blocks.

---

## Schritt 7  
Ziehe einen ``||Agent:agent untersuche||``‑Block in das erste Feld des ``||Logic:0 = 0||``‑Blocks.  
Wähle im ``||Agent:agent untersuche||``‑Block über das Dropdown-Menü die Richtung **links** aus.  
Ziehe einen ``||Blocks:block||``‑Block heraus und platziere ihn im zweiten Feld des Vergleichs.  
Wähle im ``||Blocks:block||``‑Block über das Dropdown-Menü ein **Eichenholz**‑Block oder einen anderen Baumtyp aus, den du durchsuchen möchtest.

### ~ tutorialhint
``` blocks
function suchen() {
    if (agent.inspect(AgentInspection.Block, LEFT) == LOG_OAK) {

    } else if (0 == 0) {

    } else if (0 == 0) {

    } else {

    }
}
```

---

## Schritt 8  
Fällt den Baum links:  
Ziehe aus ``||Agent:AGENT||`` einen ``||Agent:Agent, drehe dich nach||``‑Block in den ersten Ast des ``||Logic:wenn dann||``‑Blocks.

### ~ tutorialhint
Wenn du links vom Agenten Holz findest, solltest du den Agenten nach links drehen und die Funktion chop() aufrufen, um den Baum zu fällen. Anschließend sollte sich der Agent wieder umdrehen und nach vorne blicken.

---

## Schritt 9  
Platziere einen ``||Functions:Aufruf Funktion chop||``‑Block unterhalb des ``||Agent:Agent, drehe dich nach||``‑Blocks.  
Dupliziere anschließend den ``||Agent:Agent, drehe dich nach||``‑Block und platziere die Kopie unterhalb des ``||Functions:Aufruf Funktion chop||``‑Blocks.  
Wähle in diesem neuen Block über das Dropdown-Menü **rechts** aus.

### ~ tutorialhint
``` blocks
function suchen() {
    if (agent.inspect(AgentInspection.Block, LEFT) == LOG_OAK) {
        agent.turn(TurnDirection.Left)
        chop()
        agent.turn(TurnDirection.Right)
    } else if (false) {

    } else if (false) {

    } else {

    }
}
function chop()  {

}
```

---

## Schritt 10  
Suche nach Holz, das geradeaus gefällt werden kann.  
Du möchtest nun prüfen, ob sich vor dem Agenten ein Holzblock befindet. In diesem Fall muss der Agent nicht gedreht werden.  
Klicke auf die erste erstellte Bedingung und dupliziere sie. Platziere das Duplikat in das zweite Bedingungsfeld deines ``||Logic:wenn||``‑Blocks.

---

## Schritt 11  
Nimm nun einige Anpassungen vor:  
Ändere im duplizierten ``||Agent:agent untersuche||``‑Block die Richtung zu **vorne**.  
Dupliziere den ``||Functions:Aufruf Funktion chop||``‑Block und platziere ihn in diesem zweiten Ast.

### ~ tutorialhint
``` blocks
function suchen() {
    if (agent.inspect(AgentInspection.Block, LEFT) == LOG_OAK) {
        agent.turn(TurnDirection.Left)
        chop()
        agent.turn(TurnDirection.Right)
    } else if (agent.inspect(AgentInspection.Block, FORWARD) == LOG_OAK) {
        chop()
    } else if (false) {

    } else {

    }
}
function chop() {

}
```

---

## Schritt 12  
Suche nach Holz rechts:  
Dupliziere die erste Bedingung und platziere sie in den dritten Ast des ``||Logic:sonst wenn||``‑Blocks.

### ~ tutorialhint
Das ist im Grunde dasselbe wie links nach Holz zu suchen, nur dass einige Dinge umgekehrt sind.

---

## Schritt 13  
Passe die Richtung in diesem Ast auf **rechts** an.  
Du benötigst zwei ``||Agent:Agent, drehe dich nach||``‑Blöcke. Dupliziere zwei und platziere sie in den dritten Ast.

---

## Schritt 14  
Dupliziere den ``||Functions:Aufruf Funktion chop||``‑Block und platziere ihn zwischen den beiden ``||Agent:Agent, drehe dich nach||``‑Blöcken.  
Passe anschließend die Drehungen an: Dieses Mal dreht sich der Agent zuerst nach rechts, fällt den Baum und dreht sich dann wieder nach links, um in seine Ausgangsrichtung zurückzukehren.

---

## Schritt 15  
Der letzte **ansonsten**‑Ast deines ``||Logic:wenn||``‑Blocks bleibt leer.

### ~ tutorialhint
``` blocks
function suchen() {
    if (agent.inspect(AgentInspection.Block, LEFT) == LOG_OAK) {
        agent.turn(TurnDirection.Left)
        chop()
        agent.turn(TurnDirection.Right)
    } else if (agent.inspect(AgentInspection.Block, FORWARD) == LOG_OAK) {
        chop()
    } else if (agent.inspect(AgentInspection.Block, RIGHT) == LOG_OAK) {
        agent.turn(TurnDirection.Right)
        chop()
        agent.turn(TurnDirection.Left)
    } else {

    }
}
function chop() {

}
```

---

## Schritt 16  
Erlaube dem Agenten, Hindernisse auf seinem Weg zu zerstören.  
Der Agent verfügt über einen Block, der ihm zusätzliche Fähigkeiten verleiht – er kann damit automatisch Blöcke platzieren, wenn er sich bewegt, und Blöcke aus jedem Inventarslot verwenden, statt nur aus dem oberen linken Slot.  
Ziehe einen ``||Agent:Agent platziere bei Bewegung||``‑Block in den Block ``||Player:Bei Chat-Befehl "chopper"||`` und wähle im Dropdown-Menü **Hindernisse zerstören** aus.

### ~ tutorialhint
Schau dir an, welche weiteren coolen Funktionen dieser Block hat – du findest sie in der Hilfe! Mit ihm kann dein Agent automatisch Blöcke platzieren, während er sich bewegt, und auch Blöcke aus jedem Slot seines Inventars verwenden, statt nur den oberen linken Slot.

---

## Schritt 17  
Wähle abschließend **EIN**.

---

## Schritt 18  
Steuere die Drehung des Agenten.  
Am Ende jeder Reihe soll sich der Agent umdrehen.  
Erstelle dazu eine Boolean‑Variable, um festzuhalten, in welche Richtung gedreht werden soll. Wir verwenden ``||Logic:Wahr||`` für eine Rechtsdrehung und ``||Logic:Falsch||`` für eine Linksdrehung.  
Nach der Drehung wird die Boolean‑Variable umgeschaltet.  
Die Variable **flipturn** wurde bereits im Starter-Code dieser Aktivität angelegt.  
Ziehe einen ``||Variables:setze||``‑Block in den Block ``||Player:Bei Chat-Befehl "chopper"||`` und wähle über das Dropdown-Menü **flipturn** aus.

---

## Schritt 19  
Ziehe einen ``||Logic:Falsch||``‑Block in den Setz‑Block und ersetze damit die **0**.

### ~ tutorialhint
``` blocks
let flipturn = false
player.onChat("chopper", function(area) {
    agent.setAssist(DESTROY_OBSTACLES, true)
    flipturn = false;
})
```

---

## Schritt 20  
Nun ist alles vorbereitet. Jetzt müssen wir den Agenten durch das Suchgebiet bewegen:  
Der Agent soll eine Reihe des Gitters hinuntergehen, sich am Ende wenden und dann weitere Reihen abgehen, bis das quadratische Gebiet vollständig durchsucht wurde.

---

## Schritt 21  
Füge die Funktionen **suchen()** und **follow()** in den Chatbefehl ein.  
Nachdem alle Funktionen erstellt wurden, bringen wir nun alles zusammen.  
Bei jedem Schritt soll der Agent nach Bäumen suchen und dem Geländeverlauf folgen. Dabei sucht er gleichzeitig in drei Richtungen (links, rechts und geradeaus).

---

## Schritt 22  
Ziehe einen ``||Loops:-mal wiederholen||``‑Block in den Block ``||Player:Bei Chat-Befehl "chopper"||`` und platziere ihn unterhalb des ``||Variables:setze flipturn||``‑Blocks.

---

## Schritt 23  
Denke daran, dass der Parameter **area** die Anzahl der Blöcke in jeder Reihe angibt.  
Ziehe ``||Variables:area||`` in den ``||Loops:-mal wiederholen||``‑Block und ersetze damit den Standardwert **4**.  
Nun wird der Agent alle Blöcke einer Reihe durchsuchen – so viele, wie der Benutzer angibt.  
Ziehe anschließend die Blöcke ``||Functions:Aufruf Funktion suchen||`` und ``||Functions:Aufruf Funktion follow||`` in die Wiederholungsschleife.

### ~ tutorialhint
``` blocks
let area = 0
let flipturn = false
player.onChat("chopper", function (area) {
    agent.setAssist(DESTROY_OBSTACLES, true)
    flipturn = false
    for (let i = 0; i < area; i++) {
        suchen()
        follow()
    }
})
function suchen() {

}
function follow() {

}
```

---

## Schritt 24  
Füge die Funktion **turn()** hinzu, damit sich der Agent am Ende jeder Reihe wendet.  
Ziehe den Block ``||Functions:Aufruf Funktion turn||`` unterhalb der ``||Loops:-mal wiederholen||``‑Schleife.

### ~ tutorialhint
``` blocks
let flipturn = false
player.onChat("chopper", function (area) {
    agent.setAssist(DESTROY_OBSTACLES, true)
    flipturn = false
    for (let i = 0; i < area; i++) {
        suchen()
        follow()
    }
    turn()
})
function suchen() {

}
function follow() {

}
function turn() {

}
```

---

## Schritt 25  
Erstelle ein vollständiges quadratisches Suchgitter.  
Du musst dazu eine weitere ``||Loops:SCHLEIFEN||``‑Schleife hinzufügen, damit der Agent das gesamte Gebiet durchsucht und ein Quadrat bildet, anstatt nur eine Reihe (bzw. drei Reihen) abzuarbeiten.

---

## Schritt 26  
Da der Agent in jedem Schritt drei Blöcke durchsucht, muss nicht die gesamte, angegebene Fläche geloopt werden.  
Teile den Wert von **area** durch 3. Im folgenden Beispiel durchsucht der Agent ein 9×9‑Gitter, benötigt aber nur 3 Wiederholungen, um alle Reihen abzugehen.  
Füge dazu eine weitere ``||Loops:-mal wiederholen||``‑Schleife ein, die alles unterhalb des Blocks ``||Variables:setze flipturn||`` einschließt.

---

## Schritt 27  
Ziehe einen ``||Math:0 / 0||``‑Block in die neue ``||Loops:-mal wiederholen||``‑Schleife und ersetze damit den Standardwert **4**.

---

## Schritt 28  
Ziehe ``||Variables:area||`` in das erste Feld des ``||Math:0 ÷ 0||``‑Blocks.  
Gib im zweiten Feld des Blocks den Wert **3** ein.  
Um das Ganze zu testen, teleportiere deinen Agenten zunächst zu deiner Position mit dem bereitgestellten ``||Player:Bei Chat-Befehl "tp"||``‑Befehl.

### ~ tutorialhint
``` blocks
let flipturn = false
let height = 0
player.onChat("tp", function () {
    agent.teleportToPlayer()
})
player.onChat("lt", function () {
    agent.turn(TurnDirection.Left)
})
player.onChat("chopper", function (area) {
    agent.setAssist(DESTROY_OBSTACLES, true)
    flipturn = false
    for (let i = 0; i < area / 3; i++) {
        for (let i = 0; i < area; i++) {
            suchen()
            follow()
        }
        turn()
    }
})
function suchen() {
    if (agent.inspect(AgentInspection.Block, LEFT) == LOG_OAK) {
        agent.turn(TurnDirection.Left)
        chop()
        agent.turn(TurnDirection.Right)
    } else if (agent.inspect(AgentInspection.Block, FORWARD) == LOG_OAK) {
        chop()
    } else if (agent.inspect(AgentInspection.Block, RIGHT) == LOG_OAK) {
        agent.turn(TurnDirection.Right)
        chop()
        agent.turn(TurnDirection.Left)
    } else {

    }
}
function follow() {
    agent.move(FORWARD, 1)
    if (agent.inspect(AgentInspection.Block, FORWARD) == GRASS) {
        agent.destroy(UP)
        agent.move(UP, 1)
    } else if (!(agent.detect(AgentDetection.Block, DOWN))) {
        agent.move(DOWN, 1)
    } else {

    }
}
function turn() {
    agent.setAssist(DESTROY_OBSTACLES, true)
    if (flipturn) {
        agent.turn(TurnDirection.Right)
        agent.move(FORWARD, 3)
        agent.turn(TurnDirection.Right)
    } else {
        agent.turn(TurnDirection.Left)
        agent.move(FORWARD, 3)
        agent.turn(TurnDirection.Left)
    }
    flipturn = !(flipturn)
}
function chop() {
    height = 0
    while (agent.detect(AgentDetection.Block, FORWARD)) {
        height += 1
        agent.destroy(UP)
        agent.move(UP, 1)
    }
    for (let i = 0; i < height; i++) {
        agent.move(DOWN, 1)
        agent.destroy(FORWARD)
    }
    agent.collectAll()
}
```

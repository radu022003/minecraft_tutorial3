### @explicitHints 1  
# Aktivität: Baumjäger

## 1. Chopper-Befehl mit Starter-Code
Verwende den bereitgestellten Starter-Code. Erstelle den Chat-Befehl „chopper“.  
Erzeuge einen ``||PLAYER:Bei Chat-Befehl||``‑Block und benenne ihn in **"chopper"** um.

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

## 2. Parameter hinzufügen
Um die Größe des Suchgebiets festzulegen, fügen wir unserem „chopper“‑Chatbefehl einen Parameter hinzu, der die Länge einer Seite des quadratischen Suchgebiets darstellt.  
Klicke im Block ``||PLAYER:Bei Chat-Befehl "chopper"||`` auf das Pluszeichen **(+)**, um den Parameter **num1** hinzuzufügen. Benenne diesen über das Dropdown-Menü in **area** um.

### ~ tutorialhint
``` blocks
player.onChat("chopper", function(area) {

})
```

---

## 3. Suchen-Funktion erstellen
Erstelle die Funktion **suchen()**.  
Wir erstellen nun die restlichen Funktionen, die unser Programm bilden. Am Ende rufen wir alle Funktionen aus dem Block ``||PLAYER:Bei Chat-Befehl "chopper"||`` auf.

---

## 4. Suchlogik aufbauen
Füge Logik in die Funktion **suchen()** ein.  
Die Funktion **suchen()** soll den Agenten prüfen lassen, ob sich Bäume in seiner Umgebung befinden. Der Agent sucht dabei rechts, links und vor sich nach Holzblöcken, die auf einen Baum hinweisen. Findet er einen solchen Block, ruft er die Funktion *chop()* auf, um den Baum zu fällen.

---

## 5. If-Struktur vorbereiten
Ziehe einen ``||LOGIC:wenn dann ansonsten||``‑Block in die Funktion **suchen()**.  
Klicke in diesem Block zweimal auf das Pluszeichen **(+)**, um zwei zusätzliche ``||LOGIC:sonst wenn||``‑Klauseln zu erstellen.

---

## 6. Linke-Holz-Prüfung aufbauen
Suche nach Holz links:  
Ziehe einen ``||LOGIC:0 = 0||``‑Vergleichsblock heraus und platziere ihn in das erste Bedingungsfeld des ``||LOGIC:wenn||``‑Blocks.

---

## 7. Bedingung konfigurieren
Ziehe einen ``||AGENT:agent untersuche||``‑Block in das erste Feld des ``||LOGIC:0 = 0||``‑Blocks.  
Wähle im ``||AGENT:agent untersuche||``‑Block über das Dropdown-Menü die Richtung **links** aus.  
Ziehe einen ``||BLOCKS:block||``‑Block heraus und platziere ihn im zweiten Feld des Vergleichs.  
Wähle im ``||BLOCKS:block||``‑Block über das Dropdown-Menü ein **Eichenholz**‑Block oder einen anderen Baumtyp aus, den du durchsuchen möchtest.

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

## 8. Linksdrehung für Baumfall
Fällt den Baum links:  
Ziehe aus ``||AGENT:AGENT||`` einen ``||AGENT:Agent, drehe dich nach||``‑Block in den ersten Ast des ``||LOGIC:wenn dann||``‑Blocks.

### ~ tutorialhint
Wenn du links vom Agenten Holz findest, solltest du den Agenten nach links drehen und die Funktion chop() aufrufen, um den Baum zu fällen. Anschließend sollte sich der Agent wieder umdrehen und nach vorne blicken.

---

## 9. Drehung einrichten
Platziere einen ``||FUNCTIONS:Aufruf Funktion chop||``‑Block unterhalb des ``||AGENT:Agent, drehe dich nach||``‑Blocks.  
Dupliziere anschließend den ``||AGENT:Agent, drehe dich nach||``‑Block und platziere die Kopie unterhalb des ``||FUNCTIONS:Aufruf Funktion chop||``‑Blocks.  
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

## 10. Vorwärts-Holz-Prüfung kopieren
Suche nach Holz, das geradeaus gefällt werden kann.  
Du möchtest nun prüfen, ob sich vor dem Agenten ein Holzblock befindet. In diesem Fall muss der Agent nicht gedreht werden.  
Klicke auf die erste erstellte Bedingung und dupliziere sie. Platziere das Duplikat in das zweite Bedingungsfeld deines ``||LOGIC:wenn||``‑Blocks.

---

## 11. Richtung auf vorne setzen
Nimm nun einige Anpassungen vor:  
Ändere im duplizierten ``||AGENT:agent untersuche||``‑Block die Richtung zu **vorne**.  
Dupliziere den ``||FUNCTIONS:Aufruf Funktion chop||``‑Block und platziere ihn in diesem zweiten Ast.

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

## 12. Rechte-Holz-Prüfung kopieren
Suche nach Holz rechts:  
Dupliziere die erste Bedingung und platziere sie in den dritten Ast des ``||LOGIC:sonst wenn||``‑Blocks.

### ~ tutorialhint
Das ist im Grunde dasselbe wie links nach Holz zu suchen, nur dass einige Dinge umgekehrt sind.

---

## 13. Rechtsdrehung vorbereiten
Passe die Richtung in diesem Ast auf **rechts** an.  
Du benötigst zwei ``||AGENT:Agent, drehe dich nach||``‑Blöcke. Dupliziere zwei und platziere sie in den dritten Ast.

---

## 14. Block duplizieren
Dupliziere den ``||FUNCTIONS:Aufruf Funktion chop||``‑Block und platziere ihn zwischen den beiden ``||AGENT:Agent, drehe dich nach||``‑Blöcken.  
Passe anschließend die Drehungen an: Dieses Mal dreht sich der Agent zuerst nach rechts, fällt den Baum und dreht sich dann wieder nach links, um in seine Ausgangsrichtung zurückzukehren.

---

## 15. Leeren Else-Zweig belassen
Der letzte **ansonsten**‑Ast deines ``||LOGIC:wenn||``‑Blocks bleibt leer.

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

## 16. Hindernisse-Zerstörung aktivieren
Erlaube dem Agenten, Hindernisse auf seinem Weg zu zerstören.  
Der Agent verfügt über einen Block, der ihm zusätzliche Fähigkeiten verleiht – er kann damit automatisch Blöcke platzieren, wenn er sich bewegt, und Blöcke aus jedem Inventarslot verwenden, statt nur aus dem oberen linken Slot.  
Ziehe einen ``||AGENT:Agent platziere bei Bewegung||``‑Block in den Block ``||PLAYER:Bei Chat-Befehl "chopper"||`` und wähle im Dropdown-Menü **Hindernisse zerstören** aus.

### ~ tutorialhint
Schau dir an, welche weiteren coolen Funktionen dieser Block hat – du findest sie in der Hilfe! Mit ihm kann dein Agent automatisch Blöcke platzieren, während er sich bewegt, und auch Blöcke aus jedem Slot seines Inventars verwenden, statt nur den oberen linken Slot.

---

## 17. Auswahl treffen
Wähle abschließend **EIN**.

---

## 18. Flipturn-Variable initialisieren
Steuere die Drehung des Agenten.  
Am Ende jeder Reihe soll sich der Agent umdrehen.  
Erstelle dazu eine Boolean‑Variable, um festzuhalten, in welche Richtung gedreht werden soll. Wir verwenden ``||LOGIC:Wahr||`` für eine Rechtsdrehung und ``||LOGIC:Falsch||`` für eine Linksdrehung.  
Nach der Drehung wird die Boolean‑Variable umgeschaltet.  
Die Variable **flipturn** wurde bereits im Starter-Code dieser Aktivität angelegt.  
Ziehe einen ``||VARIABLES:setze||``‑Block in den Block ``||PLAYER:Bei Chat-Befehl "chopper"||`` und wähle über das Dropdown-Menü **flipturn** aus.

---

## 19. Startwert auf falsch setzen
Ziehe einen ``||LOGIC:Falsch||``‑Block in den Setz‑Block und ersetze damit die **0**.

### ~ tutorialhint
``` blocks
let flipturn = false
player.onChat("chopper", function(area) {
    agent.setAssist(DESTROY_OBSTACLES, true)
    flipturn = false;
})
```

---

## 20. Suchpfad durch Gitter planen
Nun ist alles vorbereitet. Jetzt müssen wir den Agenten durch das Suchgebiet bewegen:  
Der Agent soll eine Reihe des Gitters hinuntergehen, sich am Ende wenden und dann weitere Reihen abgehen, bis das quadratische Gebiet vollständig durchsucht wurde.

---

## 21. Funktionen im Chopper aufrufen
Füge die Funktionen **suchen()** und **follow()** in den Chatbefehl ein.  
Nachdem alle Funktionen erstellt wurden, bringen wir nun alles zusammen.  
Bei jedem Schritt soll der Agent nach Bäumen suchen und dem Geländeverlauf folgen. Dabei sucht er gleichzeitig in drei Richtungen (links, rechts und geradeaus).

---

## 22. Reihen-Schleife einfügen
Ziehe einen ``||LOOPS:-mal wiederholen||``‑Block in den Block ``||PLAYER:Bei Chat-Befehl "chopper"||`` und platziere ihn unterhalb des ``||VARIABLES:setze flipturn||``‑Blocks.

---

## 23. Parameter hinzufügen
Denke daran, dass der Parameter **area** die Anzahl der Blöcke in jeder Reihe angibt.  
Ziehe ``||VARIABLES:area||`` in den ``||LOOPS:-mal wiederholen||``‑Block und ersetze damit den Standardwert **4**.  
Nun wird der Agent alle Blöcke einer Reihe durchsuchen – so viele, wie der Benutzer angibt.  
Ziehe anschließend die Blöcke ``||FUNCTIONS:Aufruf Funktion suchen||`` und ``||FUNCTIONS:Aufruf Funktion follow||`` in die Wiederholungsschleife.

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

## 24. Drehung einrichten
Füge die Funktion **turn()** hinzu, damit sich der Agent am Ende jeder Reihe wendet.  
Ziehe den Block ``||FUNCTIONS:Aufruf Funktion turn||`` unterhalb der ``||LOOPS:-mal wiederholen||``‑Schleife.

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

## 25. Äußere Flächenschleife ergänzen
Erstelle ein vollständiges quadratisches Suchgitter.  
Du musst dazu eine weitere ``||LOOPS:SCHLEIFEN||``‑Schleife hinzufügen, damit der Agent das gesamte Gebiet durchsucht und ein Quadrat bildet, anstatt nur eine Reihe (bzw. drei Reihen) abzuarbeiten.

---

## 26. Bereich auf Drittel skalieren
Da der Agent in jedem Schritt drei Blöcke durchsucht, muss nicht die gesamte, angegebene Fläche geloopt werden.  
Teile den Wert von **area** durch 3. Im folgenden Beispiel durchsucht der Agent ein 9×9‑Gitter, benötigt aber nur 3 Wiederholungen, um alle Reihen abzugehen.  
Füge dazu eine weitere ``||LOOPS:-mal wiederholen||``‑Schleife ein, die alles unterhalb des Blocks ``||VARIABLES:setze flipturn||`` einschließt.

---

## 27. Division in Schleife einsetzen
Ziehe einen ``||Math:0 / 0||``‑Block in die neue ``||LOOPS:-mal wiederholen||``‑Schleife und ersetze damit den Standardwert **4**.

---

## 28. Area-Teilung konfigurieren
Ziehe ``||VARIABLES:area||`` in das erste Feld des ``||Math:0 ÷ 0||``‑Blocks.  
Gib im zweiten Feld des Blocks den Wert **3** ein.  
Um das Ganze zu testen, teleportiere deinen Agenten zunächst zu deiner Position mit dem bereitgestellten ``||PLAYER:Bei Chat-Befehl "tp"||``‑Befehl.

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

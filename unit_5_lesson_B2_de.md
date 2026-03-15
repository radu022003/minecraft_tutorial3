### @explicitHints 1  

# Aktivität: Agent-Baumfäller  

## 1. Chat-Befehl anlegen
Benenne den vorhandenen ``||PLAYER:bei Chat-Befehl||``-Block in **"tp"** um. Ziehe einen ``||AGENT:Agent teleportiere dich zu Spieler||``-Block in den ``||PLAYER:bei Chat-Befehl "tp"||``-Block.  

---

## 2. Block duplizieren
Erstelle nun einen Befehl, um den Agenten zu drehen. Du kannst den vorhandenen ``||PLAYER:bei Chat-Befehl "tp"||``-Block mit Rechtsklick **duplizieren**.  

Benenne die Kopie in **"lt"** um.  

---

## 3. Block duplizieren
Entferne den Inhalt des duplizierten Blocks und ersetze ``||AGENT:Agent teleportiere zu Spieler||`` durch ``||AGENT:Agent drehe dich nach 'links'||``.  

### ~ tutorialhint  
```blocks  
player.onChat("tp", function () {
    agent.teleportToPlayer()
})
player.onChat("lt", function () {
    agent.turn(TurnDirection.Left)
})
```  

---

## 4. Chat-Befehl anlegen
Erstelle die Höhen-Variable. Ziehe einen neuen ``||PLAYER:bei Chat-Befehl||``-Block in den Arbeitsbereich und benenne ihn in **"chop"** um.  

Du wirst eine Variable verwenden, um die Höhe des Baums zu verfolgen. Öffne das ``||VARIABLES:Variablen||``-Werkzeugmenü und klicke auf **Variable erstellen**. Nenne die neue Variable **höhe**.  

---

## 5. Höhe initialisieren
Ziehe einen ``||VARIABLES:setze||``-Block in den ``||PLAYER:bei Chat-Befehl "chop"||``-Block.  
Wähle im ``||VARIABLES:setze||``-Block im Dropdown-Menü die Variable **höhe** und setze sie auf **0**.

### ~ tutorialhint  
```blocks  
let höhe = 0
player.onChat("tp", function () {
    agent.teleportToPlayer()
})
player.onChat("lt", function () {
    agent.turn(TurnDirection.Left)
})
player.onChat("chop", function () {
    höhe = 0
})
```  

---

## 6. Bedingung konfigurieren
Beginne am Fuß eines Baums. Gehe davon aus, dass der Agent auf den Baumstamm zeigt, wenn der **"chop"**-Befehl gegeben wird. Nutze die Befehle **"tp"** und **"lt"**, um deinen Agenten auszurichten, und führe anschließend **"chop"** aus.

Verwende eine ``||LOOPS:während||``-Schleife, die den Code wiederholt, solange ein Block vor dem Agenten ist.  

---

## 7. Während-Schleife einfügen
Ziehe eine ``||LOOPS:während||``-Schleife und lege sie unter den ``||VARIABLES:setze 'höhe'||``-Block im ``||PLAYER:bei Chat-Befehl "chop"||``-Block.  

---

## 8. Blockerkennung einfügen
Ziehe einen ``||AGENT:Agent erkenne 'Block' 'vorwärts'||``-Block in die Bedingung der ``||LOOPS:während||``-Schleife, um **falsch** zu ersetzen.  

### ~ tutorialhint  
```blocks  
let höhe = 0
player.onChat("tp", function () {
    agent.teleportToPlayer()
})
player.onChat("lt", function () {
    agent.turn(TurnDirection.Left)
})
player.onChat("chop", function () {
    höhe = 0
    while (agent.detect(AgentDetection.Block, FORWARD)) {

    }
})
```  

---

## 9. Variable konfigurieren
Bewege dich den Baum hinauf. Ziehe einen ``||VARIABLES:ändere||``-Block in die ``||LOOPS:während||``-Schleife und stelle ein, dass **höhe** um **1** erhöht wird.  

---

## 10. Oberen Block zerstören
Falls Blätter oder Äste über dem Agenten sind, müssen sie zerstört werden. Platziere einen ``||AGENT:Agent zerstöre||``-Block direkt unter dem ``||VARIABLES:ändere 'höhe' um 1||``-Block. Wähle **oben** aus dem Dropdown-Menü.  

---

## 11. Nach oben bewegen
Lass den Agenten aufsteigen. Füge einen ``||AGENT:Agent bewege||``-Block hinzu und wähle im Dropdown-Menü **oben** als Richtung.  

### ~ tutorialhint  
```blocks  
let höhe = 0
player.onChat("tp", function () {
    agent.teleportToPlayer()
})
player.onChat("lt", function () {
    agent.turn(TurnDirection.Left)
})
player.onChat("chop", function () {
    höhe = 0
    while (agent.detect(AgentDetection.Block, FORWARD)) {
        höhe += 1
        agent.destroy(UP)
        agent.move(UP, 1)
    }
})
```  

---

## 12. Abstiegsschleife einfügen
Lass den Agenten wieder herunterkommen. Ziehe eine ``||LOOPS:wiederhole||``-Schleife unter die ``||LOOPS:während||``-Schleife.  

---

## 13. Höhe als Schleifenwert nutzen
Ziehe die Variable ``||VARIABLES:höhe||``  in die ``||LOOPS:wiederhole||``-Schleife, um die Zahl **4** zu ersetzen.  

### ~ tutorialhint  
```blocks  
let höhe = 0
player.onChat("tp", function () {
    agent.teleportToPlayer()
})
player.onChat("lt", function () {
    agent.turn(TurnDirection.Left)
})
player.onChat("chop", function () {
    höhe = 0
    while (agent.detect(AgentDetection.Block, FORWARD)) {
        höhe += 1
        agent.destroy(UP)
        agent.move(UP, 1)
    }
    for (let i = 0; i < höhe; i++) {

    }
})
```  

---

## 14. Abstiegscode ergänzen
Fälle während des Abstiegs. Füge innerhalb der ``||LOOPS:wiederhole||``-Schleife einen ``||AGENT:Agent bewege||``-Block hinzu, gefolgt von einem ``||AGENT:Agent zerstöre||``-Block.  

---

## 15. Auswahl treffen
Stelle sicher, dass der Agent nach unten geht und die Blöcke vor sich zerstört. Im ``||AGENT:Agent bewege||``-Block wähle **unten** als Richtung.  

---

## 16. Holz einsammeln
Sammle alles Holz ein. Füge am Ende des ``||PLAYER:bei Chat-Befehl "chop"||``-Blocks einen ``||AGENT:Agent sammle alles ein||``-Block hinzu.  

### ~ tutorialhint  
```blocks  
let höhe = 0
player.onChat("tp", function () {
    agent.teleportToPlayer()
})
player.onChat("lt", function () {
    agent.turn(TurnDirection.Left)
})
player.onChat("chop", function () {
    höhe = 0
    while (agent.detect(AgentDetection.Block, FORWARD)) {
        höhe += 1
        agent.destroy(UP)
        agent.move(UP, 1)
    }
    for (let i = 0; i < höhe; i++) {
        agent.move(DOWN, 1)
        agent.destroy(FORWARD)
    }
    agent.collectAll()
})
```  

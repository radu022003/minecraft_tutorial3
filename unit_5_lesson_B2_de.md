### @explicitHints 1  

# Aktivität: Agent-Baumfäller  

## Schritt 1  
Benenne den vorhandenen ``||Player:bei Chat-Befehl||``-Block in **"tp"** um. Ziehe einen ``||Agent:Agent teleportiere dich zu Spieler||``-Block in den ``||Player:bei Chat-Befehl "tp"||``-Block.  

---

## Schritt 2  
Erstelle nun einen Befehl, um den Agenten zu drehen. Du kannst den vorhandenen ``||Player:bei Chat-Befehl "tp"||``-Block mit Rechtsklick **duplizieren**.  

Benenne die Kopie in **"lt"** um.  

---

## Schritt 3  
Entferne den Inhalt des duplizierten Blocks und ersetze ``||Agent:Agent teleportiere zu Spieler||`` durch ``||Agent:Agent drehe dich nach 'links'||``.  

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

## Schritt 4  
Erstelle die Höhen-Variable. Ziehe einen neuen ``||Player:bei Chat-Befehl||``-Block in den Arbeitsbereich und benenne ihn in **"chop"** um.  

Du wirst eine Variable verwenden, um die Höhe des Baums zu verfolgen. Öffne das ``||Variables:Variablen||``-Werkzeugmenü und klicke auf **Variable erstellen**. Nenne die neue Variable **höhe**.  

---

## Schritt 5  
Ziehe einen ``||Variables:setze||``-Block in den ``||Player:bei Chat-Befehl "chop"||``-Block.  
Wähle im ``||Variables:setze||``-Block im Dropdown-Menü die Variable **höhe** und setze sie auf **0**.

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

## Schritt 6 
Beginne am Fuß eines Baums. Gehe davon aus, dass der Agent auf den Baumstamm zeigt, wenn der **"chop"**-Befehl gegeben wird. Nutze die Befehle **"tp"** und **"lt"**, um deinen Agenten auszurichten, und führe anschließend **"chop"** aus.  

Verwende eine ``||Loops:während||``-Schleife, die den Code wiederholt, solange ein Block vor dem Agenten ist.  

---

## Schritt 7 
Ziehe eine ``||Loops:während||``-Schleife und lege sie unter den ``||Variables:setze 'höhe'||``-Block im ``||Player:bei Chat-Befehl "chop"||``-Block.  

---

## Schritt 8 
Ziehe einen ``||Agent:Agent erkenne 'Block' 'vorwärts'||``-Block in die Bedingung der ``||Loops:während||``-Schleife, um **falsch** zu ersetzen.  

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

## Schritt 9 
Bewege dich den Baum hinauf. Ziehe einen ``||Variables:ändere||``-Block in die ``||Loops:während||``-Schleife und stelle ein, dass **höhe** um **1** erhöht wird.  

---

## Schritt 10 
Falls Blätter oder Äste über dem Agenten sind, müssen sie zerstört werden. Platziere einen ``||Agent:Agent zerstöre||``-Block direkt unter dem ``||Variables:ändere 'höhe' um 1||``-Block. Wähle **oben** aus dem Dropdown-Menü.  

---

## Schritt 11
Lass den Agenten aufsteigen. Füge einen ``||Agent:Agent bewege||``-Block hinzu und wähle im Dropdown-Menü **oben** als Richtung.  

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

## Schritt 12 
Lass den Agenten wieder herunterkommen. Ziehe eine ``||Loops:wiederhole||``-Schleife unter die ``||Loops:während||``-Schleife.  

---

## Schritt 13 
Ziehe die Variable ``||Variables:höhe||``  in die ``||Loops:wiederhole||``-Schleife, um die Zahl **4** zu ersetzen.  

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

## Schritt 14  
Fälle während des Abstiegs. Füge innerhalb der ``||Loops:wiederhole||``-Schleife einen ``||Agent:Agent bewege||``-Block hinzu, gefolgt von einem ``||Agent:Agent zerstöre||``-Block.  

---

## Schritt 15  
Stelle sicher, dass der Agent nach unten geht und die Blöcke vor sich zerstört. Im ``||Agent:Agent bewege||``-Block wähle **unten** als Richtung.  

---

## Schritt 16 
Sammle alles Holz ein. Füge am Ende des ``||Player:bei Chat-Befehl "chop"||``-Blocks einen ``||Agent:Agent sammle alles ein||``-Block hinzu.  

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

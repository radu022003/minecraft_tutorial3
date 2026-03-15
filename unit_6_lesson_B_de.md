### @explicitHints 1

# Aktivität: Blitzschwein-Arena

## 1. Zombie-Schwein-Funktion erstellen
Erstelle eine ``||FUNCTIONS:Funktion||`` mit dem Namen **zombiepig**.

## 2. Setup- und Atmosphäre-Funktionen erstellen
Erstelle zwei weitere ``||FUNCTIONS:Funktionen||`` mit den Namen **atmosphere** und **setup**.

## 3. Chat-Befehl anlegen
Ziehe einen ``||PLAYER:Bei Chat-Befehl||``-Block auf die Arbeitsfläche und benenne ihn zu **"play"**.

## 4. Alle Funktionen aufrufen verbinden
Ziehe die drei Blöcke ``||FUNCTIONS:aufruf setup||``, ``||FUNCTIONS:aufruf atmosphere||`` und ``||FUNCTIONS:aufruf zombiepig||`` in den **bei Chat-Befehl "play"**-Block.

### ~ tutorialhint
``` blocks
function zombiepig()  {

}
function atmosphere()  {

}
player.onChat("play", function () {
    setup()
    atmosphere()
    zombiepig()
})
function setup()  {

}
```

## 5. Spawn konfigurieren
Ziehe einen ``||MOBS:spawne Tier||`` Block in ``||FUNCTIONS:function zombie pig||``. 

Ändere das Tier zum **Schwein**. 


## 6. Blitzeffekt mit Schwein kombinieren
Ziehe noch einen ``||MOBS:spawne Tier||`` Block in ``||FUNCTIONS:function zombie pig||`` und ersetze **Tier** mit ``||MOBS:Projektil Blitz||``.

Dann setze beide Koordinaten auf **(~0, ~0, ~-5)**.

### ~ tutorialhint
``` blocks
function zombiepig() {
    mobs.spawn(PIG, pos(0, 0, -5))
    mobs.spawn(LIGHTNING_BOLT, pos(0, 0, -5))
}
player.onChat("play", function () {
    setup()
    atmosphere()
    zombiepig()
})
function setup()  {

}
function atmosphere()  {

}
```

## 7. Schwierigkeit einstellen
Du möchtest, dass das Spiel automatisch funktioniert. Nachdem du "play" eingibst, soll das Spiel mit allem eingerichtet werden, sodass du ein paar verrückte Zombie-Schweine-Menschen bekämpfen kannst. Das erste Problem ist der Schwierigkeitsgrad des Spiels. Das Schwein wird sich nicht in ein Zombie-Schwein verwandeln, wenn das Spiel auf Friedlich eingestellt ist.

## 8. Schwierigkeit einstellen
Ziehe einen ``||GAMEPLAY:Stelle Schwierigkeit ein auf||`` Block in ``||FUNCTIONS:setup||``.

Passe diesen neuen Block so an, dass er ``||GAMEPLAY:stelle Schwierigkeit ein auf 'normal'||`` lautet.

## 9. Spielmodus festlegen
Als Nächstes möchtest du den Spielmodus für den Spieler ändern. Durch Einstellen des Spielmodus auf Überleben wird sichergestellt, dass der Schweinemensch dich angreift!

Ziehe einen ``||GAMEPLAY:Ändere Spielmodus zu||``-Block in ``||FUNCTIONS:Setup||``.

Passe diesen neuen Block so an, dass er ``||GAMEPLAY:ändere Spielmodus zu 'Überleben'||`` lautet.

Ändere auch das Ziel, sodass es **"du selbst"** lautet.

## 10. Diamantschwert austeilen
Schließlich wird es sehr schwierig sein zu kämpfen, ohne eine Waffe zu haben. Du kannst dir selber eine Waffe geben, um das Spiel für deinen Spieler vernünftiger zu gestalten. 

Ziehe einen ``||MOBS:Gib||``-Block und platziere ihn als letzten Block in die ``||FUNCTIONS:function Setup||``.

## 11. Auswahl treffen
Du musst dich selber als Ziel wählen und dir selber ein Schwert oder eine andere Waffe geben. Z.B. ein **Diamantschwert**.
Dazu brauchst du ein ``||MOBS:gib Block oder Element||``-Block und ein ``||BLOCKS:Element||``-Block. 

### ~ tutorialhint
``` blocks
function atmosphere()  {

}
function setup() {
    gameplay.setDifficulty(EASY)
    gameplay.setGameMode(
    SURVIVAL,
    mobs.target(LOCAL_PLAYER)
    )
    mobs.give(
    mobs.target(LOCAL_PLAYER),
    blocks.item(DIAMOND_SWORD),
    1
    )
}
function zombiepig() {
    mobs.spawn(PIG, pos(0, 0, -5))
    mobs.spawn(LIGHTNING_BOLT, pos(0, 0, -5))
}
player.onChat("play", function () {
    setup()
    atmosphere()
    zombiepig()
})
```


## 12. Mitternacht-Atmosphäre setzen
Ziehe einen ``||GAMEPLAY:Zeiteinstellung||``-Block in ``||FUNCTIONS:function atmosphere||``.

Passe dies so an, dass es ``||GAMEPLAY:Zeiteinstellung 'Mitternacht'||`` lautet. 

Jetzt kannst du **play** in den Chat eingeben und deinen Code testen. 

### ~ tutorialhint
``` blocks
function atmosphere() {
    gameplay.timeSet(gameplay.time(MIDNIGHT))
}
function setup() {
    gameplay.setDifficulty(EASY)
    gameplay.setGameMode(
    SURVIVAL,
    mobs.target(LOCAL_PLAYER)
    )
    mobs.give(
    mobs.target(LOCAL_PLAYER),
    blocks.item(DIAMOND_SWORD),
    1
    )
}
function zombiepig() {
    mobs.spawn(PIG, pos(0, 0, -5))
    mobs.spawn(LIGHTNING_BOLT, pos(0, 0, -5))
}
player.onChat("play", function () {
    setup()
    atmosphere()
    zombiepig()
})
```

## 13. Respawn-Event vorbereiten
Nachdem ein Schweinemensch besiegt wurde, möchtest du, dass ein weiterer Schweinemensch erscheint. 

## 14. Mob-Filter einstellen
Ziehe einen ``||MOBS:wenn getötet||``-Block.

Passe diesen Block so an, dass es ``||MOBS:wenn Monster Zombie-Pigman getötet||`` lautet.

## 15. Zombiepig erneut aufrufen
Ziehe einen ``||FUNCTIONS:aufruf zombiepig||``-Block zu diesem neuen Ereignis hinzu.

Jetzt kannst du **play** in den Chat eingeben und deinen Code testen. 

### ~ tutorialhint
``` blocks
function setup() {
    gameplay.setDifficulty(EASY)
    gameplay.setGameMode(
    SURVIVAL,
    mobs.target(LOCAL_PLAYER)
    )
    mobs.give(
    mobs.target(LOCAL_PLAYER),
    blocks.item(DIAMOND_SWORD),
    1
    )
}
mobs.onMobKilled(mobs.monster(PIG_ZOMBIE), function () {
    zombiepig()
})
function atmosphere() {
    gameplay.timeSet(gameplay.time(MIDNIGHT))
}
function zombiepig() {
    mobs.spawn(PIG, pos(0, 0, -5))
    mobs.spawn(LIGHTNING_BOLT, pos(0, 0, -5))
}
player.onChat("play", function () {
    setup()
    atmosphere()
    zombiepig()
})
```


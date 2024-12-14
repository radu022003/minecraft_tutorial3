### @explicitHints 1

# Aktivität: Zombie Schwein 

## Schritt 1
Erstelle eine ``||Functions:Funktion||`` mit dem Namen **zombipig**.

## Schritt 2
Erstelle zwei weitere ``||Functions:Funktionen||`` mit den Namen **atmosphere** und **setup**.

## Schritt 3
Ziehe einen ``||Player:Bei Chat-Befehl||``-Block auf die Arbeitsfläche und benenne es zum **"play"**.

## Schritt 4
Ziehe die drei Blöcke ``||Functions:aufruf setup||``, ``||Functions:aufruf atmosphere||`` und ``||Functions:aufruf zombiepig||`` in den ``||Blocks:Bei Chat-Befehl "play"||``-Block.

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

## Schritt 5: Zombie-Schwein erstellen
Ziehe einen ``||Mobs:spawne Tier||`` Block in ``||Functions:function zombie pig||``. 

Ändere das Tier zum **Schwein**. 


## Schritt 6
Ziehe noch einen ``||Mobs:spawne Tier||`` Block in ``||Functions:function zombie pig||`` und ersetze **Tier** mit ``||Mobs:Projektil Blitz||``.

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

## Schritt 7
Einstellungen anpassen. Sie möchten, dass das Spiel automatisch funktioniert. Nachdem Sie "play" eingeben, soll das Spiel mit allem eingerichtet werden, sodass Sie ein paar verrückte Zombie-Schweine-Menschen bekämpfen können. Das erste Problem ist der Schwierigkeitsgrad des Spiels. Das Schwein wird sich nicht in ein Zombie-Schwein verwandeln, wenn das Spiel auf Friedlich eingestellt ist.

## Schritt 8
Ziehe einen ``||Gameplay:Stelle Schwierigkeit ein auf||`` Block in ``||Functions:setup||``.

Passe diesen neuen Block so an, dass er ``||Gameplay:stelle Schwierigkeit ein auf 'normal'||`` lautet.

## Schritt 9
Als nächstes möchten Sie den Spielmodus für Ihren Spieler ändern. Durch Einstellen des Spielmodus auf Überlebensmodus wird sichergestellt, dass der Schweinmensch hinter Ihnen herkommt! 

Ziehe einen ``||Gameplay:Ändere Spielmodus zu||``-Block in ``||Functions:Setup||``.

Passe diesen neuen Block so an, dass er ``||Gameplay:ändere Spielmodus zu 'Überleben'||`` lautet.

Ändereauch das Ziel, sodass es **"du selbst"** lautet.

## Schritt 10
Schließlich wird es sehr schwierig sein zu kämpfen, ohne eine Waffe zu haben. Du kannst dir selber eine Waffe geben, um das Spiel für deinen Spieler vernünftiger zu gestalten. 

Ziehe einen ``||Mobs:Gib||``-Block und platziere ihn als letzten Block in die ``||Functions:function Setup||``.

## Schritt 11
Du musst dich selber als Ziel wählen und dir selber ein Schwert oder eine andere Waffe geben. Z.B. ein **Diamantschwert**.

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


## Schritt 12
Ziehe einen ``||Gameplay:Zeiteinstellung||``-Block in ``||Functions:function atmosphere||``.

Passe dies so an, dass es ``||Gameplay:Zeiteinstellung 'Mitternacht'||`` lautet. 

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

## Schritt 13
Nachdem ein Schweinemensch besiegt wurde, möchtest du, dass ein weiterer Schweinemensch erscheint. 

## Schritt 14
Ziehe einen ``||Mobs:wenn getötet||``-Block.

Passe diesen Block so an, dass es ``||Mobs:wenn Monster Zombie-Pigman getötet||`` lautet.

## Schritt 15
Ziehe einen ``||Functions:aufruf zombiepig||``-Block zu diesem neuen Ereignis hinzu.

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


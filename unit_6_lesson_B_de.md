### @explicitHints 1

# Aktivität: Zombie Schwein 

## Schritt 1
In der ``||Functions:FUNKTIONEN||``-Werkzeugleisten-Schublade klicken Sie auf die Schaltfläche **Erstelle eine Funktion**. Benennen Sie diese Funktion **zombiepig**, und klicken Sie auf **OK**.

## Schritt 2
Erstellen Sie die Funktionen platform() und teleport(). Wiederholen Sie den vorherigen Schritt, um zwei weitere Funktionen mit den Namen **atmosphere** und **setup** zu erstellen.

## Schritt 3
Ziehen Sie ``||Player:Bei Chat-Befehl||`` auf die Arbeitsfläche.

Benennen Sie ``||Player:Bei Chat-Befehl||`` zum **"play"**.

## Schritt 4
Ziehen Sie die drei Blöcke ``||Functions:aufruf function setup||``, ``||Functions:aufruf function atmosphere||`` und ``||Functions:aufruf function zombiepig||`` in ``||Blocks:Bei Chat-Befehl "play"||``.

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

## Schritt 5
Erstellen Sie das Zombie-Schwein. Ziehen Sie einen ``||Mobs:spawne Tier||`` Block in ``||Functions:zombie pig||``. Ändern Sie das Tier, indem Sie **Schwein** aus dem Dropdown-Menü auswählen. Ändern Sie dann die Position in der Z-Koordinate, um ein Schwein fünf Blöcke nördlich des Spielers erscheinen zu lassen.

Erstellen Sie einen weiteren Spawne-Block und platzieren Sie ihn unterhalb des ersten. Ersetzen Sie **Tier** durch einen Projektil-Blitz.

## Schritt 6
Geben Sie die gleichen Koordinaten ein, die für das Schwein verwendet wurden: **(~0, ~0, ~-5)**. Der Trick hierbei ist, dass wenn ein Schwein von einem Blitz getroffen wird, es sich in ein Zombie-Schweinmenschen verwandelt! Deshalb möchten Sie beide an den gleichen Koordinaten **(~0, ~0, ~-5)** spawnen.

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
Ziehen Sie einen ``||Gameplay:Stelle Schwierigkeit ein auf||`` Block in ``||Function:setup||``.

Passen Sie diesen neuen Block so an, dass er ``||Gameplay:stelle Schwierigkeit ein auf 'normal'||`` lautet.

## Schritt 9
Als nächstes möchten Sie den Spielmodus für Ihren Spieler ändern. Durch Einstellen des Spielmodus auf Überlebensmodus wird sichergestellt, dass der Schweinmensch hinter Ihnen herkommt! Sobald Sie den Schweinmenschen treffen, wird er anfangen, zurückzuschlagen! Ziehen Sie ein ``||Gameplay:Ändere Spielmodus zu||`` in ``||Function:Setup||``.

Passen Sie diesen neuen Block so an, dass er ``||Gameplay:ändere Spielmodus zu 'Überleben'||`` lautet.

Ändern Sie auch das Ziel, sodass es "du selbst" anvisiert.

## Schritt 10
Schließlich wird es sehr schwierig sein zu kämpfen, ohne eine Waffe zu haben. Sie können sich selbst eine Waffe geben, um das Spiel für Ihren Spieler vernünftiger zu gestalten. Holen Sie sich einen ``||Mobs:Gib||`` Block und platzieren Sie ihn als letzten Block in der ``||Function:Setup||`` Funktion.

## Schritt 11
Sie müssen sich selbst als Ziel wählen und sich selbst ein Schwert oder eine andere Waffe geben. Das Beispiel gibt ein Diamantschwert.

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
An diesem Punkt können Sie Ihr Spiel testen! Durch Eingabe von "play" im Chatfenster wird das Minispiel gestartet.

## Schritt 13
Passen Sie die Zeit an. Der letzte Schritt für dieses Minispiel besteht darin, visuelle Effekte hinzuzufügen, indem Sie die Tageszeit anpassen. Dadurch entsteht die entsprechende Atmosphäre, die alle Zombies benötigen. Sie werden einen **Zeiteinstellung** Block hinzufügen.

## Schritt 14
Ein Minecraft-Tag dauert 24.000 Ticks für 20 Minuten Spielzeit. Indem Sie das Spiel auf Mitternacht einstellen, setzen Sie die aktuelle Zeit auf den Beginn der Mitternacht. Zeit setzen Blöcke sind eine einfache Möglichkeit, die Zeit auf einen gemeinsamen Teil des Tages zu setzen. Mitternacht entspricht 18.000 Ticks (00:00 Uhr).

## Schritt 15
Ziehen Sie einen ``||Gameplay:Zeiteinstellung||`` Block in die ``||Functions:atmosphere||`` Funktion.

Passen Sie dies so an, dass es ``||Gameplay:Zeiteinstellung 'Mitternacht'||`` lautet. Probieren Sie es in Minecraft aus!

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

## Schritt 16
Zeit ändert sich nicht? Stellen Sie sicher, dass die Option **Immer Tag** nicht aktiviert ist.

Spawnen Sie zusätzliche Schweinmenschen. Nachdem ein Schweinmensch besiegt wurde, möchten Sie, dass ein weiterer Schweinmensch erscheint. Sie können einen neuen Schweinmenschen mit dem Ereignis ``||Mobs:wenn getötet||`` erstellen. Sie werden die Funktion ``||Agent:aufruf Schweinmenschen||`` verwenden.

## Schritt 17
Holen Sie sich ein ``||Mobs:wenn getötet||`` Ereignis und platzieren Sie es auf der Arbeitsfläche.

Passen Sie diesen Block so an, dass es ``||Mobs:wenn getötet||`` lautet.

## Schritt 18
Fügen Sie ein ``||Functions:aufruf Funktion Zombie-Schwein||`` zu diesem neuen Ereignis hinzu.

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


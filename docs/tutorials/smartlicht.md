# 👏 Smartlicht

## Einleitung @showdialog

Kennst du Lampen, die man mit **Klatschen** ein- und ausschaltet?

Heute programmierst du genau so eine Lampe! Der @boardname@ hört auf Geräusche – wenn du in die Hände klatschst, leuchten die RGB-LEDs auf. Nach **5 Sekunden** gehen sie automatisch wieder aus.

## Schritt 1 – Das Mikrofon @showdialog

Der Calliope mini 3 hat ein eingebautes **Mikrofon**, das Lautstärke messen kann.

Die Lautstärke wird als Zahl von **0** (still) bis **255** (sehr laut) angegeben.

Du findest den Block unter ``||input:Eingabe||`` → „Lautstärke".

Ein Klatschen erzeugt typischerweise einen Wert über **100** – das nutzen wir als Signal!

## Schritt 2 – Dauerhaft die Lautstärke prüfen

Unser Programm soll **immer** lauschen. Dafür nutzen wir den ``||basic:dauerhaft||``-Block.

Darin prüfen wir: **Ist die Lautstärke größer als 100?**

```blocks
basic.forever(function () {
    if (input.soundLevel() > 100) {
    }
})
```

## Schritt 3 – Eine Variable für den Lampen-Status

Damit wir wissen, ob die Lampe gerade an oder aus ist, brauchen wir eine Variable.

Erstelle eine Variable namens **lampeAn** und setze sie am Start auf **0** (= aus).

```blocks
let lampeAn = 0
basic.forever(function () {
    if (input.soundLevel() > 100) {
    }
})
```

## Schritt 4 – Lampe einschalten

Wenn es einen lauten Geräusch gibt **und** die Lampe gerade aus ist, soll sie angehen.

- Setze `lampeAn` auf **1**
- Schalte die RGB-LEDs auf eine Farbe deiner Wahl (z. B. Gelb = warmweißes Licht)
- Zeige ein Glühbirnen-Symbol auf der LED-Matrix

```blocks
let lampeAn = 0
basic.forever(function () {
    if (input.soundLevel() > 100 && lampeAn == 0) {
        lampeAn = 1
        basic.setLedColor(0xffff00)
        basic.showIcon(IconNames.Diamond)
    }
})
```

## Schritt 5 – Automatisch nach 5 Sekunden ausschalten

Jetzt kommt der automatische Ausschalter! Nach dem Einschalten:

1. Warte **5000 Millisekunden** (= 5 Sekunden)
2. Schalte die RGB-LEDs aus (Farbe Schwarz)
3. Lösche das Symbol auf der LED-Matrix
4. Setze `lampeAn` wieder auf **0**

```blocks
let lampeAn = 0
basic.forever(function () {
    if (input.soundLevel() > 100 && lampeAn == 0) {
        lampeAn = 1
        basic.setLedColor(0xffff00)
        basic.showIcon(IconNames.Diamond)
        basic.pause(5000)
        basic.setLedColor(0x000000)
        basic.clearScreen()
        lampeAn = 0
    }
})
```

## Schritt 6 – Warum brauchen wir die Variable „lampeAn"? @showdialog

Gute Frage! 🤔

Ohne die Variable würde jedes Geräusch die Lampe sofort neu starten – auch wenn sie gerade erst angegangen ist!

Mit `lampeAn == 0` prüfen wir zuerst: **Ist die Lampe überhaupt aus?** Nur dann reagieren wir auf das Klatschen.

Das nennt man in der Programmierung einen **Zustand** – das Programm „weiß", ob es gerade schläft oder wach ist.

## Schritt 7 – Testen und verfeinern

Teste dein Programm im Simulator – klicke auf das Mikrofon-Symbol.

Dann lade es auf deinen @boardname@ und teste mit echtem Klatschen!

```blocks
let lampeAn = 0
basic.forever(function () {
    if (input.soundLevel() > 100 && lampeAn == 0) {
        lampeAn = 1
        basic.setLedColor(0xffff00)
        basic.showIcon(IconNames.Diamond)
        basic.pause(5000)
        basic.setLedColor(0x000000)
        basic.clearScreen()
        lampeAn = 0
    }
})
```

## Fertig! @showdialog

💡 **Fantastisch!** Dein Smartlicht funktioniert!

**Ideen zum Weiterdenken:**
- Kannst du die Leuchtdauer mit Taste **A** (+ 5 s) und Taste **B** (− 5 s) einstellen?
- Was wäre, wenn die Lampe **blinkt**, kurz bevor sie ausgeht?
- Wie könntest du die Lampe durch **zweimaliges** Klatschen einschalten (damit einmaliges Klatschen sie nicht auslöst)?

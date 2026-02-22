# 💪 Fitnessprogramm

## Einleitung @showdialog

Heute baust du ein **Fitnessprogramm** mit dem @boardname@!

Die drei RGB-LEDs leuchten in verschiedenen Farben. Jede Farbe steht für eine andere Fitnessübung.

Drücke Taste **A**, um die nächste zufällige Übung angezeigt zu bekommen. Viel Spaß!

## Schritt 1 – Was sind RGB-LEDs? @showdialog

Der Calliope mini 3 hat **3 eingebaute RGB-LEDs**.

RGB bedeutet: **R**ot, **G**rün, **B**lau. Durch Mischen dieser drei Farben kann man fast jede Farbe erzeugen.

Wir ordnen 5 Farben 5 Fitnessübungen zu:

| Farbe | Übung |
|---|---|
| 🔴 Rot | Kniebeugen |
| 🟢 Grün | Strecksprünge |
| 🔵 Blau | Hampelmann |
| 🟡 Gelb | Liegestütze |
| 🟣 Lila | Sit-ups |

## Schritt 2 – Eine Variable für die Übung

Erstelle eine Variable namens **übung**, die eine Zufallszahl zwischen **0 und 4** speichert.

Öffne ``||variables:Variablen||`` → „Erstelle eine Variable" → nenne sie `übung`.

Ziehe dann ``||variables:setze übung auf||`` in den ``||input:wenn Knopf A gedrückt||``-Block.
Als Wert: ``||math:wähle zufällig von 0 bis 4||``.

```blocks
let übung = 0
input.onButtonEvent(Button.A, input.buttonEventValue(ButtonEvent.Click), function () {
    übung = randint(0, 4)
})
```

## Schritt 3 – Farbe und Übung anzeigen

Jetzt kommt der wichtigste Teil: je nach Zufallszahl soll eine andere Farbe leuchten und der Name der Übung auf der LED-Matrix erscheinen.

Nutze ``||logic:wenn ... dann ... sonst||``-Blöcke (auch „wenn-sonst-wenn" genannt).

> 💡 **Tipp:** Du findest die RGB-Farben unter ``||basic:Grundlagen||`` → „setze alle RGB-LEDs auf".

```blocks
let übung = 0
input.onButtonEvent(Button.A, input.buttonEventValue(ButtonEvent.Click), function () {
    übung = randint(0, 4)
    if (übung == 0) {
        basic.setLedColor(0xff0000)
        basic.showString("Kniebeugen")
    } else if (übung == 1) {
        basic.setLedColor(0x00ff00)
        basic.showString("Strecksprung")
    } else if (übung == 2) {
        basic.setLedColor(0x0000ff)
        basic.showString("Hampelmann")
    } else if (übung == 3) {
        basic.setLedColor(0xffff00)
        basic.showString("Liegestuetze")
    } else {
        basic.setLedColor(0x7f00ff)
        basic.showString("Sit-ups")
    }
})
```

## Schritt 4 – Anzahl der Wiederholungen anzeigen

Nach dem Übungsnamen soll auch eine **Anzahl** erscheinen – zum Beispiel immer **10 Wiederholungen**.

Füge nach jedem ``||basic:zeige Text||``-Block einen ``||basic:zeige Zahl||``-Block mit dem Wert **10** ein.

```blocks
let übung = 0
input.onButtonEvent(Button.A, input.buttonEventValue(ButtonEvent.Click), function () {
    übung = randint(0, 4)
    if (übung == 0) {
        basic.setLedColor(0xff0000)
        basic.showString("Kniebeugen")
        basic.showNumber(10)
    } else if (übung == 1) {
        basic.setLedColor(0x00ff00)
        basic.showString("Strecksprung")
        basic.showNumber(10)
    } else if (übung == 2) {
        basic.setLedColor(0x0000ff)
        basic.showString("Hampelmann")
        basic.showNumber(10)
    } else if (übung == 3) {
        basic.setLedColor(0xffff00)
        basic.showString("Liegestuetze")
        basic.showNumber(10)
    } else {
        basic.setLedColor(0x7f00ff)
        basic.showString("Sit-ups")
        basic.showNumber(10)
    }
})
```

## Schritt 5 – LEDs am Ende ausschalten

Nach der Anzeige sollen die RGB-LEDs wieder ausgehen. Füge ganz am Ende deines A-Knopf-Blocks einen Block ein:

``||basic:setze alle RGB-LEDs auf||`` → wähle **Schwarz** (= ausgeschaltet).

```blocks
let übung = 0
input.onButtonEvent(Button.A, input.buttonEventValue(ButtonEvent.Click), function () {
    übung = randint(0, 4)
    if (übung == 0) {
        basic.setLedColor(0xff0000)
        basic.showString("Kniebeugen")
        basic.showNumber(10)
    } else if (übung == 1) {
        basic.setLedColor(0x00ff00)
        basic.showString("Strecksprung")
        basic.showNumber(10)
    } else if (übung == 2) {
        basic.setLedColor(0x0000ff)
        basic.showString("Hampelmann")
        basic.showNumber(10)
    } else if (übung == 3) {
        basic.setLedColor(0xffff00)
        basic.showString("Liegestuetze")
        basic.showNumber(10)
    } else {
        basic.setLedColor(0x7f00ff)
        basic.showString("Sit-ups")
        basic.showNumber(10)
    }
    basic.setLedColor(0x000000)
})
```

## Schritt 6 – Fertig! @showdialog

🏋️ **Klasse!** Dein Fitnessprogramm ist bereit!

Drücke im Simulator mehrmals auf Taste **A** und schau, welche Übungen du bekommst.

Lade das Programm auf deinen @boardname@ und mach Sport!

**Ideen zum Weiterdenken:**
- Kannst du einen **Countdown von 10 Sekunden** einbauen, damit du Zeit hast, die Übung zu machen?
- Was wäre, wenn du auch die **Anzahl der Wiederholungen zufällig** wählst (z. B. 5–15)?

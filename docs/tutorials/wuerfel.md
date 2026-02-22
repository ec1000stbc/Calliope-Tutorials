# 🎲 Würfel

## Einleitung @showdialog

Ein echter Würfel zeigt Zahlen von **1 bis 6** – bestimmt durch Zufall.

Heute programmierst du deinen eigenen digitalen Würfel! Schüttle den @boardname@, und er zeigt eine zufällige Zahl auf der LED-Matrix.

## Schritt 1 – Den Lagesensor kennenlernen @showdialog

Der @boardname@ hat einen eingebauten **Lagesensor** (Beschleunigungssensor).

Er erkennt verschiedene Bewegungen, zum Beispiel:
- **Schütteln** → `wenn geschüttelt`
- Neigen nach links / rechts / vorne / hinten
- Freier Fall

Für unseren Würfel nutzen wir **Schütteln** als Auslöser!

## Schritt 2 – Das Schüttel-Ereignis

Öffne ``||input:Eingabe||`` und suche nach ``||input:wenn geschüttelt||``.

Ziehe diesen Block auf die Arbeitsfläche. Alles, was du dort hineinlegst, passiert beim Schütteln.

```blocks
input.onGesture(Gesture.Shake, function () {
})
```

## Schritt 3 – Eine Zufallszahl erzeugen

Ein Würfel zeigt Zahlen von **1 bis 6**. Nutze ``||math:wähle zufällig von 1 bis 6||`` aus der Kategorie ``||math:Mathematik||``.

Speichere die Zahl in einer Variable namens **augenzahl**.

```blocks
let augenzahl = 0
input.onGesture(Gesture.Shake, function () {
    augenzahl = randint(1, 6)
})
```

## Schritt 4 – Die Zahl anzeigen

Zeige die Augenzahl auf der LED-Matrix!

```blocks
let augenzahl = 0
input.onGesture(Gesture.Shake, function () {
    augenzahl = randint(1, 6)
    basic.showNumber(augenzahl)
})
```

Teste es im Simulator – klicke auf „Schütteln" unter dem @boardname@-Bild.

## Schritt 5 – Mit Punkten anzeigen (Bonus)

Echter als Zahlen: Echte Würfelpunkte! Nutze ``||basic:zeige LEDs||`` für jede Augenzahl.

Füge eine ``||logic:wenn ... dann ... sonst||``-Kette ein:

```blocks
let augenzahl = 0
input.onGesture(Gesture.Shake, function () {
    augenzahl = randint(1, 6)
    if (augenzahl == 1) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . . # . .
            . . . . .
            . . . . .
            `)
    } else if (augenzahl == 2) {
        basic.showLeds(`
            # . . . .
            . . . . .
            . . . . .
            . . . . .
            . . . . #
            `)
    } else if (augenzahl == 3) {
        basic.showLeds(`
            # . . . .
            . . . . .
            . . # . .
            . . . . .
            . . . . #
            `)
    } else if (augenzahl == 4) {
        basic.showLeds(`
            # . . . #
            . . . . .
            . . . . .
            . . . . .
            # . . . #
            `)
    } else if (augenzahl == 5) {
        basic.showLeds(`
            # . . . #
            . . . . .
            . . # . .
            . . . . .
            # . . . #
            `)
    } else {
        basic.showLeds(`
            # . . . #
            . . . . .
            # . . . #
            . . . . .
            # . . . #
            `)
    }
})
```

## Schritt 6 – Animation beim Würfeln

Machen wir das Würfeln etwas spannender! Zeige **kurz ein Fragezeichen**, bevor das Ergebnis erscheint.

Füge am Anfang deines Schüttel-Blocks ein:
- ``||basic:zeige Symbol||`` → Fragezeichen (oder ein eigenes Bild)
- ``||basic:pausiere||`` → 500 ms

```blocks
let augenzahl = 0
input.onGesture(Gesture.Shake, function () {
    basic.showIcon(IconNames.No)
    basic.pause(500)
    augenzahl = randint(1, 6)
    if (augenzahl == 1) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . . # . .
            . . . . .
            . . . . .
            `)
    } else if (augenzahl == 2) {
        basic.showLeds(`
            # . . . .
            . . . . .
            . . . . .
            . . . . .
            . . . . #
            `)
    } else if (augenzahl == 3) {
        basic.showLeds(`
            # . . . .
            . . . . .
            . . # . .
            . . . . .
            . . . . #
            `)
    } else if (augenzahl == 4) {
        basic.showLeds(`
            # . . . #
            . . . . .
            . . . . .
            . . . . .
            # . . . #
            `)
    } else if (augenzahl == 5) {
        basic.showLeds(`
            # . . . #
            . . . . .
            . . # . .
            . . . . .
            # . . . #
            `)
    } else {
        basic.showLeds(`
            # . . . #
            . . . . .
            # . . . #
            . . . . .
            # . . . #
            `)
    }
})
```

## Fertig! @showdialog

🎲 **Sehr gut!** Dein digitaler Würfel ist fertig!

Lade das Programm auf deinen @boardname@ und würfele los!

**Ideen zum Weiterdenken:**
- Kannst du einen **Zwei-Würfel-Modus** mit Taste **B** einbauen (zwei Zufallszahlen addieren, max. 12)?
- Was wäre, wenn die RGB-LED bei einer 6 **grün** aufleuchtet und bei einer 1 **rot**?
- Wie würdest du einen **20-seitigen Würfel** (für Rollenspiele) programmieren?

# 🚀 Raketenstart

## Einleitung @showdialog

Heute programmierst du einen **Raketenstart mit Countdown**!

Der @boardname@ zählt von 5 auf 0 herunter und zeigt dann eine Rakete auf der LED-Matrix.

Los geht's!

## Schritt 1 – Den Startknopf vorbereiten

Wenn du Taste **A** drückst, soll der Countdown beginnen.

Öffne die Kategorie ``||input:Eingabe||`` und ziehe den Block
``||input:wenn Knopf A gedrückt||`` auf die Arbeitsfläche.

```blocks
input.onButtonEvent(Button.A, input.buttonEventValue(ButtonEvent.Click), function () {
})
```

## Schritt 2 – Von 5 auf 1 zählen

Jetzt lassen wir den @boardname@ von **5 bis 1** zählen.

Füge eine ``||loops:für Index von 0 bis 4||``-Schleife ein – aber wir wollen **rückwärts** zählen.
Nutze stattdessen einzelne ``||basic:zeige Zahl||``-Blöcke mit einer ``||basic:pausiere||``-Pause dazwischen.

> 💡 **Tipp:** Eine Pause von **1000 Millisekunden** = 1 Sekunde.

```blocks
input.onButtonEvent(Button.A, input.buttonEventValue(ButtonEvent.Click), function () {
    basic.showNumber(5)
    basic.pause(1000)
    basic.showNumber(4)
    basic.pause(1000)
    basic.showNumber(3)
    basic.pause(1000)
    basic.showNumber(2)
    basic.pause(1000)
    basic.showNumber(1)
    basic.pause(1000)
})
```

## Schritt 3 – Der Abschuss: Zahl 0 und Bild

Nach dem Countdown kommt die große **0** – und dann startet die Rakete!

Zeige nach der 1 noch die **0** an, warte kurz, und zeige danach ein Bild.
Nutze ``||basic:zeige LEDs||`` und zeichne selbst eine Rakete – oder verwende ``||basic:zeige Symbol||``.

```blocks
input.onButtonEvent(Button.A, input.buttonEventValue(ButtonEvent.Click), function () {
    basic.showNumber(5)
    basic.pause(1000)
    basic.showNumber(4)
    basic.pause(1000)
    basic.showNumber(3)
    basic.pause(1000)
    basic.showNumber(2)
    basic.pause(1000)
    basic.showNumber(1)
    basic.pause(1000)
    basic.showNumber(0)
    basic.pause(500)
    basic.showLeds(`
        . . # . .
        . # # # .
        . . # . .
        . # . # .
        # . . . #
        `)
})
```

## Schritt 4 – Sound dazu!

Ein Raketenstart braucht Geräusche! Füge vor der 0 einen Ton ein.

Öffne ``||music:Musik||`` und ziehe ``||music:spiele Note||`` oder ``||music:spiele Melodie||`` ein.

```blocks
input.onButtonEvent(Button.A, input.buttonEventValue(ButtonEvent.Click), function () {
    basic.showNumber(5)
    basic.pause(1000)
    basic.showNumber(4)
    basic.pause(1000)
    basic.showNumber(3)
    basic.pause(1000)
    basic.showNumber(2)
    basic.pause(1000)
    basic.showNumber(1)
    basic.pause(1000)
    basic.showNumber(0)
    music.play(music.builtinPlayableSoundEffect(soundExpression.mysterious), music.PlaybackMode.UntilDone)
    basic.pause(500)
    basic.showLeds(`
        . . # . .
        . # # # .
        . . # . .
        . # . # .
        # . . . #
        `)
})
```

## Schritt 5 – Testen und herunterladen @showdialog

🎉 **Super!** Dein Raketenstart-Programm ist fertig!

Teste es im Simulator auf der linken Seite – klicke auf Taste **A**.

Wenn alles klappt, lade das Programm mit ``|Herunterladen|`` auf deinen @boardname@.

**Ideen zum Weiterdenken:**
- Kannst du die Rakete am Ende animieren, sodass sie „hochfliegt"?
- Was passiert, wenn du Taste **B** drückst – kannst du dort einen Reset einbauen?

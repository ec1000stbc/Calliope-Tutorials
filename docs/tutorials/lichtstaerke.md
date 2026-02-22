# 💡 Lichtstärke messen

## Einleitung @showdialog

Der @boardname@ kann mit seinen LEDs auch **Licht messen** – die LEDs funktionieren dabei wie kleine Sensoren.

Aber Achtung: Wenn die LED-Matrix leuchtet, misst sie ihr eigenes Licht – das verfälscht das Ergebnis!

Heute lernst du, wie du den **Lichtwert bei ausgeschalteter Matrix** misst und ihn dann anzeigst.

## Schritt 1 – Den Lichtsensor kennenlernen

Der @boardname@ misst die Helligkeit als Zahl von **0** (dunkel) bis **255** (sehr hell).

Du findest den Lichtsensor-Block unter ``||input:Eingabe||`` → „Lichtstärke".

Teste ihn zunächst einfach: Baue ein kleines Programm, das die Lichtstärke **dauerhaft** anzeigt.

```blocks
basic.forever(function () {
    basic.showNumber(input.lightLevel())
})
```

Halte deine Hand über den @boardname@ – ändert sich der Wert?

## Schritt 2 – Das Problem erkennen @showdialog

Hast du bemerkt, dass der Wert **nicht sehr genau** ist?

Das liegt daran: Die LED-Matrix **leuchtet selbst** und beeinflusst die Messung.

Die Lösung: Wir **schalten die Matrix kurz aus**, messen dann den Lichtwert, und **speichern** ihn in einer Variable. Danach schalten wir die Matrix wieder ein und zeigen den gespeicherten Wert an.

## Schritt 3 – Eine Variable erstellen

Erstelle eine Variable namens **lichtwert**.

Öffne ``||variables:Variablen||`` → „Erstelle eine Variable" → nenne sie `lichtwert`.

## Schritt 4 – Messung mit Knopfdruck starten

Wenn wir Taste **A** drücken, soll die Messung starten.

Ziehe ``||input:wenn Knopf A gedrückt||`` auf die Arbeitsfläche.

```blocks
let lichtwert = 0
input.onButtonEvent(Button.A, input.buttonEventValue(ButtonEvent.Click), function () {
})
```

## Schritt 5 – LED-Matrix ausschalten und messen

Jetzt kommt der Trick! In drei Schritten:

1. LED-Matrix **ausschalten** mit ``||led:Bildschirm löschen||``
2. Kurz **warten** (100 ms reichen), damit der Sensor sich anpassen kann
3. Lichtstärke in die Variable **speichern**

```blocks
let lichtwert = 0
input.onButtonEvent(Button.A, input.buttonEventValue(ButtonEvent.Click), function () {
    led.stopAnimation()
    basic.clearScreen()
    basic.pause(100)
    lichtwert = input.lightLevel()
})
```

## Schritt 6 – Wert anzeigen

Nach der Messung zeigen wir den gespeicherten Wert auf der LED-Matrix an.
Da die Matrix jetzt wieder angeht, haben wir den Messwert schon sicher in der Variable.

```blocks
let lichtwert = 0
input.onButtonEvent(Button.A, input.buttonEventValue(ButtonEvent.Click), function () {
    led.stopAnimation()
    basic.clearScreen()
    basic.pause(100)
    lichtwert = input.lightLevel()
    basic.showNumber(lichtwert)
})
```

## Schritt 7 – Ausprobieren und vergleichen @showdialog

🔬 **Jetzt experimentieren!**

1. Drücke **A** bei normalem Licht → merke dir den Wert
2. Decke den @boardname@ mit der Hand ab → drücke **A** → ist der Wert kleiner?
3. Halte ihn unter eine Lampe → drücke **A** → ist der Wert größer?

**Vergleich mit dem alten Programm:**
Baue zum Vergleich auf Taste **B** das einfache Programm von Schritt 1 ein und vergleiche die Werte!

```blocks
let lichtwert = 0
input.onButtonEvent(Button.A, input.buttonEventValue(ButtonEvent.Click), function () {
    led.stopAnimation()
    basic.clearScreen()
    basic.pause(100)
    lichtwert = input.lightLevel()
    basic.showNumber(lichtwert)
})
input.onButtonEvent(Button.B, input.buttonEventValue(ButtonEvent.Click), function () {
    basic.showNumber(input.lightLevel())
})
```

Lade das Programm auf deinen @boardname@ und teste es an verschiedenen Orten!

**Ideen zum Weiterdenken:**
- Kannst du eine Lampe programmieren, die sich **automatisch** einschaltet, wenn es zu dunkel wird?
- Wie könnte man den Wert auf einer Skala von 0–5 Sternen anzeigen?

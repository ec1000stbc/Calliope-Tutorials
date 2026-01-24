# Zufalls-Blinker

## Schritt 1
Füge zunächst den LED-Umschalt-Block für x- und y-Koordinate ein.

```blocks
led.toggle(0, 0)
```

## Schritt 2
Trage für x den Block für Zufallszahlen zwischen 0 und 4 ein.

```blocks
let x = randint(0, 4)
led.toggle(x, 0)
```

## Schritt 3
Trage nun auch für y diesen Block ein.

```blocks
let y = randint(0, 4)
led.toggle(x, y)
```

## Schritt 4
Ergänze noch eine Pause von 200ms.

```blocks
basic.pause(200)
```
### Schritt 5
Damit der Blinker kontinuierlich läuft, packe alles in eine ``forever-Schleife``:

```blocks
basic.forever(function () {
    let x = randint(0, 4)
    let y = randint(0, 4)
    led.toggle(x, y)
    basic.pause(200)
})
```
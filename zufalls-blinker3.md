# Zufalls-Blinker

## Schritt 1
Füge zunächst den LED-Umschalt-Block für x- und y-Koordinate ein.


```blocks
basic.forever(function () {
    led.toggle(0, 0)
})
```

## Schritt 2
Trage für x den Block für Zufallszahlen zwischen 0 und 4 ein.

```blocks
basic.forever(function () {
    led.toggle(randint(0, 4), 0)
})
```


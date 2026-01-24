# Zufalls-Blinker

## Schritt 1
Füge zunächst den LED-Umschalt-Block für x- und y-Koordinate ein.


```blocks
basic.forever(function () {
    led.toggle(0, 0)
})
```

## Schritt 2
Trage für x den ``||randint(0, 10)||``-Block und trage 0 und 4 ein.

# Zufalls-Blinker

## Schritt 1
Füge zunächst den LED-Umschalt-Block für x- und y-Koordinate ein.


## Schritt 2
Verwende für x den Zufallszahlen-Block und trage 0 und 4 ein.
```blocks
basic.forever(function () {
    led.toggle(randint(0, 4), 0)
})
```

## Schritt 3
Ebenso für y!

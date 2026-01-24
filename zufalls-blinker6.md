# Zufalls-Blinker

## Füge zunächst den LED-Umschalt-Block für x- und y-Koordinate ein.

```blocks
basic.forever(function () {
    led.toggle(0, 0)
})
```

## Trage für x den Block für Zufallszahlen zwischen 0 und 4 ein.

```blocks
basic.forever(function () {
    led.toggle(randint(0, 4), 0)
})
```

## Trage nun auch für y diesen Block ein.

```blocks
basic.forever(function () {
    led.toggle(randint(0, 4), randint(0, 4))
})
```

## Ergänze noch eine Pause von 200ms.

```blocks
basic.forever(function () {
    led.toggle(randint(0, 4), randint(0, 4))
    basic.pause(200)
})
```

# Día 5 - Contando los días para los regalos

> ¡Qué ganas de abrir los regalos 🎁! Estoy tan nervioso que no paro de contar los días que faltan 🤣. ¿Me ayudas creando un programita? ¡Venga!

<br />
<img src="https://img.shields.io/badge/Dificultad-Fácil-brightgreen?style=for-the-badge&labelColor=black">

## Enunciado

Con la emoción, ya estamos empezando a **contar los días del calendario hasta el 25 de diciembre 📆.**

Para ayudar a esto, vamos a crear una función que pasándole una instancia de `Date` nos diga el número de días que faltan.

Veamos unos ejemplos:

```swift
daysToXmas(date: Calendar.current.date(from: DateComponents(year: 2021, month: 12, day: 1))!) // 24
daysToXmas(date: Calendar.current.date(from: DateComponents(year: 2021, month: 12, day: 24, hour: 0, minute: 0, second: 1))!) // 1
daysToXmas(date: Calendar.current.date(from: DateComponents(year: 2021, month: 12, day: 24, hour: 23, minute: 59, second: 59))!) // 1
daysToXmas(date: Calendar.current.date(from: DateComponents(year: 2021, month: 12, day: 20, hour: 3, minute: 24))!) // 5
```

El resultado tiene que ser **un número entero** y, como ves, aunque falte un segundo hasta el siguiente día, se entiende que todavía falta un día.

**¡Pero ojo!** También hay que indicar si la fecha es del mismo día (devolveríamos `0`) o si es una fecha futura (devolveríamos el número de días en negativo `-`):

```swift
daysToXmas(date: Calendar.current.date(from: DateComponents(year: 2021, month: 12, day: 25))!) // 0
daysToXmas(date: Calendar.current.date(from: DateComponents(year: 2021, month: 12, day: 26))!) // -1
daysToXmas(date: Calendar.current.date(from: DateComponents(year: 2021, month: 12, day: 31))!) // -6
daysToXmas(date: Calendar.current.date(from: DateComponents(year: 2022, month: 1, day: 1, hour: 0, minute: 0, second: 1))!) // -7
daysToXmas(date: Calendar.current.date(from: DateComponents(year: 2022, month: 1, day: 1, hour: 23, minute: 59, second: 59))!) // -7
```

## Solución

```swift
let XMAS_DATE = Calendar.current.date(from: DateComponents(year: 2021, month: 12, day: 25))!
let SEC_IN_A_DAY: Double = 3600 * 24;

func daysToXmas(date: Date) -> Int {
    return Int(ceil(date.distance(to: XMAS_DATE) / SEC_IN_A_DAY))
}
```

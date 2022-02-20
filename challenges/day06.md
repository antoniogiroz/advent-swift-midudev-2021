# Día 6 - Rematando los exámenes finales

> Buffff! Ya huelo las vacaciones pero todavía falta terminar los exámenes finales. ¡Y toca un poco de matemáticas! 😱 ¡Ayúdame!

Dificultad: Normal

## Enunciado

Antes de poder disfrutar de la navidad... nos toca terminar de rematar los exámenes finales. ¡Y toca un poco de matemáticas! 😱

A una función se le pasan dos parámetros: un Array con números y el resultado que se espera.

La función debe devolver los dos valores del Array que sumen el resultado esperado. Como a veces **pueden haber más de dos valores** que sumen, se devolverá el primero empezando por la izquierda que encuentre otro par, **sin importar lo lejos que esté a la derecha.**

Si no se encuentra, se devuelve `nil`.

Veamos unos ejemplos:

```swift
print(sumPairs(numbers: [3, 5, 7, 2], result: 10)) // [3, 7]
print(sumPairs(numbers: [-3, -2, 7, -5], result: 10)) // nil
print(sumPairs(numbers: [2, 2, 3, 1], result: 4)) // [2, 2]
print(sumPairs(numbers: [6, 7, 1, 2], result: 8)) // [6, 2]
print(sumPairs(numbers: [0, 2, 2, 3, -1, 1, 5], result: 6)) // [1, 5]
```

El resultado tiene que ser **un array con dos números.**

Una vez que tengas el resultado... ¿cómo podrías hacer que fuese lo más óptimo posible para **no tener que recorrer las mismas situaciones dos veces** 🤔?



## Solución

```swift
func sumPairs(numbers: [Int], result: Int) -> [Int]? {
    for (i, num1) in numbers.enumerated() {
        for num2 in numbers.dropFirst(i + 1) {
            if num1 + num2 == result {
                return [num1, num2];
            }
        }
    }
    return nil;
}
```

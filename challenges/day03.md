# Día 3 - El Grinch quiere fastidiar la Navidad

> ¡El Grinch anda suelto y quiere fastidiar la Navidad! 😱 Vamos a arreglar el lío que ha montado en la fábrica de regalos de Santa Claus

Dificultad: Normal

## Enunciado

El Grinch está abriendo las cartas que iban a Santa Claus y las está dejando hechas un lío. 😱

Las cartas son una cadena de texto que incluyen regalos y paréntesis `()`.

Para saber si una carta es válida ✅, debes comprobar que los paréntesis cierran correctamente y que, además, no vayan vacíos.

**¡Pero ojo!** Porque el Grinch ha dejado llaves `{` y corchetes `[` dentro de los paréntesis que **hacen que no sean válidas**. Por suerte sólo los ha dejado en medio de los paréntesis...

Ejemplos:

```swift
print(isValid("bici coche (balón) bici coche peluche")) // true
print(isValid("(muñeca) consola bici")) // true

print(isValid("bici coche (balón bici coche")) // false
print(isValid("peluche (bici [coche) bici coche balón")) // false
print(isValid("(peluche {) bici")) // false
print(isValid("() bici")) // false
```
      
Crea una función que pasándole el texto de la carta, devuelva `true` si es válida y `false` si no lo es. ¡Y acaba con la travesura del Grinch!

## Solución

```swift
func isValid(_ letter: String) -> Bool {
    letter.range(
        of: "^[^\\{\\[\\(\\)]*\\([^\\{\\[\\(\\)]+\\)+.*",
        options: .regularExpression
    ) != nil
}
```

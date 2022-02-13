# Día 1 - Contando ovejas para dormir 

> Con la emoción de que llega la navidad, nos está costando dormir bastante últimamente. Vamos a intentar usar este pequeño truco que nos ayudará a dormir más rápido 🐑.

Dificultad: Fácil

## Enunciado

Considera una lista/array de ovejas. Cada oveja tiene un nombre y un color. Haz una función que devuelva una lista con todas las ovejas que sean de color `rojo` **y que además** su nombre contenga tanto las letras `n` Y `a`, sin importar el orden, las mayúsculas o espacios.

Por ejemplo, si tenemos las ovejas:

```swift
let ovejas = [
    Oveja(name: "Noa", color: .azul),
    Oveja(name: "Euge", color: .rojo),
    Oveja(name: "Navidad", color: .rojo),
    Oveja(name: "Ki Na Ma", color: .rojo),
    Oveja(name: "AAAAAaaaaa", color: .rojo),
    Oveja(name: "Nnnnnnnn", color: .rojo),
]
```

Al ejecutar el método debería devolver lo siguiente:

```swift
let ovejasFiltradas = contarOvejas(ovejas)

print(ovejasFiltradas.map{ $0.name })

// ["Navidad", "Ki Na Ma"]
```

Recuerda. **Debe contener las dos letras 'a' y 'n' en el nombre**. No cuentes ovejas que sólo tenga una de las letras, debe tener ambas.

## Solución

```swift
enum Color {
    case rojo, azul, verde, amarillo
}

struct Oveja {
    var name: String
    var color: Color
}

func contarOvejas(_ ovejas: [Oveja]) -> [Oveja] {
    let pattern = #"^(?=.*a)(?=.*n).*$"#
    return ovejas.filter {
        $0.color == .rojo &&
        $0.name.range(
            of: pattern,
            options: [.regularExpression, .caseInsensitive]
        ) != nil
    }
}
```
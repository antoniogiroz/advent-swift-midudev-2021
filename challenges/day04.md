# Día 4 - ¡Es hora de poner la navidad en casa!

> Creo que ya podemos sacar el gorro navideño, el turrón... ¡Y el árbol de navidad! 🎄 Vamos a montarlo con JavaScript.

<br />
<img src="https://img.shields.io/badge/Dificultad-Normal-yellow?style=for-the-badge&labelColor=black">

## Enunciado

¡Es hora de poner el árbol de navidad en casa! 🎄

Para ello vamos a crear una función que recibe la altura del árbol, que será un entero positivo del 1 a, como máximo, 100.

Si le pasamos el argumento `5`, se pintaría esto:

```swift
print(createXmasTree(height: 5))

/*
____*____
___***___
__*****__
_*******_
*********
____#____
____#____
*/
```

Creamos un triángulo de asteriscos `*` con la altura proporcionada y, a los lados, usamos el guión bajo `_` para los espacios. Es muy importante que nuestro árbol siempre tenga la misma longitud por cada lado.
Todos los árboles, por pequeños o grandes que sean, tienen un tronco de dos líneas de `#`.

Otro ejemplo con un árbol de altura `3`:

```swift
print(createXmasTree(height: 3))

/*
__*__
_***_
*****
__#__
__#__
*/
```

Ten en cuenta que el árbol es un string y necesitas los saltos de línea `\n` para cada línea para que se forme bien el árbol.

## Solución

```swift
enum Symbol: String {
    case leaf = "*"
    case gap = "_"
    case trunk = "#"
}

func createXmasTree(height: Int) -> String {
    var tree = [String]();
    var width = 1;
    var emptyChars = height - 1;
    var gap = String(repeating: Symbol.gap.rawValue, count: emptyChars);
    let trunk = gap + Symbol.trunk.rawValue + gap;
    
    for _ in 1...height {
        let leafs = String(repeating: Symbol.leaf.rawValue, count: width);
        gap = String(repeating: Symbol.gap.rawValue, count: emptyChars);
        tree.append(gap + leafs + gap);
        width += 2;
        emptyChars -= 1;
    }
    
    tree.append(trunk);
    tree.append(trunk);
    
    return tree.joined(separator: "\n");
}
```

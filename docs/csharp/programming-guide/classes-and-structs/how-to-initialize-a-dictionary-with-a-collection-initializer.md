---
title: 'Inicialización de un diccionario con un inicializador de colección: Guía de programación de C#'
ms.custom: seodec18
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: 22f80365b974df66999ac68f7bc2a9ffa7d445a5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596809"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>Procedimientos: inicialización de un diccionario con un inicializador de colección (guía de programación de C#)

Una clase <xref:System.Collections.Generic.Dictionary%602> contiene una colección de pares clave-valor. Su método <xref:System.Collections.Generic.Dictionary%602.Add*> toma dos parámetros: uno para la clave y otro para el valor. Una manera de inicializar <xref:System.Collections.Generic.Dictionary%602>, o cualquier colección cuyo método `Add` tome varios parámetros, es incluir entre llaves cada conjunto de parámetros, como se muestra en el ejemplo siguiente. Otra opción es usar un inicializador de índice, lo que también se muestra en el ejemplo siguiente.

## <a name="example"></a>Ejemplo

En el ejemplo de código siguiente, <xref:System.Collections.Generic.Dictionary%602> se inicializa con instancias de tipo `StudentName`.  La primera inicialización usa el método `Add` con dos argumentos. El compilador genera una llamada a `Add` por cada uno de los pares de claves `int` y valores `StudentName`. La segunda usa un método de indizador de lectura y escritura público de la clase `Dictionary`:

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

Observe los dos pares de llaves de cada elemento de la colección en la primera declaración. Las llaves internas contienen el inicializador de objeto para `StudentName`, mientras que las externas contienen el inicializador para el par clave-valor que se va a agregar a la clase <xref:System.Collections.Generic.Dictionary%602> `students`. Por último, el inicializador completo de la colección para el diccionario se encierra entre llaves. En la segunda inicialización, el lado izquierdo de la asignación es la clave y el lado derecho es el valor, con un inicializador de objeto para `StudentName`.

## <a name="see-also"></a>Vea también

- [Guía de programación de C#](../index.md)
- [Inicializadores de objeto y colección](./object-and-collection-initializers.md)

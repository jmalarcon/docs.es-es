---
title: 'Bucles: expresión for...to'
description: Vea cómo F# ... la expresión to se usa para iterar en un bucle en un intervalo de valores de una variable de bucle.
ms.date: 05/16/2016
ms.openlocfilehash: 910c04aa4ea6b2c637dcad147347c1c317b5e0c0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626627"
---
# <a name="loops-forto-expression"></a>Bucles: expresión for...to

La `for...to` expresión se usa para iterar en un bucle en un intervalo de valores de una variable de bucle.

## <a name="syntax"></a>Sintaxis

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a>Comentarios

El tipo del identificador se deduce del tipo de las expresiones de *Inicio* y *finalización* . Los tipos de estas expresiones deben ser enteros de 32 bits.

A pesar de ser técnicamente `for...to` una expresión, es más similar a una instrucción tradicional en un lenguaje de programación imperativo. El tipo de valor devuelto para la *expresión de cuerpo* debe ser `unit`. En los ejemplos siguientes se muestran varios usos `for...to` de la expresión.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

La salida del código anterior es la siguiente.

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a>Vea también

- [Referencia del lenguaje F#](index.md)
- [Bucles `for...in`Expresiones](loops-for-in-expression.md)
- [Bucles `while...do`Expresiones](loops-while-do-expression.md)

---
title: 'Checked y Unchecked: Referencia de C#'
ms.custom: seodec18
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: 7abc19e0657330752e7798d060516c48aa402297
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771777"
---
# <a name="checked-and-unchecked-c-reference"></a>Checked y Unchecked (Referencia de C#)
Las instrucciones de C# se pueden ejecutar en un contexto comprobado o no comprobado. En un contexto no comprobado, el desbordamiento aritmético produce una excepción. En un contexto sin comprobar, se omite el desbordamiento aritmético y se produce un truncamiento del resultado al descartar los bits de orden superior que no caben en el tipo de destino.  
  
- [checked](checked.md) Especifica un contexto comprobado.  
  
- [unchecked](unchecked.md) Especifica un contexto no comprobado.  
  
 Las siguientes operaciones se ven afectadas por la comprobación del desbordamiento:  
  
- Expresiones que usan los siguientes operadores predefinidos en tipos integrales:  
  
     `++`, `--`, `-` unario, `+`, `-`, `*`, `/`  
  
- Conversiones numéricas explícitas entre tipos integrales o de `float` o `double` a un tipo integral.  
  
 Si no se especifica `checked` ni `unchecked`, el contexto predeterminado para expresiones no constantes (expresiones que se evalúan en tiempo de ejecución) se define por medio del valor de la opción del compilador [/checked](../compiler-options/checked-compiler-option.md). De forma predeterminada, el valor de esa opción se desactiva y se ejecutan operaciones aritméticas en un contexto sin comprobar.
 
 Para expresiones constantes (expresiones que se pueden evaluar completamente en tiempo de compilación), el contexto predeterminado se comprueba siempre. A menos que se coloque de forma explícita una expresión constante en un contexto sin comprobar, los desbordamientos que se producen durante la evaluación de tiempo de compilación de la expresión dan lugar a errores en tiempo de compilación.
  
## <a name="see-also"></a>Vea también

- [Referencia de C#](../index.md)
- [Guía de programación de C#](../../programming-guide/index.md)
- [Palabras clave de C#](index.md)
- [Palabras clave de instrucciones](statement-keywords.md)

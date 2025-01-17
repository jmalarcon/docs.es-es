---
title: 'Genéricos y atributos: Guía de programación de C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 99a24a7069145dfad5ce6c9c91f2a8653eb9a224
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589643"
---
# <a name="generics-and-attributes-c-programming-guide"></a>Genéricos y atributos (Guía de programación de C#)
Los atributos pueden aplicarse a los tipos genéricos de la misma manera que los tipos no genéricos. Para obtener más información sobre la aplicación de los atributos, vea [Atributos](../concepts/attributes/index.md).  
  
 Los atributos personalizados solo se permiten para hacer referencia a tipos genéricos abiertos, que son tipos genéricos para los que no se proporciona ningún argumento de tipo, y tipos genéricos construidos cerrados, que proporcionan argumentos para todos los parámetros de tipo.  
  
 En los ejemplos siguientes se usa este atributo personalizado:  
  
 [!code-csharp[csProgGuideGenerics#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#48)]  
  
 Un atributo puede hacer referencia a un tipo genérico abierto:  
  
 [!code-csharp[csProgGuideGenerics#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#49)]  
  
 Especifica varios parámetros de tipo con el número de comas apropiado. En este ejemplo, `GenericClass2` tiene dos parámetros de tipo:  
  
 [!code-csharp[csProgGuideGenerics#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#50)]  
  
 Un atributo puede hacer referencia a un tipo genérico construido cerrado:  
  
 [!code-csharp[csProgGuideGenerics#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#51)]  
  
 Un atributo que hace referencia a un parámetro de tipo genérico provocará un error en tiempo de compilación:  
  
 [!code-csharp[csProgGuideGenerics#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#52)]  
  
 Un tipo genérico no puede heredarse de <xref:System.Attribute>:  
  
 [!code-csharp[csProgGuideGenerics#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#53)]  
  
 Para obtener información sobre un tipo genérico o un parámetro de tipo en tiempo de ejecución, puede usar los métodos de <xref:System.Reflection>. Para obtener más información, vea [Genéricos y reflexión](./generics-and-reflection.md).  
  
## <a name="see-also"></a>Vea también

- [Guía de programación de C#](../index.md)
- [Genéricos](./index.md)
- [Atributos](../../../standard/attributes/index.md)

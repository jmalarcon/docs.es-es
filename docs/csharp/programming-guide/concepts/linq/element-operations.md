---
title: Operaciones de elementos (C#)
ms.date: 10/03/2018
ms.assetid: 283206c9-3246-4c48-b01a-d9de409a7231
ms.openlocfilehash: b32066d13e700d95e4d2eef29e24e8b87690037d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594578"
---
# <a name="element-operations-c"></a>Operaciones de elementos (C#)

Las operaciones de elementos devuelven un único elemento específico de una secuencia.  
  
 Los métodos del operador de consulta estándar que realizan operaciones de elementos se indican en la sección siguiente.  
  
## <a name="methods"></a>Métodos  
  
|Nombre del método|DESCRIPCIÓN|Sintaxis de la expresión de consulta de C#|Más información|  
|-----------------|-----------------|---------------------------------|----------------------|  
|ElementAt|Devuelve el elemento situado en un índice especificado de la colección.|No es aplicable.|<xref:System.Linq.Enumerable.ElementAt%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAt%2A?displayProperty=nameWithType>|  
|ElementAtOrDefault|Devuelve el elemento situado en un índice especificado de una colección o un valor predeterminado si el índice está fuera del intervalo.|No es aplicable.|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=nameWithType>|  
|First|Devuelve el primer elemento de una colección, o el primer elemento que cumple una condición.|No es aplicable.|<xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.First%2A?displayProperty=nameWithType>|  
|FirstOrDefault|Devuelve el primer elemento de una colección, o el primer elemento que cumple una condición. Devuelve un valor predeterminado si dicho elemento no existe.|No es aplicable.|<xref:System.Linq.Enumerable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%60%601%28System.Linq.IQueryable%7B%60%600%7D%29?displayProperty=nameWithType>|  
|Último|Devuelve el último elemento de una colección, o el último elemento que cumple una condición.|No es aplicable.|<xref:System.Linq.Enumerable.Last%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Last%2A?displayProperty=nameWithType>|  
|LastOrDefault|Devuelve el último elemento de una colección, o el último elemento que cumple una condición. Devuelve un valor predeterminado si dicho elemento no existe.|No es aplicable.|<xref:System.Linq.Enumerable.LastOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=nameWithType>|  
|Single|Devuelve el único elemento de una colección, o el único elemento que cumple una condición. Se produce un <xref:System.InvalidOperationException> si no hay ningún elemento o hay más de un elemento para devolver. |No es aplicable.|<xref:System.Linq.Enumerable.Single%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Single%2A?displayProperty=nameWithType>|  
|SingleOrDefault|Devuelve el único elemento de una colección, o el único elemento que cumple una condición. Devuelve un valor predeterminado si no hay ningún elemento para devolver. Se produce un <xref:System.InvalidOperationException> si hay más de un elemento para devolver. |No es aplicable.|<xref:System.Linq.Enumerable.SingleOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Vea también

- <xref:System.Linq>
- [Standard Query Operators Overview (C#)](./standard-query-operators-overview.md) (Información general sobre operadores de consulta estándar (C#))
- [Cómo: Buscar el archivo o archivos de mayor tamaño en un árbol de directorios (LINQ) (C#)](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)

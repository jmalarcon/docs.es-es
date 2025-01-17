---
title: '#ExternalSource (Directiva) (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- '#Externalsource'
- '#ExternalSource'
- vb.ExternalSource
- Externalsource
- vb.#ExternalSource
- ExternalSource
helpviewer_keywords:
- ExternalSource directive (#ExternalSource)
- '#ExternalSource directive'
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
ms.openlocfilehash: ac7096e998dd8d2a416dc739e1d7625e1abff7a6
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696824"
---
# <a name="externalsource-directive"></a>#ExternalSource (Directiva)
Indica una asignación entre líneas específicas de código fuente y texto externo al origen.  
  
## <a name="syntax"></a>Sintaxis  
  
```vb  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a>Elementos  
 `StringLiteral`  
 Ruta de acceso al origen externo.  
  
 `IntLiteral`  
 Número de línea de la primera línea del origen externo.  
  
 `LogicalLine`  
 La línea donde se produce el error en el origen externo.  
  
 `#End ExternalSource`  
 Finaliza el bloque `#ExternalSource`.  
  
## <a name="remarks"></a>Comentarios  
 Esta directiva solo la usan el compilador y el depurador.  
  
 Un archivo de código fuente puede incluir directivas de origen externo, que indican una asignación entre líneas específicas de código en el archivo de código fuente y texto externo al origen, como un archivo. aspx. Si se encuentran errores en el código fuente designado durante la compilación, se identifican como procedentes del origen externo.  
  
 Las directivas de origen externo no tienen ningún efecto en la compilación y no se pueden anidar. Están pensadas para uso interno de la aplicación únicamente.  
  
## <a name="see-also"></a>Vea también

- [Compilación condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)

---
title: -langversion (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: 5f59f1c4c269a52131a324bbd2bfbe817ab794a4
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197090"
---
# <a name="-langversion-visual-basic"></a>-langversion (Visual Basic)
Hace que el compilador acepte solo la sintaxis que se incluye en la versión de idioma de Visual Basic especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```console  
-langversion:version  
```  
  
## <a name="arguments"></a>Argumentos  
 `version`  
 Requerido. Versión de idioma que se va a usar durante la compilación. Los valores aceptados son `9`, `10`, `11`, `12`, `14`, `15`, `15.3`, `15.5`, `default` y `latest`.

 También se puede especificar cualquiera de los números enteros mediante `.0` como la versión secundaria, por ejemplo, `11.0`.

 Puede ver la lista de todos los valores posibles si especifica `-langversion:?` en la línea de comandos.  
  
## <a name="remarks"></a>Comentarios  
 La opción `-langversion` especifica qué sintaxis acepta el compilador. Por ejemplo, si especifica que la versión de lenguaje es 9,0, el compilador genera errores para la sintaxis que solo es válida en la versión 10,0 y posteriores.  
  
 Puede usar esta opción cuando desarrolle aplicaciones destinadas a versiones diferentes del .NET Framework. Por ejemplo, si tiene como destino .NET Framework 3,5, puede usar esta opción para asegurarse de que no usa la sintaxis de la versión 10,0 del lenguaje.  
  
 Solo puede establecer `-langversion` directamente mediante la línea de comandos. Para obtener más información, consulte [Elegir una versión específica de .NET Framework](/visualstudio/ide/visual-studio-multi-targeting-overview).  
  
## <a name="example"></a>Ejemplo  
 El código siguiente compila `sample.vb` para Visual Basic 9,0.  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a>Vea también

- [Compilador de línea de comandos de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Líneas de comandos de compilación de ejemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Elegir una versión específica de .NET Framework](/visualstudio/ide/visual-studio-multi-targeting-overview)

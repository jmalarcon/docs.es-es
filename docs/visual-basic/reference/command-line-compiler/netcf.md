---
title: -netcf
ms.date: 03/13/2018
f1_keywords:
- /netcf
- -netcf
helpviewer_keywords:
- -netcf compiler option [Visual Basic]
- netcf compiler option [Visual Basic]
- /netcf compiler option [Visual Basic]
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
ms.openlocfilehash: 3df7e622f97a5a1291736180e3964b1b3deaea2f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005454"
---
# <a name="-netcf"></a>-netcf

Establece el compilador para que tenga como destino el .NET Compact Framework.

## <a name="syntax"></a>Sintaxis

```console
-netcf
```

## <a name="remarks"></a>Comentarios

La opción `-netcf` hace que el compilador de Visual Basic tenga como destino la .NET Compact Framework en lugar de la .NET Framework completa. La funcionalidad del lenguaje que solo está presente en el .NET Framework completo está deshabilitada.

La opción `-netcf` está diseñada para usarse con [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md). Las características de lenguaje deshabilitadas por `-netcf` son las mismas que las características de lenguaje que no están presentes en los archivos de destino de `-sdkpath`.

> [!NOTE]
> La opción `-netcf` no está disponible en el entorno de desarrollo de Visual Studio; solo está disponible al compilar desde la línea de comandos. La opción `-netcf` se establece cuando se carga un proyecto de dispositivo Visual Basic.

La opción `-netcf` cambia las siguientes características del lenguaje:

- La palabra clave [End \<keyword > instrucción](../../../visual-basic/language-reference/statements/end-keyword-statement.md) , que finaliza la ejecución de un programa, está deshabilitada. El siguiente programa se compila y se ejecuta sin `-netcf`, pero produce un error en tiempo de compilación con `-netcf`.

  [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]

- El enlace en tiempo de ejecución, en todos los formularios, está deshabilitado. Se generan errores en tiempo de compilación cuando se encuentran escenarios de enlace en tiempo de ejecución reconocidos. El siguiente programa se compila y se ejecuta sin `-netcf`, pero produce un error en tiempo de compilación con `-netcf`.

  [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]

- Los modificadores [automático](../../../visual-basic/language-reference/modifiers/auto.md), [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md)y [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) están deshabilitados. La sintaxis de la instrucción [declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) también se modifica en `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`. En el código siguiente se muestra el efecto de `-netcf` en una compilación.

  [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]

- El uso de Visual Basic palabras clave 6,0 que se quitaron de Visual Basic genera un error diferente cuando se usa `-netcf`. Esto afecta a los mensajes de error de las palabras clave siguientes:

  - `Open`

  - `Close`

  - `Put`

  - `Print`

  - `Write`

  - `Input`

  - `Lock`

  - `Unlock`

  - `Seek`

  - `Width`

  - `Name`

  - `FreeFile`

  - `EOF`

  - `Loc`

  - `LOF`

  - `Line`

## <a name="example"></a>Ejemplo

El código siguiente compila `Myfile.vb` con el .NET Compact Framework, con las versiones de mscorlib. dll y Microsoft. VisualBasic. dll que se encuentran en el directorio de instalación predeterminado de la .NET Compact Framework en la unidad C. Normalmente, se usaría la versión más reciente de la .NET Compact Framework.

```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb
```

## <a name="see-also"></a>Vea también

- [Compilador de línea de comandos de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Líneas de comandos de compilación de ejemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)

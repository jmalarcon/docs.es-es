---
title: Niveles de acceso en Visual Basic
ms.date: 05/10/2018
helpviewer_keywords:
- members [Visual Basic], accessing in Visual Basic
- Friend access modifier
- access levels, declared elements
- access levels
- access modifiers
- Public access modifier
- Protected access modifier
- Protected Friend access modifier
- Private Protected access modifier
- Private access modifier
- declared elements [Visual Basic], access level
ms.assetid: 6e06c1ab-fd78-47f0-83a8-1152780b5e1a
ms.openlocfilehash: d1548f7850c68bc3c5422cf9d8d3d30eaa4aa8f3
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/29/2019
ms.locfileid: "73035888"
---
# <a name="access-levels-in-visual-basic"></a>Niveles de acceso en Visual Basic

El *nivel de acceso* de un elemento declarado es la extensión de la capacidad de obtener acceso a él, es decir, qué código tiene permiso para leerlo o escribir en él. Esto no solo se determina en la forma en que se declara el elemento en sí, sino también en el nivel de acceso del contenedor del elemento. El código que no puede tener acceso a un elemento contenedor no puede tener acceso a ninguno de sus elementos contenidos, incluso a los declarados como `Public`. Por ejemplo, se puede tener acceso a una variable de `Public` en una estructura de `Private` desde dentro de la clase que contiene la estructura, pero no desde fuera de esa clase.

## <a name="public"></a>Public

La palabra clave [Public](../../../language-reference/modifiers/public.md) de la instrucción de declaración especifica que se puede tener acceso al elemento desde el código en cualquier lugar del mismo proyecto, desde otros proyectos que hagan referencia al proyecto y desde cualquier ensamblado compilado a partir del proyecto. En el código siguiente se muestra una declaración de `Public` de ejemplo:

```vb
Public Class ClassForEverybody
```

Solo se puede usar `Public` en el nivel de módulo, interfaz o espacio de nombres. Esto significa que puede declarar un elemento público en el nivel de un archivo de código fuente o un espacio de nombres, o dentro de una interfaz, módulo, clase o estructura, pero no en un procedimiento.
  
## <a name="protected"></a>Protected

La palabra clave [Protected](../../../language-reference/modifiers/protected.md) de la instrucción de declaración especifica que solo se puede tener acceso al elemento desde dentro de la misma clase o desde una clase derivada de esta clase. En el código siguiente se muestra una declaración de `Protected` de ejemplo:

```vb
Protected Class ClassForMyHeirs
```

Solo se puede usar `Protected` en el nivel de clase y solo cuando se declara un miembro de una clase. Esto significa que puede declarar un elemento protegido en una clase, pero no en el nivel de un archivo de código fuente o un espacio de nombres, o dentro de una interfaz, un módulo, una estructura o un procedimiento.

## <a name="friend"></a>Friend

La palabra clave [Friend](../../../language-reference/modifiers/friend.md) de la instrucción declaration especifica que se puede tener acceso al elemento desde dentro del mismo ensamblado, pero no desde fuera del ensamblado. En el código siguiente se muestra una declaración de `Friend` de ejemplo:

```vb
Friend stringForThisProject As String
```

Solo se puede usar `Friend` en el nivel de módulo, interfaz o espacio de nombres. Esto significa que puede declarar un elemento Friend en el nivel de un archivo de código fuente o un espacio de nombres, o dentro de una interfaz, módulo, clase o estructura, pero no en un procedimiento.

## <a name="protected-friend"></a>Protected Friend

La combinación de palabras clave [Friend protegida](../../../language-reference/modifiers/protected-friend.md) de la instrucción de declaración especifica que se puede tener acceso al elemento desde clases derivadas o desde dentro del mismo ensamblado, o ambos. En el código siguiente se muestra una declaración de `Protected Friend` de ejemplo:

```vb
Protected Friend stringForProjectAndHeirs As String
```

Solo se puede usar `Protected Friend` en el nivel de clase y solo cuando se declara un miembro de una clase. Esto significa que puede declarar un elemento Friend protegido en una clase, pero no en el nivel de un archivo de código fuente o un espacio de nombres, o dentro de una interfaz, un módulo, una estructura o un procedimiento.

## <a name="private"></a>Private

La palabra clave [Private](../../../language-reference/modifiers/private.md) de la instrucción de declaración especifica que solo se puede tener acceso al elemento desde dentro del mismo módulo, clase o estructura. En el código siguiente se muestra una declaración de `Private` de ejemplo:

```vb
Private _numberForMeOnly As Integer
```

Solo se puede usar `Private` en un nivel de módulo. Esto significa que puede declarar un elemento privado dentro de un módulo, clase o estructura, pero no en el nivel de un archivo de código fuente o espacio de nombres, dentro de una interfaz o en un procedimiento.

En el nivel de módulo, la instrucción `Dim` sin palabras clave de nivel de acceso es equivalente a una declaración `Private`. Sin embargo, es posible que desee usar la palabra clave `Private` para que el código sea más fácil de leer e interpretar.

## <a name="private-protected"></a>Private Protected

La combinación de palabras clave [Private Protected](../../../language-reference/modifiers/private-protected.md) de la instrucción de declaración especifica que solo se puede tener acceso al elemento desde dentro de la misma clase, así como desde las clases derivadas que se encuentran en el mismo ensamblado que la clase contenedora. El modificador de acceso `Private Protected` se admite a partir de Visual Basic 15,5.

En el ejemplo siguiente se muestra una declaración de `Private Protected`:

```vb
Private Protected internalValue As Integer
```

Puede declarar un elemento `Private Protected` solo dentro de una clase. No puede declararlo en una interfaz o estructura, ni puede declararlo en el nivel de un archivo de código fuente o un espacio de nombres, dentro de una interfaz o una estructura, o en un procedimiento.

Visual Basic 15,5 y versiones posteriores admiten el modificador de acceso `Private Protected`. Para usarlo, agregue el siguiente elemento al archivo de proyecto de Visual Basic ( *\*. vbproj*). Siempre que Visual Basic 15,5 o posterior esté instalado en el sistema, le permite aprovechar todas las características de lenguaje compatibles con la versión más reciente del compilador de Visual Basic:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Para usar el modificador de acceso `Private Protected`, debe agregar el siguiente elemento al archivo de proyecto Visual Basic ( *\*. vbproj*):

```xml
<PropertyGroup>
   <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

Para obtener más información, vea [establecer la versión de lenguaje Visual Basic](../../../language-reference/configure-language-version.md).

## <a name="access-modifiers"></a>Modificadores de acceso

Las palabras clave que especifican el nivel de acceso se denominan *modificadores de acceso*. En la tabla siguiente se comparan los modificadores de acceso:

|Modificador de acceso|Nivel de acceso concedido|Elementos que puede declarar con este nivel de acceso|Contexto de declaración en el que puede usar este modificador|
|---------------------|--------------------------|-----------------------------------------------------|----------------------------------------------------------------|
|`Public`|Sin restricciones<br /><br /> Cualquier código que pueda ver un elemento público puede acceder a él|Interfaces<br /><br /> Módulos<br /><br /> Clases<br /><br /> Estructuras<br /><br /> Miembros de estructura<br /><br /> Procedimientos<br /><br /> Propiedades<br /><br /> Variables de miembro<br /><br /> Constantes<br /><br /> Enumeraciones<br /><br /> Events<br /><br /> Declaraciones externas<br /><br /> Delegados|Archivo de origen<br /><br /> Espacio de nombres<br /><br /> Interfaz<br /><br /> Module<br /><br /> Clase<br /><br /> Estructura|
|`Protected`|Derivación:<br /><br /> El código de la clase que declara un elemento protegido, o una clase derivada de él, puede tener acceso al elemento.|Interfaces<br /><br /> Clases<br /><br /> Estructuras<br /><br /> Procedimientos<br /><br /> Propiedades<br /><br /> Variables de miembro<br /><br /> Constantes<br /><br /> Enumeraciones<br /><br /> Events<br /><br /> Declaraciones externas<br /><br /> Delegados|Clase|
|`Friend`|Ensamblado:<br /><br /> El código del ensamblado que declara un elemento Friend puede tener acceso a él|Interfaces<br /><br /> Módulos<br /><br /> Clases<br /><br /> Estructuras<br /><br /> Miembros de estructura<br /><br /> Procedimientos<br /><br /> Propiedades<br /><br /> Variables de miembro<br /><br /> Constantes<br /><br /> Enumeraciones<br /><br /> Events<br /><br /> Declaraciones externas<br /><br /> Delegados|Archivo de origen<br /><br /> Espacio de nombres<br /><br /> Interfaz<br /><br /> Module<br /><br /> Clase<br /><br /> Estructura|
|`Protected` `Friend`|Unión de `Protected` y `Friend`:<br /><br /> El código de la misma clase o del mismo ensamblado que un elemento Friend protegido, o dentro de cualquier clase derivada de la clase del elemento, puede tener acceso a él.|Interfaces<br /><br /> Clases<br /><br /> Estructuras<br /><br /> Procedimientos<br /><br /> Propiedades<br /><br /> Variables de miembro<br /><br /> Constantes<br /><br /> Enumeraciones<br /><br /> Events<br /><br /> Declaraciones externas<br /><br /> Delegados|Clase|
|`Private`|Contexto de declaración:<br /><br /> El código del tipo que declara un elemento privado, incluido el código dentro de los tipos contenidos, puede tener acceso al elemento.|Interfaces<br /><br /> Clases<br /><br /> Estructuras<br /><br /> Miembros de estructura<br /><br /> Procedimientos<br /><br /> Propiedades<br /><br /> Variables de miembro<br /><br /> Constantes<br /><br /> Enumeraciones<br /><br /> Events<br /><br /> Declaraciones externas<br /><br /> Delegados|Module<br /><br /> Clase<br /><br /> Estructura|
|`Private Protected`|Código de la clase que declara un elemento protegido privado o código en una clase derivada que se encuentra en el mismo ensamblado que la clase Bas.|Interfaces<br /><br /> Clases<br /><br /> Estructuras<br /><br /> Procedimientos<br /><br /> Propiedades<br /><br /> Variables de miembro<br /><br /> Constantes<br /><br /> Enumeraciones<br /><br /> Events<br /><br /> Declaraciones externas<br /><br /> Delegados|Clase|

## <a name="see-also"></a>Vea también

- [Dim (instrucción)](../../../language-reference/statements/dim-statement.md)
- [Static](../../../language-reference/modifiers/static.md)
- [Nombres de elementos declarados](declared-element-names.md)
- [Referencias a elementos declarados](references-to-declared-elements.md)
- [Características de los elementos declarados](declared-element-characteristics.md)
- [Duración en Visual Basic](lifetime.md)
- [Ámbito en Visual Basic](scope.md)
- [Controlar la disponibilidad de una variable](how-to-control-the-availability-of-a-variable.md)
- [Variables](../variables/index.md)
- [Declaración de variables](../variables/variable-declaration.md)

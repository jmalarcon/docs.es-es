---
title: Elemento <TimeSpan_LegacyFormatMode>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
ms.openlocfilehash: c835e1bcef7bbfdc990c8db177eafed4ec6bb30c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115216"
---
# <a name="timespan_legacyformatmode-element"></a>\<elemento > TimeSpan_LegacyFormatMode

Determina si el tiempo de ejecución conserva el comportamiento heredado en operaciones de formato con valores <xref:System.TimeSpan?displayProperty=nameWithType>.

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<en tiempo de ejecución >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<TimeSpan_LegacyFormatMode >**  

## <a name="syntax"></a>Sintaxis

```xml
<TimeSpan_LegacyFormatMode
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|`enabled`|Atributo necesario.<br /><br /> Especifica si el Runtime usa el comportamiento de formato heredado con valores <xref:System.TimeSpan?displayProperty=nameWithType>.|

## <a name="enabled-attribute"></a>Atributo enabled

|Valor|Descripción|
|-----------|-----------------|
|`false`|El motor en tiempo de ejecución no restaura el comportamiento de formato heredado.|
|`true`|El motor en tiempo de ejecución restaura el comportamiento de formato heredado.|

### <a name="child-elements"></a>Elementos secundarios

Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|`configuration`|Elemento raíz de cada archivo de configuración usado por las aplicaciones de Common Language Runtime y .NET Framework.|
|`runtime`|Contiene información sobre las opciones de inicialización del motor en tiempo de ejecución.|

## <a name="remarks"></a>Comentarios

A partir de la .NET Framework 4, la estructura de <xref:System.TimeSpan?displayProperty=nameWithType> implementa la interfaz <xref:System.IFormattable> y admite operaciones de formato con cadenas de formato estándar y personalizadas. Si un método de análisis encuentra un especificador de formato no compatible o una cadena de formato, produce una <xref:System.FormatException>.

En versiones anteriores del .NET Framework, la estructura de <xref:System.TimeSpan> no implementaba <xref:System.IFormattable> y no admitía cadenas de formato. Sin embargo, muchos desarrolladores suponían erróneamente que <xref:System.TimeSpan> admitía un conjunto de cadenas de formato y las usaban en [operaciones de formato compuesto](../../../../standard/base-types/composite-formatting.md) con métodos como <xref:System.String.Format%2A?displayProperty=nameWithType>. Normalmente, si un tipo implementa <xref:System.IFormattable> y admite cadenas de formato, las llamadas a métodos de formato con cadenas de formato no admitidas normalmente inician una <xref:System.FormatException>. Sin embargo, dado que <xref:System.TimeSpan> no implementó <xref:System.IFormattable>, el tiempo de ejecución omitió la cadena de formato y, en su lugar, llamó al método <xref:System.TimeSpan.ToString?displayProperty=nameWithType>. Esto significa que, aunque las cadenas de formato no tenían ningún efecto en la operación de formato, su presencia no produjo una <xref:System.FormatException>.

En los casos en los que el código heredado pasa un método de formato compuesto y una cadena de formato no válida, y ese código no se puede volver a compilar, puede usar el elemento `<TimeSpan_LegacyFormatMode>` para restaurar el comportamiento de la <xref:System.TimeSpan> heredada. Al establecer el `enabled` atributo de este elemento en `true`, el método de formato compuesto produce una llamada a <xref:System.TimeSpan.ToString?displayProperty=nameWithType> en lugar de <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>y no se produce una <xref:System.FormatException>.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se crea una instancia de un objeto <xref:System.TimeSpan> e intenta aplicarle formato con el método <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> mediante una cadena de formato estándar no compatible.

[!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
[!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]

Al ejecutar el ejemplo en el .NET Framework 3,5 o en una versión anterior, se muestra el siguiente resultado:

```
12:30:45
```

Esto difiere notablemente de la salida si ejecuta el ejemplo en el .NET Framework 4 o una versión posterior:

```
Invalid Format
```

Sin embargo, si agrega el archivo de configuración siguiente al directorio del ejemplo y, a continuación, ejecuta el ejemplo en el .NET Framework 4 o una versión posterior, la salida es idéntica a la generada por el ejemplo cuando se ejecuta en .NET Framework 3,5.

```xml
<?xml version ="1.0"?>
<configuration>
   <runtime>
      <TimeSpan_LegacyFormatMode enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Vea también

- [Esquema de la configuración de Common Language Runtime](index.md)
- [Esquema de los archivos de configuración](../index.md)

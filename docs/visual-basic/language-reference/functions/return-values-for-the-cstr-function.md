---
title: Valores devueltos para la función CStr (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- times [Visual Basic], CStr Function return values
- type conversion [Visual Basic]
- dates [Visual Basic], CStr Function return values
- CStr function
- strings [Visual Basic], return value
- Date data type [Visual Basic], converting
- dates [Visual Basic]
- String data type [Visual Basic], converting
ms.assetid: 3aa744e7-1419-45d5-85e3-e5abc2953673
ms.openlocfilehash: cd525ea5a295411e509f3bc37285675d15a8c4f4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930049"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a>Valores devueltos para la función CStr (Visual Basic)
En la tabla siguiente se describen los valores `CStr` devueltos para para `expression`distintos tipos de datos de.  
  
|Si `expression` el tipo es|Devoluciones de `CStr`|  
|-----------------------------|--------------------|  
|[Boolean (tipo de datos)](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Cadena que contiene "true" o "false".|  
|[Date (tipo de datos)](../../../visual-basic/language-reference/data-types/date-data-type.md)|Cadena que contiene un `Date` valor (fecha y hora) en el formato de fecha corta del sistema.|  
|[Tipos de datos numéricos](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|Cadena que representa el número.|  
  
## <a name="cstr-and-date"></a>CStr y Date  
 El `Date` tipo siempre contiene información de fecha y hora. A efectos de la conversión de tipos, Visual Basic considera 1/1/0001 (1 de enero del año 1) para que sea un *valor neutro* para la fecha y 00:00:00 (medianoche) como valor neutro para el tiempo. `CStr`no incluye valores neutros en la cadena resultante. Por ejemplo, si convierte `#January 1, 0001 9:30:00#` en una cadena, el resultado es "9:30:00 AM"; se suprime la información de fecha. Sin embargo, la información de fecha todavía está presente en `Date` el valor original y se puede recuperar con funciones <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>como.  
  
> [!NOTE]
> La `CStr` función realiza su conversión en función de la configuración de la referencia cultural actual de la aplicación. Para obtener la representación en forma de cadena de un número en una referencia cultural determinada, `ToString(IFormatProvider)` use el método del número. Por ejemplo, se <xref:System.Double.ToString%2A?displayProperty=nameWithType> usa al convertir un valor de `Double` tipo en `String`.  
  
## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [Funciones de conversión de tipos](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Boolean (tipo de datos)](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Date (tipo de datos)](../../../visual-basic/language-reference/data-types/date-data-type.md)

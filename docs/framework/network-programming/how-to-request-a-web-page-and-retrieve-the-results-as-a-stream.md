---
title: Procedimiento para solicitar una página web y recuperar los resultados como una secuencia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: 65bda268cd77959dbcd786c365d0a30c324b89ce
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71393110"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a>Procedimiento para solicitar una página web y recuperar los resultados como una secuencia

En este ejemplo se muestra cómo solicitar una página web y recuperar los resultados en una secuencia.
  
## <a name="example"></a>Ejemplo

```csharp
var myClient = new WebClient();
Stream response = myClient.OpenRead("https://docs.microsoft.com/dotnet/");
// The stream data is used here.
response.Close();
```

```vb
Dim myClient As New WebClient()
Dim response As Stream = myClient.OpenRead("https://docs.microsoft.com/dotnet/")
' The stream data is used here.
response.Close()
```

## <a name="compiling-the-code"></a>Compilar el código

 Para este ejemplo se necesita:

- Referencias a los espacios de nombres <xref:System.IO> y <xref:System.Net>.

## <a name="see-also"></a>Vea también

- [Solicitud de datos](requesting-data.md)

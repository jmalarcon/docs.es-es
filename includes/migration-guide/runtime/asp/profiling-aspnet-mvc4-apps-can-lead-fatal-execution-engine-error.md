---
ms.openlocfilehash: 107b34c7bd26e1396e8a6638d6929c15de92b8e4
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803158"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a>Las aplicaciones de MVC4 de generación de perfiles de ASP.NET pueden provocar el error irrecuperable de motor de ejecución

|   |   |
|---|---|
|Detalles|Los generadores de perfiles que usan ensamblados /Profile de NGEN pueden bloquear las aplicaciones de MVC4 con perfiles de ASP.NET durante el inicio con una "Excepción irrecuperable de motor de ejecución".|
|Sugerencia|Este problema se ha corregido en .NET Framework 4.5.2. Como alternativa, el generador de perfiles puede evitar este problema mediante la especificación de <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> en su máscara de eventos.|
|Ámbito|Borde|
|Versión|4.5|
|Tipo|Tiempo de ejecución|


---
ms.openlocfilehash: f007a2b81820a1d25a2d101b35f3a49e7794fec1
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859109"
---
### <a name="workflow-checksums-changed-from-md5-to-sha1"></a>Las sumas de comprobación de flujo de trabajo han cambiado de MD5 a SHA1

|   |   |
|---|---|
|Detalles|Para admitir la depuración con Visual Studio, el tiempo de ejecución de flujo de trabajo genera una suma de comprobación para una instancia de flujo de trabajo mediante un algoritmo de hash. En .NET Framework 4.6.2 y versiones anteriores, el hash de suma de comprobación de flujo de trabajo usaba el algoritmo MD5, que causaba problemas en sistemas compatibles con FIPS. A partir de .NET Framework 4.7, el algoritmo es SHA1. Si se han conservado estas sumas de comprobación en el código, serán incompatibles.|
|Sugerencia|Si el código no puede cargar las instancias de flujo de trabajo debido a un error de suma de comprobación, pruebe a establecer el modificador <code>AppContext</code> &quot;Switch.System.Activities.UseMD5ForWFDebugger&quot; en true. En el código:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Activities.UseMD5ForWFDebugger&quot;, true);&#13;&#10;</code></pre>O bien, en la configuración:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Activities.UseMD5ForWFDebugger=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Ámbito|Secundaria|
|Versión|4.7|
|Tipo|Redestinación|


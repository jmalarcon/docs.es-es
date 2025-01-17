---
ms.openlocfilehash: 745e880db08c5fa7e5514a71758f7fbb042e7ef4
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858932"
---
### <a name="the-default-hash-algorithm-for-wpf-packagedigitalsignaturemanager-is-now-sha256"></a>El algoritmo hash predeterminado para PackageDigitalSignatureManager de WPF ahora es SHA256

|   |   |
|---|---|
|Detalles|<code>System.IO.Packaging.PackageDigitalSignatureManager</code> proporciona funcionalidad para las firmas digitales en relación con los paquetes de WPF.  En .NET Framework 4.7 y versiones anteriores, el algoritmo predeterminado (<xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>) que se usaba para firmar los elementos de un paquete era SHA1.  Por motivos de seguridad recientes con SHA1, este valor predeterminado se ha cambiado a SHA256 a partir de .NET Framework 4.7.1.  Este cambio afecta a todas las firmas de paquetes, incluidos los documentos XPS.|
|Sugerencia|Un desarrollador que quiera usar este cambio mientras selecciona como destino una versión de la plataforma inferior a .NET Framework 4.7.1 o un desarrollador que requiera la funcionalidad anterior mientras selecciona como destino .NET Framework 4.7.1 o una versión posterior pueden establecer de manera apropiada la marca de AppContext siguiente.  Un valor de true dará como resultado el uso de SHA1 como el algoritmo predeterminado; false hará que se use SHA256.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.UseSha1AsDefaultHashAlgorithmForDigitalSignatures=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Ámbito|Borde|
|Versión|4.7.1|
|Tipo|Redestinación|
|API afectadas|<ul><li><xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType></li></ul>|


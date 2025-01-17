---
ms.openlocfilehash: 846a6bcd3c668e6ad505f745bcb830c3b9dce437
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859313"
---
### <a name="aescryptoserviceprovider-decryptor-provides-a-reusable-transform"></a>El descifrador AesCryptoServiceProvider proporciona una transformación reutilizable

|   |   |
|---|---|
|Detalles|A partir de las aplicaciones que tienen como destino .NET Framework 4.6.2, el descifrador <xref:System.Security.Cryptography.AesCryptoServiceProvider> ofrece una transformación reutilizable. Después de llamar a <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=name>, la transformación se reinicializa y se puede reutilizar. Para las aplicaciones que tienen como destino versiones anteriores de .NET Framework, intentar volver a usar el descifrador mediante una llamada a <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=name> después de llamar a <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=name> inicia una excepción <xref:System.Security.Cryptography.CryptographicException> o genera datos dañados.|
|Sugerencia|El impacto de este cambio debería ser mínimo, dado que es el comportamiento esperado. Las aplicaciones que dependen del comportamiento anterior pueden rechazar su uso si se agrega el ajuste de configuración siguiente a la sección <code>&lt;runtime&gt;</code> del archivo de configuración de la aplicación:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Además, las aplicaciones que tienen como destino una versión anterior de .NET Framework pero que se ejecutan en una versión de .NET Framework a partir de la 4.6.2 pueden incluirse en este comportamiento si se agrega el ajuste de configuración siguiente a la sección <code>&lt;runtime&gt;</code> del archivo de configuración de la aplicación:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Ámbito|Secundaria|
|Versión|4.6.2|
|Tipo|Redestinación|
|API afectadas|<ul><li><xref:System.Security.Cryptography.AesCryptoServiceProvider.CreateDecryptor?displayProperty=nameWithType></li></ul>|


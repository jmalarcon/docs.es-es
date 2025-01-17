---
title: 'Mitigación: marcos PNG en objetos de icono'
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85a76681cf6efd649fe366a68d956246334975fe
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789975"
---
# <a name="mitigation-png-frames-in-icon-objects"></a>Mitigación: marcos PNG en objetos de icono
A partir de .NET Framework 4.6, el método <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> convierte correctamente iconos con marcos PNG en objetos <xref:System.Drawing.Bitmap> .  
  
 En aplicaciones destinadas a .NET Framework 4.5.2 y versiones anteriores, el método <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> genera una excepción <xref:System.ArgumentOutOfRangeException> si el objeto <xref:System.Drawing.Icon> tiene marcos PNG.  
  
## <a name="impact"></a>Impacto  
 Este cambio afecta a las aplicaciones que se vuelven a compilar para tener como destino .NET Framework 4.6 y que implementan un control especial para <xref:System.ArgumentOutOfRangeException> que se genera cuando un objeto <xref:System.Drawing.Icon> tiene marcos PNG. Cuando se ejecuta en .NET Framework 4.6, la conversión es correcta, ya no se genera un <xref:System.ArgumentOutOfRangeException> y, por tanto, ya no se invoca el controlador de excepciones.  
  
### <a name="mitigation"></a>Mitigación  
 Si no desea este comportamiento, puede conservar el comportamiento anterior agregando el siguiente elemento en la sección [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) del archivo app.config:  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 Si el archivo app.config ya contiene el elemento `AppContextSwitchOverrides` , el nuevo valor se debe combinar con el atributo `value` como este:  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a>Vea también

- [Cambios de redestinación](retargeting-changes-in-the-net-framework-4-6.md)

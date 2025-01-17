---
title: <relativeBindForResources> (Elemento)
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: 6a418fc546313b74bb965a0b223eca9c2e5acc08
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115800"
---
# <a name="relativebindforresources-element"></a>\<elemento > relativeBindForResources
Optimiza el sondeo de ensamblados satélite.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<en tiempo de ejecución >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<relativeBindForResources >**  
  
## <a name="syntax"></a>Sintaxis  
  
```xml
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`enabled`|Atributo necesario.<br /><br /> Especifica si el Common Language Runtime optimiza el sondeo para los ensamblados satélite.|  
  
## <a name="enabled-attribute"></a>Atributo enabled  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`false`|El motor en tiempo de ejecución no optimiza el sondeo de ensamblados satélite. Este es el valor predeterminado.|  
|`true`|El motor en tiempo de ejecución optimiza el sondeo de los ensamblados satélite.|  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|`configuration`|Elemento raíz de cada archivo de configuración usado por las aplicaciones de Common Language Runtime y .NET Framework.|  
|`runtime`|Contiene información sobre las opciones de inicialización del motor en tiempo de ejecución.|  
  
## <a name="remarks"></a>Comentarios  
 En general, Administrador de recursos sondea los recursos, tal como se documenta en el tema [empaquetar e implementar recursos](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) . Esto significa que, cuando Administrador de recursos sondea una versión localizada determinada de un recurso, puede buscar en la caché global de ensamblados, buscar en una carpeta específica de la referencia cultural en la base de código de la aplicación, Windows Installer de consulta para los ensamblados satélite y generar el evento <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>. El elemento `<relativeBindForResources>` optimiza el modo en que Administrador de recursos sondea para los ensamblados satélite. Puede mejorar el rendimiento al buscar recursos en las siguientes condiciones:  
  
- Cuando el ensamblado satélite se implementa en la misma ubicación que el ensamblado de código. En otras palabras, si el ensamblado de código está instalado en la caché global de ensamblados, los ensamblados satélite también se deben instalar allí. Si el ensamblado de código está instalado en la base de código de la aplicación, los ensamblados satélite también se deben instalar en una carpeta específica de la referencia cultural en el código base.  
  
- Cuando Windows Installer no se usa o solo se usa con poca frecuencia para la instalación a petición de ensamblados satélite.  
  
- Cuando el código de aplicación no controla el evento <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.  
  
 Al establecer el atributo `enabled` del elemento `<relativeBindForResources>` en `true`, se optimiza el sondeo de Administrador de recursos para los ensamblados satélite de la manera siguiente:  
  
- Utiliza la ubicación del ensamblado de código primario para sondear el ensamblado satélite.  
  
- No consulta Windows Installer para los ensamblados satélite.  
  
- No genera el evento <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Vea también

- [Empaquetar e implementar recursos](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [Esquema de la configuración de Common Language Runtime](index.md)
- [Esquema de los archivos de configuración](../index.md)

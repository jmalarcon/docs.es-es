---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: c901daf4d442a206345301795c7a4bdc076329cd
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252091"
---
# <a name="claimsauthenticationmanager"></a>\<claimsAuthenticationManager>
Registra un administrador de autenticación de notificaciones para las notificaciones entrantes.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identityConfiguration**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> claimsAuthenticationManager**  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|DESCRIPCIÓN|  
|---------------|-----------------|  
|type|Especifica un tipo personalizado que deriva de la <xref:System.Security.Claims.ClaimsAuthenticationManager> clase. Para obtener más información sobre cómo especificar el `type` atributo, vea [referencias de tipo personalizado].|  
  
### <a name="child-elements"></a>Elementos secundarios  
 Si no hay ningún `type` atributo, o si el `type` atributo hace referencia <xref:System.Security.Claims.ClaimsAuthenticationManager> a la clase `<claimsAuthenticationManager>` , el elemento no toma los elementos secundarios; sin embargo, <xref:System.Security.Claims.ClaimsAuthenticationManager> las clases derivadas de pueden definir elementos de configuración secundarios.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|DESCRIPCIÓN|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|Especifica la configuración de identidad de nivel de servicio.|  
  
## <a name="remarks"></a>Comentarios  
 El comportamiento predeterminado proporcionado a través <xref:System.Security.Claims.ClaimsAuthenticationManager> de la clase repite las notificaciones entrantes. Si no `type` se especifica ningún atributo o si `type` el atributo especifica <xref:System.Security.Claims.ClaimsAuthenticationManager> la clase, `<claimsAuthenticationManager>` el elemento no toma los elementos secundarios. Puede especificar el `type` atributo para registrar un tipo derivado de la <xref:System.Security.Claims.ClaimsAuthenticationManager> clase para implementar el comportamiento personalizado. Las clases derivadas pueden admitir la configuración a través `<claimsAuthenticationManager>` de elementos secundarios del elemento <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> invalidando el método para controlar estos elementos. El esquema definido para los elementos secundarios es hasta el diseñador de la clase.  
  
 El `<claimsAuthenticationManager>` elemento establece la <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> propiedad.  
  
## <a name="example"></a>Ejemplo  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</system.identityModel>  
```

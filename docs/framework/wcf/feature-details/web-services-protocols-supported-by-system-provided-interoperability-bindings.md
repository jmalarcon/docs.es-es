---
title: Protocolos de servicios Web compatibles con los enlaces de interoperabilidad proporcionados por el sistema
ms.date: 03/30/2017
helpviewer_keywords:
- WS-protocols
- Web services protocols
- Windows Communication Foundation, Web service protocols
ms.assetid: 1f7fc4ff-30fe-4e46-adda-91caad3b06c6
ms.openlocfilehash: 963325604f66ddd4f8470933584b7880c86403bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951559"
---
# <a name="web-services-protocols-supported-by-system-provided-interoperability-bindings"></a>Protocolos de servicios Web compatibles con los enlaces de interoperabilidad proporcionados por el sistema
Windows Communication Foundation (WCF) se crea para interoperar con los servicios web que admiten un conjunto de especificaciones conocidas como especificaciones de servicios Web. Para simplificar la configuración del servicio para los procedimientos recomendados de interoperabilidad, WCF introduce tres enlaces interoperables proporcionados por el sistema: <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>, <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType>y <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>. Para la interoperabilidad con la organización para el avance de estándares de la información estructurada (OASIS), WCF incluye un enlace proporcionado <xref:System.ServiceModel.WS2007HttpBinding?displayProperty=nameWithType>por el sistema interoperable:. En la publicación de metadatos, WCF incluye dos enlaces proporcionados por el sistema interoperables: [ \<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) y [ \<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md). En este tema se enumeran las especificaciones que admiten los enlaces interoperables proporcionados por el sistema.  
  
## <a name="web-services-protocols-supported-by-basichttpbinding-wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding-bindings"></a>Protocolos de servicios Web admitidos por basicHttpBinding, wsHttpBinding, ws2007HttpBinding y enlaces wsDualHttpBinding  
  
### <a name="all-bindings"></a>Todos los enlaces  
 Los enlaces de [ \<> basicHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)y [ \<> ws2007HttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) admiten los siguientes protocolos.  
  
> [!NOTE]
> Para obtener información sobre los enlaces usados para publicar metadatos, consulte la sección "Enlaces de metadatos proporcionados por el sistema" más adelante en este tema.  
  
|Categoría|Protocol|Especificación y uso|  
|--------------|--------------|-----------------------------|  
|Transporte|HTTP 1.1|[HTTP 1.1](https://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> `BasicHttpBinding`, `WSHttpBinding`y `WS2007HttpBinding` utilizan los transportes HTTP y HTTPS.|  
|Mensajería|MTOM|[MTOM](https://go.microsoft.com/fwlink/?LinkId=95326)<br /><br /> `basicHttpBinding`, `wsHttpBinding`y `ws2007HttpBinding` admiten el Mecanismo de optimización de transmisión de mensajes (MTOM). No utilizado de manera predeterminada: Para utilizar MTOM, defina el atributo `messageEncoding` como `"Mtom"`.<br /><br /> Ejemplo:<br /><br /> `<wsHttpBinding> <binding messageEncoding="Mtom"/> </wsHttpBinding>`|  
|Metadatos|WSDL 1.1|[WSDL 1.1](https://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> WCF usa el lenguaje de descripción de servicios web (WSDL) para describir los servicios.|  
|Metadatos|WS-Policy|[WS-Policy](https://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> WCF usa la especificación WS-Policy junto con las aserciones específicas del dominio para describir las capacidades y los requisitos del servicio.|  
|Metadatos|WS-Policy 1.5|[WS-Policy 1,5](https://go.microsoft.com/fwlink/?LinkId=95327)<br /><br /> WCF usa la especificación WS-Policy junto con las aserciones específicas del dominio para describir las capacidades y los requisitos del servicio.|  
|Metadatos|WS-PolicyAttachment|[WS-PolicyAttachment](https://go.microsoft.com/fwlink/?LinkId=95328)<br /><br /> WCF implementa WS-PolicyAttachment para adjuntar expresiones de directiva en varios ámbitos del lenguaje de descripción de servicios web (WSDL).|  
|Metadatos|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> WCF implementa WS-MetadataExchange para recuperar el esquema XML, WSDL y WS-Policy.|  
  
### <a name="basichttpbinding"></a>basicHttpBinding  
  
|Categoría|Protocol|Especificación y uso|  
|--------------|--------------|-----------------------------|  
|Mensajería|SOAP 1,1|[SOAP 1.1](https://go.microsoft.com/fwlink/?LinkId=90520)<br /><br /> De acuerdo con Basic Profile 1.1, el elemento `basicHttpBinding` implementa el protocolo de mensajes SOAP 1.1.|  
|Seguridad|WSS SOAP Message Security 1.0|[Seguridad del mensaje SOAP de WSS 1,0](https://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> De acuerdo con el perfil de seguridad básico, el elemento `basicHttpBinding` implementa la especificación de seguridad de mensaje SOAP 1.0 de Seguridad de Servicios web (WSS) para el nombre de usuario/contraseña y la seguridad basada en X.509.<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential &#124;                     "Message" .../> </binding> </basicHttpBinding>`|  
|Seguridad|Perfil UsernameToken 1.0 de seguridad de mensaje WSS SOAP|[Perfil UsernameToken de seguridad de mensajes SOAP de WSS 1,0](https://go.microsoft.com/fwlink/?LinkId=95334)<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential"> <transport clientCredentialType="Basic"/> </security> </basicHttpBinding>`|  
|Seguridad|Perfil de token de certificado X.509 de seguridad de mensaje WSS SOAP 1.1|[Perfil de token de certificado X. 509 de seguridad de mensajes de WSS SOAP 1,0](https://go.microsoft.com/fwlink/?LinkId=95335)<br /><br /> `<basicHttpBinding>   <security mode="Message"> <message clientCredentialType="Certificate"/> </security> </basicHttpBinding>`|  
  
### <a name="wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding"></a>wsHttpBinding, ws2007HttpBinding y wsDualHttpBinding  
  
|Categoría|Protocol|Especificación y uso|  
|--------------|--------------|-----------------------------|  
|Mensajería|SOAP 1.2|[Manual](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Marco de mensajería](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuntos (incluido el enlace HTTP)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|Mensajería|WS-Addressing 2005/08|[Direccionamiento de servicios Web 1,0-núcleo](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Direccionamiento de servicios Web 1,0-SOAP](https://go.microsoft.com/fwlink/?LinkId=95330)<br /><br /> `wsHttpBinding`, `ws2007HttpBinding`y `wsDualHttpBinding` implementan la recomendación WS-Addressing del World Wide Web Consortium (W3C) para habilitar la mensajería asincrónica, la correlación de mensajes y mecanismos de direccionamiento independiente del transporte.<br /><br /> WCF no admite el cifrado de encabezados de WS-Addressing aunque lo permiten las especificaciones de WS-*.|  
|Mensajería|WS-Addressing 1.0 - Metadatos|[Metadatos de WS-addressing 1,0](https://www.w3.org/2007/05/addressing/metadata) La compatibilidad con este protocolo se habilita estableciendo la versión de la Directiva en ServiceMetadata Behavior-with policyversion establecido en 1,2 (el valor predeterminado), la descripción de WSDL es compatible con el WSDL de WS-Addressing, con policyversion establecido en 1,5, la descripción de WSDL es compatible con los metadatos de WS-Addressing.<br /><br /> WCF no admite el cifrado de encabezados de WS-Addressing aunque lo permiten las especificaciones de WS-*.|  
|Seguridad|WSS SOAP Message Security 1.0|[Seguridad del mensaje SOAP de WSS 1,0](https://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> Utilícese cuando el atributo `securityMode` está definido como "wsSecurityOverHttp" (valor predeterminado) y los parámetros se configuran utilizando un elemento secundario `wsSecurity`.<br /><br /> `<wsHttpBinding>   <binding name="myBinding">      <security mode="Message" .../>   </binding> </wsHttpBinding>`|  
|Seguridad|Perfil UsernameToken de seguridad de mensajes SOAP de WSS 1,1|[Perfil UsernameToken de seguridad de mensajes SOAP de WSS 1,0](https://go.microsoft.com/fwlink/?LinkId=95331)<br /><br /> Utilice cuando el atributo `wsSecurity` del elemento `authenticationMode` esté definido como "Nombre de usuario."<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="UserName        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security> </binding> </wsHttpBinding>`|  
|Seguridad|WSS SOAP Message Security X.509 Certificate Token Profile 1.1|[Perfil de token de certificado X. 509 de seguridad de mensajes de WSS SOAP 1,1](https://go.microsoft.com/fwlink/?LinkId=95332)<br /><br /> Utilice para la protección del mensaje cuando el atributo `wsSecurity` del elemento `authenticationMode` está definido como "Nombre de usuario", "Certificado" o "Ninguno." Además, utilice esto para la autenticación del cliente cuando el atributo del `wsSecurity` de elemento `authenticationMode` se defina como "Certificado".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Certificate"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Seguridad|WSS SOAP Message Security Kerberos Token Profile 1.1|[Perfil de token de Kerberos de seguridad de mensajes SOAP de WSS 1,1](https://go.microsoft.com/fwlink/?LinkId=95333)<br /><br /> Utilice para la autenticación y protección de mensajes cuando el atributo `wsSecurity` del elemento `authenticationMode` esté definido en "Windows".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Windows"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Seguridad|WS-SecureConversation|[WS-SecureConversation](https://go.microsoft.com/fwlink/?LinkId=95317)<br /><br /> Utilice para proporcionar una sesión segura cuando el atributo `security/@mode` esté establecido en "Mensaje" y el atributo `message/@establishSecurityContext` está establecido en "true" (valor predeterminado).|  
|Seguridad|WS-Trust|[WS-Trust](https://go.microsoft.com/fwlink/?LinkId=95318)<br /><br /> Utilizado por WS-SecureConversation (vea arriba).|  
|Mensajería de confianza|WS-ReliableMessaging|[WS-ReliableMessaging](https://go.microsoft.com/fwlink/?LinkId=95322)<br /><br /> Utilícese cuando se configura el enlace para que use `reliableSession`.<br /><br /> `<wsHttpBinding>  <binding name="myBinding">    <reliableSession/>   </binding> </wsHttpBinding>`|  
|Transacciones|Transacción WS-Atomic|[WS-AtomicTransaction](https://go.microsoft.com/fwlink/?LinkId=95323)<br /><br /> Se usa para la comunicación entre administradores de transacciones. Los clientes y servicios de WCF siempre usan administradores de transacciones locales.|  
|Transacciones|WS-Coordination|[WS-Coordination](https://go.microsoft.com/fwlink/?LinkId=95324)<br /><br /> Utilícese para hacer fluir el contexto de transacción cuando el atributo `flowTransactions` se establece en "Allowed" (Permitido) o "Required" (Obligatorio).<br /><br /> `<wsHttpBinding>   <binding transactionFlow="true"/> </wsHttpBinding>`|  
  
## <a name="wsfederationhttpbinding-and-ws2007federationhttpbinding"></a>wsFederationHttpBinding y ws2007FederationHttpBinding  
 Se introdujeron los [ \<elementos wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) y [ \<ws2007FederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) para proporcionar compatibilidad con escenarios federados, donde un tercero emite un token que se usa para autenticar a un cliente. Además de los protocolos utilizados por `wsHttpBinding`, `wsFederationHttpBinding` utiliza:  
  
- `WS-Trust` para la emisión de tokens.  
  
- El Perfil 1.0 y 1.1 de tokens de lenguaje de marcado de aserciones de seguridad (SAML) WSS para el formato de tokens emitidos más comúnmente.  
  
 Ejemplo:  
  
```xml  
<wsFederationHttpBinding>  
  <binding name="myBinding">  
     <security mode="Message">  
       <message issuedKeyType="Symmetric"   
                issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
         <issuerMetadata address =   
         'http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex'>  
       </message>  
     </security>  
  </binding>  
</wsFederationHttpBinding>  
```  
  
 Para obtener más información, vea [Federation](../../../../docs/framework/wcf/feature-details/federation.md) .  
  
## <a name="system-provided-metadata-bindings"></a>Enlaces de metadatos proporcionados por el sistema  
 Las tablas siguientes describen los protocolos admitidos por los enlaces de metadatos interoperables proporcionados por el sistema expuestos por la clase <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType>.  
  
### <a name="mexhttpbinding"></a>mexHttpBinding  
 El enlace de [ \<> de mexHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) admite los siguientes protocolos. Para obtener más información sobre el uso de este enlace, vea [Publicar metadatos](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Categoría|Protocol|Especificación y uso|  
|--------------|--------------|-----------------------------|  
|Transporte|HTTP 1.1|[HTTP 1.1](https://go.microsoft.com/fwlink/?LinkId=84048)|  
|Mensajería|SOAP 1.2|[Manual](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Marco de mensajería](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuntos (incluido el enlace HTTP)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|Mensajería|WS-Addressing 2005/08|[Direccionamiento de servicios Web 1,0-núcleo](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Direccionamiento de servicios Web 1,0-SOAP](https://go.microsoft.com/fwlink/?LinkId=95330)|  
|Metadatos|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> WCF implementa WS-MetadataExchange para recuperar el esquema XML, WSDL y WS-Policy.|  
  
### <a name="mexhttpsbinding"></a>mexHttpsBinding  
 mexHttpsBinding > admite los siguientes protocolos. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md) Para obtener más información sobre el uso de este enlace, vea [Publicar metadatos](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Categoría|Protocol|Especificación y uso|  
|--------------|--------------|-----------------------------|  
|Transporte|HTTP 1.1|[HTTP 1.1](https://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> La seguridad de transporte está habilitada.|  
|Mensajería|SOAP 1.2|[Manual](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Marco de mensajería](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuntos (incluido el enlace HTTP)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|Mensajería|WS-Addressing 2005/08|[Direccionamiento de servicios Web 1,0-núcleo](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Direccionamiento de servicios Web 1,0-SOAP](https://go.microsoft.com/fwlink/?LinkId=95330)|  
|Metadatos|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> WCF implementa WS-MetadataExchange para recuperar el esquema XML, WSDL y WS-Policy.|  
  
## <a name="see-also"></a>Vea también

- [Enlaces proporcionados por el sistema](../../../../docs/framework/wcf/system-provided-bindings.md)
- [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)
- [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
- [\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)
- [\<mexHttpsBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)
- [\<mexHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)

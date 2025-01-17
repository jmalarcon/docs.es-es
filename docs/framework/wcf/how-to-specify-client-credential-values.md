---
title: 'Cómo: Especificar los valores de credenciales de cliente'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
ms.openlocfilehash: 2417c2dd16224d6cbf00d3f1f4a8958420830b6c
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319861"
---
# <a name="how-to-specify-client-credential-values"></a>Cómo: Especificar los valores de credenciales de cliente

Con Windows Communication Foundation (WCF), el servicio puede especificar cómo se autentica un cliente en el servicio. Por ejemplo, un servicio puede estipular que el cliente se autentique mediante un certificado.

## <a name="to-determine-the-client-credential-type"></a>Para determinar el tipo de credencial de cliente

1. Recupere los metadatos del punto de conexión de metadatos del servicio. Normalmente, los metadatos constan de dos archivos: el código de cliente en el lenguaje de programación elegido (el predeterminado es Visual C#), y un archivo de configuración XML. Una manera de recuperar los metadatos consiste en usar la herramienta Svcutil.exe para devolver el código y la configuración de cliente. Para obtener más información, vea [recuperar metadatos](./feature-details/retrieving-metadata.md) y la [herramienta de utilidad de metadatos de ServiceModel (SvcUtil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).

2. Abra el archivo de configuración XML. Si usa la herramienta Svcutil.exe, el nombre predeterminado del archivo es Output.config.

3. Busque el elemento **\<la >** con el atributo **mode** (**\<security mode =**`MessageOrTransport`**>** donde `MessageOrTransport` está establecido en uno de los modos de seguridad.

4. Busque el elemento secundario que coincida con el valor del modo. Por ejemplo, si el modo está establecido en **Message**, busque el elemento **\<message >** incluido en el elemento de **> \<security** .

5. Tenga en cuenta el valor asignado al atributo **clientCredentialType** . El valor real dependerá del modo que se use, de transporte o de mensaje.

El código XML siguiente muestra la configuración de un cliente usando la seguridad de mensajes y solicitando un certificado para autenticar al cliente.

```xml
<security mode="Message">
    <transport clientCredentialType="Windows" proxyCredentialType="None"
        realm="" />
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"
    algorithmSuite="Default" establishSecurityContext="true" />
</security>
```

## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a>Ejemplo: modo de transporte TCP con certificado como credencial de cliente

Este ejemplo establece el modo de seguridad en transporte y establece el valor de credencial de cliente en un certificado X.509. Los procedimientos siguientes muestran cómo establecer el valor de credencial de cliente en el cliente en código y configuración. Se supone que ha usado la [herramienta de utilidad de metadatos de ServiceModel (SvcUtil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) para devolver los metadatos (código y configuración) del servicio. Para obtener más información, consulte [Cómo: crear un cliente](how-to-create-a-wcf-client.md).

### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a>Para especificar el valor de credencial de cliente en el cliente en código

1. Use la [herramienta de utilidad de metadatos de ServiceModel (SvcUtil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) para generar código y configuración desde el servicio.

2. Cree una instancia del cliente WCF mediante el código generado.

3. En la clase de cliente, establezca la propiedad <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> de la clase <xref:System.ServiceModel.ClientBase%601> en un valor adecuado. Este ejemplo establece la propiedad en un certificado X.509 utilizando el método <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> de la clase <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>.

     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]

     Puede utilizar cualquiera de las enumeraciones de la clase <xref:System.Security.Cryptography.X509Certificates.X509FindType>. El nombre de sujeto se utiliza aquí en caso de que se cambie el certificado (debido a una fecha de caducidad). Utilizar el nombre de sujeto permite a la infraestructura encontrar de nuevo el certificado.

### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a>Para especificar el valor de credencial de cliente en el cliente en configuración

1. Agregue un elemento [de > \<behavior](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) al elemento de [> \<behaviors](../configure-apps/file-schema/wcf/behaviors.md) .

2. Agregue un elemento [de > \<clientCredentials](../configure-apps/file-schema/wcf/clientcredentials.md) al elemento de [> \<behaviors](../configure-apps/file-schema/wcf/behaviors.md) . Asegúrese de establecer el atributo `name` necesario en un valor adecuado.

3. Agregue un elemento [de > \<clientCertificate](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) al elemento de [> \<clientCredentials](../configure-apps/file-schema/wcf/clientcredentials.md) .

4. Establezca los atributos siguientes en los valores adecuados: `storeLocation`, `storeName`, `x509FindType` y `findValue`, como se muestra en el código siguiente. Para más información, consulte [Trabajar con certificados](./feature-details/working-with-certificates.md).

    ```xml
    <behaviors>
       <endpointBehaviors>
          <behavior name="endpointCredentialBehavior">
            <clientCredentials>
              <clientCertificate findValue="Contoso.com"
                                 storeLocation="LocalMachine"
                                 storeName="TrustedPeople"
                                 x509FindType="FindBySubjectName" />
            </clientCredentials>
          </behavior>
       </endpointBehaviors>
    </behaviors>
    ```

5. Al configurar el cliente, especifique el comportamiento estableciendo el atributo `behaviorConfiguration` del elemento `<endpoint>`, como se muestra en el código siguiente. El elemento de punto de conexión es un elemento secundario del elemento de [> \<client](../configure-apps/file-schema/wcf/client.md) . Especifique también el nombre de la configuración de enlace estableciendo el atributo `bindingConfiguration` en el enlace para el cliente. Si está utilizando un archivo de configuración generado, se genera automáticamente el nombre del enlace. En este ejemplo, el nombre es `"tcpBindingWithCredential"`.

    ```xml
    <client>
      <endpoint name =""
                address="net.tcp://contoso.com:8036/aloha"
                binding="netTcpBinding"
                bindingConfiguration="tcpBindingWithCredential"
                behaviorConfiguration="endpointCredentialBehavior" />
    </client>
    ```

## <a name="see-also"></a>Vea también

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [Programación de la seguridad de WCF](./feature-details/programming-wcf-security.md)
- [Selección de tipos de credenciales](./feature-details/selecting-a-credential-type.md)
- [Herramienta de utilidad de metadatos de ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Trabajo con certificados](./feature-details/working-with-certificates.md)
- [Cómo crear un cliente](how-to-create-a-wcf-client.md)
- [\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md)
- [\<La >](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
- [@no__t 1message >](../configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)
- [@no__t 1behavior >](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)
- [@no__t 1behaviors >](../configure-apps/file-schema/wcf/behaviors.md)
- [@no__t 1clientCertificate >](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)
- [@no__t 1clientCredentials >](../configure-apps/file-schema/wcf/clientcredentials.md)

---
title: Servicio AJAX mediante el uso de ejemplo de tipos complejos
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: dce3e89449a036de7c4936963cfa0b36f3f08451
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045814"
---
# <a name="ajax-service-using-complex-types-sample"></a>Servicio AJAX mediante el uso de ejemplo de tipos complejos

En este ejemplo se muestra cómo usar Windows Communication Foundation (WCF) para crear un servicio JavaScript asincrónico y XML (AJAX) ASP.NET que crea instancias de tipos complejos y los envía entre el servicio y el cliente como notación de objetos JavaScript (JSON). Puede tener acceso a un servicio de AJAX utilizando el código JavaScript de un cliente del explorador web. Este ejemplo se basa en el ejemplo de [servicio Ajax básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md) .

La compatibilidad de Ajax en WCF está optimizada para su uso con <xref:System.Web.UI.ScriptManager> ASP.NET AJAX a través del control. Para obtener un ejemplo del uso de WCF con ASP.NET AJAX, consulte los [ejemplos de Ajax](ajax.md).

> [!NOTE]
> El procedimiento de instalación y las instrucciones de compilación de este ejemplo se encuentran al final de este tema.

El servicio en el ejemplo siguiente es un servicio WCF sin código específico de AJAX. Dado que no se aplica el atributo <xref:System.ServiceModel.Web.WebGetAttribute>, se utiliza el verbo HTTP predeterminado ("POST"). El servicio tiene una operación, `DoMath`, que devuelve un tipo complejo denominado `MathResult`. El tipo complejo es un tipo de contrato de datos estándar, que tampoco contiene ningún código específico de AJAX.

```csharp
[DataContract]
public class MathResult
{
    [DataMember]
    public double sum;
    [DataMember]
    public double difference;
    [DataMember]
    public double product;
    [DataMember]
    public double quotient;
}
```

Cree un extremo AJAX en el servicio mediante el uso de la clase <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, exactamente igual que en el ejemplo de servicio AJAX básico.

La página web del cliente ComplexTypeClientPage. aspx contiene el código ASP.NET y JavaScript para invocar el servicio cuando el usuario hace clic en el botón **realizar cálculo** de la página. El código para invocar el servicio construye un cuerpo JSON y lo envía mediante HTTP POST, similar al [servicio Ajax mediante el ejemplo http post](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) .

Después de que la llamada del servicio tenga éxito, puede tener acceso a los miembros de datos individuales (`sum`, `difference`, `product` y `quotient`) en el objeto JavaScript resultante.

```javascript
function onSuccess(mathResult){
     document.getElementById("sum").value = mathResult.sum;
     document.getElementById("difference").value = mathResult.difference;
     document.getElementById("product").value = mathResult.product;
     document.getElementById("quotient").value = mathResult.quotient;
}
```

### <a name="to-set-up-build-and-run-the-sample"></a>Configurar, compilar y ejecutar el ejemplo

1. Asegúrese de que ha realizado el [procedimiento de instalación única para los ejemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Compile la solución ComplexTypeAjaxService. sln tal y como se describe en [Building the Windows Communication Foundation samples](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Vaya a `http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx` (no abra ComplexTypeClientPage. aspx en el explorador desde el directorio del proyecto).

> [!IMPORTANT]
> Puede que los ejemplos ya estén instalados en su equipo. Compruebe el siguiente directorio (predeterminado) antes de continuar.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si este directorio no existe, vaya a [ejemplos de Windows Communication Foundation (WCF) y Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para descargar todos los Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] y ejemplos. Este ejemplo se encuentra en el siguiente directorio.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`

## <a name="see-also"></a>Vea también

- [Servicio AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md)

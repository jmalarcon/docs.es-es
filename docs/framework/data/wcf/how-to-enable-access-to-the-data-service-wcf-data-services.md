---
title: Procedimiento Habilitación del acceso al servicio de datos (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
ms.openlocfilehash: cbe25dcb62adf82921b24623cc4930c3076dd1fa
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790664"
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a>Procedimiento Habilitación del acceso al servicio de datos (WCF Data Services)
En [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], debe permitir explícitamente el acceso a los recursos expuestos por un servicio de datos. Esto significa que después de crear un nuevo servicio de datos, debe proporcionar explícitamente acceso a los recursos individuales como conjuntos de entidades. En este tema se muestra cómo habilitar el acceso de lectura y escritura a cinco de los conjuntos de entidades del servicio de datos de Northwind que se crea al completar la guía de [Inicio rápido](quickstart-wcf-data-services.md). Dado que la enumeración <xref:System.Data.Services.EntitySetRights> se define utilizando <xref:System.FlagsAttribute>, puede utilizar un operador OR lógico para especificar varios permisos para un único conjunto de entidades.  
  
> [!NOTE]
> Cualquier cliente que pueda tener acceso a la aplicación ASP.NET también puede tener acceso a los recursos expuestos por el servicio de datos. En un servicio de datos de producción, para evitar el acceso no autorizado a los recursos, también debería proteger la aplicación. Para obtener más información, consulte [protección de sitios web de ASP.net](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100)).  
  
### <a name="to-enable-access-to-the-data-service"></a>Para habilitar el acceso al servicio de datos  
  
- En el código del servicio de datos, reemplace el código de marcador de posición de la función `InitializeService` por el siguiente:  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]  
  
     De esta forma, los clientes pueden tener acceso de lectura y escritura a los conjuntos de entidades de `Orders` y `Order_Details`, y acceso de solo lectura a los conjuntos de entidades de `Customers`.  
  
## <a name="see-also"></a>Vea también

- [Cómo: Desarrollo de un servicio de datos de WCF que se ejecuta en IIS](how-to-develop-a-wcf-data-service-running-on-iis.md)
- [Configuración del servicio de datos](configuring-the-data-service-wcf-data-services.md)

---
title: Procedimiento Ejecutar consultas asincrónicas del servicio de datos (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
ms.assetid: 902a2dc1-d0e9-4b00-90a8-becc4cb1f6a7
ms.openlocfilehash: 14bfc138c5ece45184fb939f19aaf3d7e73e7294
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790571"
---
# <a name="how-to-execute-asynchronous-data-service-queries-wcf-data-services"></a>Procedimiento Ejecutar consultas asincrónicas del servicio de datos (WCF Data Services)
Al usar la biblioteca de cliente de [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], puede realizar operaciones cliente-servidor, como ejecutar consultas y guardar cambios, de forma asincrónica. Para obtener más información, vea [operaciones asincrónicas](asynchronous-operations-wcf-data-services.md).  
  
> [!NOTE]
> En una aplicación donde se debe invocar la devolución de llamada en un subproceso concreto, debe calcular explícitamente las referencias de la ejecución del método <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>. Para obtener más información, vea [operaciones asincrónicas](asynchronous-operations-wcf-data-services.md).  
  
 En el ejemplo de este tema se usa el servicio de datos de ejemplo Northwind y las clases del servicio de datos de cliente generadas automáticamente. Este servicio y las clases de datos de cliente se crean al completar la guía de [Inicio rápido de WCF Data Services](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra cómo ejecutar una consulta asincrónica llamando al método <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> para iniciar la consulta. El delegado alineado llama al método <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> para mostrar los resultados de la consulta.  
  
 [!code-csharp[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#executequeryasync)]
 [!code-vb[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#executequeryasync)]  
  
## <a name="see-also"></a>Vea también

- [Biblioteca cliente de Servicios de datos de WCF](wcf-data-services-client-library.md)

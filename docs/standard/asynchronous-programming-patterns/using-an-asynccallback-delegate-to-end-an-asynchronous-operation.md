---
title: Utilizar un delegado AsyncCallback para finalizar una operación asincrónica
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ending asynchronous operations
- asynchronous programming, ending operations
- AsyncCallback delegate
- stopping asynchronous operations
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
ms.openlocfilehash: c3cac2db57a24bf6a0f5640e4ad8101686e6c3e9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130925"
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a>Utilizar un delegado AsyncCallback para finalizar una operación asincrónica
Las aplicaciones que pueden realizar otro trabajo mientras esperan los resultados de una operación asincrónica no deben bloquear la espera hasta que se complete la operación. Use una de las siguientes opciones para continuar con la ejecución de instrucciones mientras espera a que la operación asincrónica se complete:  
  
- Use un delegado <xref:System.AsyncCallback> para procesar los resultados de la operación asincrónica en un subproceso independiente. Este método se muestra en este tema.  
  
- Use la propiedad <xref:System.IAsyncResult.IsCompleted%2A> de la interfaz <xref:System.IAsyncResult> devuelta por el método **Begin**_OperationName_ de la operación asincrónica para determinar si la operación se ha completado. Para ver un ejemplo que muestre este enfoque, consulte [Sondear el estado de una operación asincrónica](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se explica cómo utilizar los métodos asincrónicos en la clase <xref:System.Net.Dns> para recuperar información del sistema de nombres de dominio (DNS) de equipos especificados por el usuario. En este ejemplo se crea un delegado <xref:System.AsyncCallback> que hace referencia al método `ProcessDnsInformation`. Se llama a este método una vez por cada solicitud asincrónica de información de DNS.  
  
 Tenga en cuenta que el host especificado por el usuario se pasa al parámetro <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object>. Para obtener un ejemplo que muestra cómo definir y usar un objeto state más complejo, vea [Utilizar un delegado AsyncCallback y un objeto State](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a>Vea también

- [Modelo asincrónico basado en eventos (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Información general sobre el modelo asincrónico basado en eventos](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Llamar a métodos asincrónicos mediante IAsyncResult](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)
- [Utilizar un delegado AsyncCallback y un objeto State](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)

---
title: Procedimiento para implementar un proveedor
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- observer design pattern [.NET Framework], implementing providers
- providers [.NET Framework], in observer design pattern
- observables [.NET Framework], in observer design pattern
ms.assetid: 790b5d8b-d546-40a6-beeb-151b574e5ee5
ms.openlocfilehash: f5bb3cda0caa39ba3fd094b80e0b769a4bfc1f85
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141556"
---
# <a name="how-to-implement-a-provider"></a>Procedimiento para implementar un proveedor
El modelo de diseño de observador requiere una división entre un proveedor, que controla los datos y envía notificaciones, y uno o varios observadores, que reciben notificaciones (devoluciones de llamada) del proveedor. En este tema se describe cómo crear un proveedor. En un tema relacionado, [Cómo: Implementar un observador](../../../docs/standard/events/how-to-implement-an-observer.md), se describe cómo crear un observador.  
  
### <a name="to-create-a-provider"></a>Para crear un proveedor  
  
1. Defina los datos de los que el proveedor es responsable de enviar a los observadores. Aunque el proveedor y los datos que envía a los observadores pueden ser de un solo tipo, suelen representarse con tipos distintos. Por ejemplo, en una aplicación de supervisión de temperatura, la estructura `Temperature` define los datos que el proveedor (representado por la clase `TemperatureMonitor` definida en el paso siguiente) controla y al que se suscriben los observadores.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2. Defina el proveedor de datos, que es un tipo que implementa la interfaz <xref:System.IObservable%601?displayProperty=nameWithType>. El argumento de tipo genérico es el tipo que el proveedor envía a los observadores. En el ejemplo siguiente se define una clase `TemperatureMonitor`, que es una implementación <xref:System.IObservable%601?displayProperty=nameWithType> construida con un argumento de tipo genérico de `Temperature`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3. Determine cómo el proveedor almacenará las referencias a los observadores, para que cada observador reciba una notificación cuando sea oportuno. Lo más común es que, para este propósito, se use un objeto de colección como un objeto <xref:System.Collections.Generic.List%601> genérico. En el ejemplo siguiente se define un objeto <xref:System.Collections.Generic.List%601> privado del que se crea una instancia en el constructor de clases `TemperatureMonitor`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4. Defina una implementación <xref:System.IDisposable> que el proveedor pueda devolver a los suscriptores, para que puedan dejar de recibir notificaciones en cualquier momento. En el ejemplo siguiente se define una clase `Unsubscriber` anidada de la que se pasa una referencia a la colección de suscriptores y al suscriptor cuando se crea la instancia de la clase. Este código permite que el suscriptor llame a la implementación <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> del objeto para quitarse de la colección de suscriptores.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5. Implemente el método <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType>. Al método se le pasa una referencia a la interfaz <xref:System.IObserver%601?displayProperty=nameWithType> y se debe almacenar en el objeto designado para dicho propósito en el paso 3. El método, a continuación, debe devolver la implementación <xref:System.IDisposable> desarrollada en el paso 4. El siguiente ejemplo muestra la implementación del método <xref:System.IObservable%601.Subscribe%2A> de la clase `TemperatureMonitor`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6. Notifique a los observadores según proceda con una llamada a sus implementaciones <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType> y <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>. En algunos casos, un proveedor no puede llamar al método <xref:System.IObserver%601.OnError%2A> cuando se produce un error. Por ejemplo, el método `GetTemperature` siguiente simula un monitor que lee los datos de temperatura cada cinco segundos y notifica a los observadores si la temperatura ha cambiado por al menos 1 grado desde la lectura anterior. Si el dispositivo no informa de una temperatura (es decir, si su valor es null), el proveedor notifica a los observadores que la transmisión está completa. Tenga en cuenta que, además de llamar al método <xref:System.IObserver%601.OnCompleted%2A> de cada observador, el método `GetTemperature` borra la colección <xref:System.Collections.Generic.List%601>. En este caso, el proveedor no realiza ninguna llamada al método <xref:System.IObserver%601.OnError%2A> de sus observadores.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo contiene el código fuente completo para definir una implementación <xref:System.IObservable%601> para una aplicación de supervisión de temperatura. Incluye la estructura `Temperature`, que son los datos enviados a los observadores, y la clase `TemperatureMonitor`, que es la implementación <xref:System.IObservable%601>.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## <a name="see-also"></a>Vea también

- <xref:System.IObservable%601>
- [Modelo de diseño de observador](../../../docs/standard/events/observer-design-pattern.md)
- [Cómo: Implementar un observador](../../../docs/standard/events/how-to-implement-an-observer.md)
- [Procedimientos recomendados para modelos de diseño de observador](../../../docs/standard/events/observer-design-pattern-best-practices.md)

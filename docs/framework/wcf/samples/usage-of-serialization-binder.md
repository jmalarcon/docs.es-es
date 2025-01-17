---
title: Uso del enlazador de serialización
ms.date: 03/30/2017
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
ms.openlocfilehash: 10900950b935b484053fe8e37263f0dfc25eba99
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348456"
---
# <a name="usage-of-serialization-binder"></a>Uso del enlazador de serialización
Este ejemplo muestra cómo utilizar <xref:System.Runtime.Serialization.SerializationBinder> para cambiar la versión de un tipo genérico cuando se serializa.  
  
## <a name="demonstrates"></a>Demostraciones  
 <xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
  
## <a name="discussion"></a>Discusión  
 Este ejemplo muestra cómo dos entidades que son destinatarios diferentes versiones de puede .NET Framework comunicarse utilizando el formateador binario y el enlazador de serialización.  
  
En este ejemplo se desarrolló con .NET Remoting. Consta de un servidor para [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], que implementa un contrato con tipos genéricos y dos clientes diferentes, destino .NET Framework 2.0 y otro para [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].  
  
 El servidor asocia un objeto <xref:System.Runtime.Serialization.SerializationBinder> al formateador binario para poder cambiar la versión de los tipos de acuerdo con la serialización, de modo que ambos clientes puedan deserializar esos tipos correctamente.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar y ejecutar el ejemplo  
  
1. Para ejecutar el cliente, haga clic en la solución, SBGenericsVTS (6 proyectos) y, a continuación, seleccione **propiedades**.  
  
2. En **propiedades comunes**, seleccione **proyecto de inicio**, a continuación, seleccione **varios proyectos de inicio**.  
  
3. Seleccione **Server** primero, a continuación **Client20** y, a continuación, **Client40**. Seleccione el **iniciar** acción para estos tres proyectos y deje el resto establecido en **ninguno**.  
  
4. Haga clic en **Aceptar** y, a continuación, presione F5 para ejecutar el ejemplo.

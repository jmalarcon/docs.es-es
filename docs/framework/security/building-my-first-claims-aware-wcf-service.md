---
title: Compilación del primer servicio WCF para notificaciones
ms.date: 03/30/2017
ms.assetid: e0e6d091-9a97-4888-8f2c-cbcee42d90ee
author: BrucePerlerMS
ms.openlocfilehash: 330d785721cb434f74ec746310a71bfd39fefd0b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045548"
---
# <a name="building-my-first-claims-aware-wcf-service"></a>Compilación del primer servicio WCF para notificaciones
## <a name="applies-to"></a>Se aplica a  
  
- Windows Identity Foundation (WIF)  
  
- Windows Communication Foundation (WCF)  
  
## <a name="overview"></a>Información general  
 En este tema se describe el escenario para compilar servicios WCF para notificaciones mediante WIF. En un escenario de servicio Web para notificaciones suele haber tres participantes: el propio servicio Web, el usuario final y el servicio de token de seguridad (STS). En la ilustración siguiente se describe este escenario:  
  
 ![Diagrama que muestra los componentes de servicio WCF con reconocimiento de notificaciones básicos de WIF.](./media/building-my-first-claims-aware-wcf-service/windows-identify-foundation-basic-claims-aware-windows-communication-foundation-service.gif)  
  
1. El cliente de servicio WCF (a veces denominado agente) usa WIF para enviar credenciales al STS que a su vez, y tras llevarse la autenticación a cabo correctamente, emite un token para el agente.  
  
2. El agente envía este token emitido por el STS al servicio WCF.  
  
3. El servicio WCF para notificaciones se configura de forma que confíe en el STS y en los token que emite. Asimismo, usa WIF para validar el token y analizarlo. Los desarrolladores usan la API y los tipos de WIF adecuados, por ejemplo, **ClaimsPrincipal**, para las necesidades de la aplicación, como la implementación de autorización correspondiente.  
  
 A partir de .NET 4.5, WIF forma parte del paquete de .NET Framework. Poder disponer de las clases de WIF directamente en el marco de trabajo permite una integración mucho más profunda de la identidad basada en notificaciones en .NET, lo que facilita el uso de notificaciones. Con WIF 4.5, no es necesario instalar ningún componente fuera de banda para comenzar a desarrollar aplicaciones web compatibles con notificaciones. Las clases de WIF se extienden ahora por diversos ensamblados; los principales son System.Security.Claims, System.IdentityModel y System.IdentityModel.Services.  
  
 El STS es un servicio que emite tokens tras haberse realizado la autenticación correctamente. Microsoft ofrece dos STS estándar del sector:  
  
- [Servicios de federación de Active Directory (AD FS) (AD FS) 2,0](https://go.microsoft.com/fwlink/?LinkID=247516)
  
- [Access Control Service de Windows Azure (ACS)](https://docs.microsoft.com/previous-versions/azure/azure-services/hh147631(v=azure.100))
  
 AD FS 2.0 forma parte de Windows Server R2 y se puede usar como STS para escenarios locales. El control de acceso de Active Directory de Azure (también conocido como Servicio de control de acceso o ACS) es un servicio en la nube que se ofrece como parte de Microsoft Azure. Con fines de pruebas o educativos, también pueden usarse otros STS para compilar las aplicaciones compatibles con notificaciones. Por ejemplo, puede usar el STS de desarrollo local que forma parte de la [herramienta de identidad y acceso para Visual Studio](https://go.microsoft.com/fwlink/?LinkID=245849) , que está disponible en línea de forma gratuita.  
  
 Para compilar el primer servicio WCF compatible con notificaciones mediante [WIF, consulte Cómo: Habilite WIF para una aplicación](how-to-enable-wif-for-a-wcf-web-service-application.md)de servicio Web WCF.
  
## <a name="see-also"></a>Vea también

- [Introducción a WIF](getting-started-with-wif.md)

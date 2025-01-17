---
title: Identity and Access Tool para Visual Studio 2012
ms.date: 03/30/2017
ms.assetid: 87b8f8f2-4074-44fd-9fd6-08278e877390
author: BrucePerlerMS
ms.openlocfilehash: d58cca13dc3ac67742e5371aed628a6a680e61e1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045426"
---
# <a name="identity-and-access-tool-for-visual-studio-2012"></a>Identity and Access Tool para Visual Studio 2012
En este tema se describe la nueva Identity and Access Tool para Visual Studio 11. Puede descargar esta herramienta desde la siguiente dirección URL: <https://go.microsoft.com/fwlink/?LinkID=245849> o directamente desde Visual Studio 11, buscando "Identity" directamente en el administrador de extensiones.  
  
 Identity and Access Tool para Visual Studio 11 ofrece una experiencia en tiempo de desarrollo considerablemente simplificada en la que destacan los siguientes aspectos:  
  
- Al usar la nueva herramienta, se puede desarrollar mediante tipos de proyecto de aplicaciones web y tener IIS Express como destino.  
  
- A diferencia de la autenticación abierta de solo protección, con la nueva herramienta se puede especificar el controlador o la página de detección de dominios de inicio locales (o cualquier otro punto de conexión que controle la experiencia de autenticación en la aplicación) y WIF configurará todas las solicitudes no autenticadas para dirigirse a estos, en lugar de redirigirlas al STS.  
  
- La herramienta incluye un servicio de token de seguridad (STS) de prueba que se ejecuta en el equipo local al iniciar una sesión de depuración. Por consiguiente, ya no es necesario crear proyectos de STS personalizados ni ajustarlos para obtener las notificaciones requeridas para probar las aplicaciones. Los tipos y valores de notificación son totalmente personalizables.  
  
- La configuración general puede modificarse directamente a través de la interfaz de usuario de la herramienta, sin necesidad de editar el archivo web.config.  
  
- Se puede establecer la federación con los Servicios de federación de Active Directory (AD FS) 2.0 (u otros proveedores de WS-Federation) en una única pantalla.  
  
- La herramienta aprovecha las capacidades de Windows Azure Access Control Service (ACS) con una sencilla lista de casillas para todos los proveedores de identidad que desea usar: Facebook, Google, Live ID, Yahoo!, cualquier proveedor de OpenID y cualquier proveedor de WS-Federation. Seleccione los proveedores de identidad, haga clic en Aceptar y, a continuación, presione F5. Tanto la aplicación como ACS se configurarán automáticamente y la aplicación de prueba será compatible con ACS.  
  
## <a name="see-also"></a>Vea también

- [Características de WIF](wif-features.md)

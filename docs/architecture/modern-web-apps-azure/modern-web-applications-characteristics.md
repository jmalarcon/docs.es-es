---
title: Características de las aplicaciones web modernas
description: Diseño de aplicaciones web modernas con ASP.NET Core y Azure | Características de las aplicaciones web modernas
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: d3848f3b0cf993930bfc3801ce40c5eac30f094d
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374089"
---
# <a name="characteristics-of-modern-web-applications"></a>Características de las aplicaciones web modernas

> "… con el diseño adecuado, las características son más baratas. Este enfoque es complicado, pero sigue siendo útil".  
> _\- Dennis Ritchie_

Las aplicaciones web modernas tienen expectativas más altas por parte del usuario y mayores demandas que nunca. Se espera que las aplicaciones web actuales estén disponibles 24 horas al día los siete días de la semana desde cualquier lugar del mundo y se puedan usar desde prácticamente cualquier dispositivo o tamaño de pantalla. Las aplicaciones web deben ser seguras, flexibles y escalables para satisfacer los picos de demanda. Cada vez más, los escenarios complejos deben controlarse mediante experiencias de usuario enriquecidas creadas en el cliente con JavaScript y comunicarse de forma eficaz a través de las API web.

ASP.NET Core se ha optimizado para aplicaciones web modernas y escenarios de hospedaje basados en la nube. Su diseño modular permite que las aplicaciones dependan solo de aquellas características que realmente usan, lo que mejora la seguridad y el rendimiento de la aplicación mientras se reducen los requisitos de recursos de hospedaje.

## <a name="reference-application-eshoponweb"></a>Aplicación de referencia: eShopOnWeb

En esta guía se incluye una aplicación de referencia, _eShopOnWeb_, en la que se muestran algunos de los principios y las recomendaciones. La aplicación es una sencilla tienda en línea que admite búsquedas a través de un catálogo de camisetas, tazas de café y otros productos de marketing. La aplicación de referencia es deliberadamente sencilla para que sea fácil de entender.

![eShopOnWeb](./media/image2-1.png)

**Figura 2-1.** eShopOnWeb

> ### <a name="reference-application"></a>Aplicación de referencia
>
> - **eShopOnWeb**  
>   <https://github.com/dotnet/eShopOnWeb>

## <a name="cloud-hosted-and-scalable"></a>Hospedada en la nube y escalable

ASP.NET Core se ha optimizado para la nube (pública, privada, cualquier nube) debido a su memoria baja y rendimiento alto. La superficie más pequeña de las aplicaciones ASP.NET Core significa que se pueden hospedar más en el mismo hardware, y se paga por menos recursos cuando se usan servicios de hospedaje en la nube de pago por uso. El rendimiento mayor significa que se puede servir a más clientes desde una aplicación dado el mismo hardware, reduciendo así la necesidad de invertir en infraestructura y servidores de hospedaje.

## <a name="cross-platform"></a>Multiplataforma

ASP.NET Core es multiplataforma y se puede ejecutar en Linux, macOS y Windows. Esto abre muchas opciones nuevas para el desarrollo y la implementación de aplicaciones compiladas con ASP.NET Core. Los contenedores de Docker, tanto en Linux como en Windows, pueden hospedar aplicaciones ASP.NET Core, lo que les permite aprovechar las ventajas que ofrecen los [contenedores y microservicios](../microservices/index.md).

## <a name="modular-and-loosely-coupled"></a>Modular y de acoplamiento flexible

Los paquetes NuGet son objetos de primera clase en .NET Core y las aplicaciones ASP.NET Core se componen de muchas bibliotecas de NuGet. Esta granularidad de la funcionalidad ayuda a garantizar que las aplicaciones solo dependen e implementan la funcionalidad que realmente necesitan, lo que reduce su superficie y el área expuesta a vulnerabilidades de seguridad.

ASP.NET Core también es totalmente compatible con la [inserción de dependencias](https://deviq.com/dependency-injection/), tanto de forma interna como en la aplicación. Las interfaces pueden tener varias implementaciones que se pueden intercambiar según sea necesario. La inserción de dependencias permite acoplar aplicaciones de forma flexible a esas interfaces en lugar de a implementaciones específicas, lo que facilita la ampliación, el mantenimiento y las pruebas correspondientes.

## <a name="easily-tested-with-automated-tests"></a>Pruebas sencillas con pruebas automatizadas

Las aplicaciones ASP.NET Core admiten las pruebas unitarias y, gracias a su acoplamiento flexible y su compatibilidad con la inserción de dependencias, se facilita el intercambio de intereses de infraestructura con implementaciones falsas para fines de prueba. ASP.NET Core también incluye un TestServer que se puede usar para hospedar aplicaciones en memoria. Después, las pruebas funcionales pueden realizar solicitudes a este servidor en memoria, ejecutar la pila de aplicación completa (incluido el software intermedio, el enrutamiento, el enlace de modelos, los filtros, etc.) y recibir una respuesta en una fracción del tiempo que sería necesario para hospedar la aplicación en un servidor real y realizar solicitudes a través de la capa de red. Estas pruebas son especialmente fáciles de escribir y útiles para las API, que cada vez son más importantes en las aplicaciones web modernas.

## <a name="traditional-and-spa-behaviors-supported"></a>Comportamientos tradicionales y de SPA admitidos

Las aplicaciones web tradicionales apenas contaban con comportamiento del lado cliente, y en su lugar se basaban en el servidor para todas las operaciones de navegación, consultas y actualizaciones que la aplicación tuviera que realizar. Cada operación nueva realizada por el usuario se convertiría en una nueva solicitud web, con el resultado de una recarga de página completa en el explorador del usuario final. Los marcos de controlador de vista de modelos (MVC) clásicos normalmente siguen este enfoque, en el que cada solicitud nueva se corresponde a otra acción de controlador, lo que a su vez podría funcionar con un modelo y devolver una vista. Es posible que algunas operaciones individuales en una página determinada se mejoraran con funcionalidad de AJAX (JavaScript asincrónico y XML), pero la arquitectura global de la aplicación usaba muchas vistas MVC distintas y extremos de URL. Además, ASP.NET Core MVC también admite Razor Pages, una forma más sencilla de organizar las páginas de tipo MVC.

Las aplicaciones de página única (SPA), por el contrario, implican muy pocas cargas de página generadas de forma dinámica en el lado de servidor (si existen). Muchas SPA se inicializan en un archivo HTML estático que carga las bibliotecas de JavaScript necesarias para iniciar y ejecutar la aplicación. Estas aplicaciones hacen un uso intensivo de las API web para sus necesidades de datos y pueden proporcionar experiencias de usuario mucho más enriquecidas.

Muchas aplicaciones web implican una combinación del comportamiento de aplicación web tradicional (normalmente para el contenido) y SPA (para la interactividad). ASP.NET Core admite MVC (basado en vistas o páginas) y las API web en la misma aplicación y usa el mismo conjunto de herramientas y bibliotecas de marco subyacentes.

## <a name="simple-development-and-deployment"></a>Implementación y desarrollo simples

Las aplicaciones ASP.NET Core se pueden escribir mediante interfaces de línea de comandos y editores de texto simples, o bien con entornos de desarrollo completos como Visual Studio. Las aplicaciones monolíticas normalmente se implementan en un solo punto de conexión. Las implementaciones se pueden automatizar con facilidad para que tengan lugar como parte de una canalización de integración continua (CI) y entrega continua (CD). Además de las herramientas de CI/CD tradicionales, Windows Azure tiene compatibilidad integrada para repositorios de Git y puede implementar automáticamente las actualizaciones que se realicen en una rama o etiqueta de Git especificada.

## <a name="traditional-aspnet-and-web-forms"></a>ASP.NET tradicional y formularios Web Forms

Además de ASP.NET Core, ASP.NET 4.x tradicional sigue siendo una plataforma sólida y confiable para compilar aplicaciones web. ASP.NET es compatible con los modelos de desarrollo de MVC y API web, así como los formularios Web Forms, que resultan muy adecuados para el desarrollo de aplicaciones basadas en páginas y ofrecen un ecosistema enriquecido de componentes de terceros. Desde hace tiempo, Windows Azure ofrece una gran compatibilidad con las aplicaciones ASP.NET 4.x y muchos desarrolladores están familiarizados con esta plataforma.

> ### <a name="references--modern-web-applications"></a>Referencias: aplicaciones web modernas
>
> - **Introducción a ASP.NET Core**  
>   <https://docs.microsoft.com/aspnet/core/>
> - **Six Key Benefits of ASP.NET Core which make it Different and Better** (Seis ventajas clave de ASP.NET Core que lo hacen diferente y mejor)  
>   <https://blog.trigent.com/six-key-benefits-of-asp-net-core-1-0-which-make-it-different-better/>
> - **Pruebas y depuración en ASP.NET Core**  
>   <https://docs.microsoft.com/aspnet/core/testing/>

>[!div class="step-by-step"]
>[Anterior](index.md)
>[Siguiente](choose-between-traditional-web-and-single-page-apps.md)

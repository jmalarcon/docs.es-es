---
title: Aplicaciones SOA
description: Tenga en cuenta que los contenedores también pueden ser una opción de implementación útil para las aplicaciones SOA.
ms.date: 02/15/2019
ms.openlocfilehash: aa56ada7b14a465fb3dafd02b03b815782ac765b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2019
ms.locfileid: "68672362"
---
# <a name="service-oriented-applications"></a>Aplicaciones orientadas a servicios

Arquitectura orientada a servicios (SOA) era un término muy utilizado que significaba muchas cosas diferentes para diferentes personas. Pero, como denominador común, SOA significa que la arquitectura de una aplicación se estructura descomponiéndola en varios servicios (normalmente como servicios HTTP) que se pueden clasificar en tipos diferentes como subsistemas o, en otros casos, como niveles.

Esos servicios se pueden implementar ahora como contenedores de Docker, con lo que se resuelven los problemas de implementación, puesto que todas las dependencias se incluyen en la imagen de contenedor. De todos modos, cuando necesite escalar arquitecturas orientadas a servicios, puede que se encuentre con problemas si realiza una implementación en función de instancias únicas. Este problema puede controlarse con software de agrupación en clústeres de Docker o un orquestador. Examinaremos los orquestadores con más detalle en la sección siguiente, cuando exploraremos los enfoques de microservicios.

Los contenedores de Docker son útiles (pero no obligatorios) para las arquitecturas orientadas a servicios tradicionales y las arquitecturas de microservicios más avanzadas.

En definitiva, las soluciones de agrupación en clústeres de contenedores resultan útiles tanto para una arquitectura tradicional de SOA como para una arquitectura de microservicios más avanzada en la que cada microservicio posee su modelo de datos. Y, gracias a varias bases de datos, también se puede escalar horizontalmente el nivel de datos en lugar de trabajar con bases de datos monolíticas compartidas por los servicios SOA. No obstante, la discusión sobre la división de los datos se centra exclusivamente en la arquitectura y el diseño.

>[!div class="step-by-step"]
>[Anterior](state-and-data-in-docker-applications.md)
>[Siguiente](orchestrate-high-scalability-availability.md)

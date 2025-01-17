---
title: 'Protocolos WS-*: gRPC para desarrolladores de WCF'
description: Revisión de los protocolos WS-* admitidos por WCF y alternativas disponibles con gRPC
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 4e7b80df182fb69cc51e14738e59ad87efaf5dd2
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2019
ms.locfileid: "73841316"
---
# <a name="ws--protocols"></a>Protocolos WS-\*

Una de las ventajas reales de trabajar con Windows Communication Foundation (WCF) era que admitía muchos de los protocolos estándar _de WS-\*_ existentes. En esta sección se explica brevemente cómo gRPC administra los mismos protocolos de WS-\* y se describen las opciones que están disponibles cuando no hay ninguna alternativa.

## <a name="metadata-exchange---ws-policy-ws-discovery-and-so-on"></a>Intercambio de metadatos: WS-Policy, WS-Discovery, etc.

Los servicios SOAP exponen documentos de esquema del lenguaje de descripción de servicios web (WSDL) con información como formatos de datos, operaciones o opciones de comunicación. Este esquema se puede utilizar para generar el código de cliente.

gRPC funciona mejor cuando los servidores y los clientes se generan a partir de los mismos `.proto` archivos, pero una extensión opcional de reflexión de servidor proporciona una manera de exponer información dinámica de un servidor en ejecución. Para obtener más información, consulte el paquete NuGet [GRPC. Reflection](https://nuget.org/packages/Grpc.Reflection) y el artículo sobre la [reflexión de C# GRPC Server](https://github.com/grpc/grpc/blob/master/doc/csharp/server_reflection.md) .

El protocolo WS-Discovery se usa para buscar servicios en una red local. los servicios de gRPC suelen encontrarse con DNS o un registro de servicio como Consul o ZooKeeper.

## <a name="security--ws-security-ws-federation-xml-encryption-and-so-on"></a>Seguridad: WS-Security, WS-Federation, cifrado XML, etc.

La seguridad, la autenticación y la autorización se describen con mucha más detalle en el [capítulo 6](security.md). Pero merece la pena mencionar que, a diferencia de WCF, gRPC no es compatible con WS-Security, WS Federation o el cifrado XML. Aun así, gRPC proporciona una seguridad excelente; todo el tráfico de red gRPC se cifra automáticamente cuando se usa HTTP/2 a través de TLS, y los certificados X509 se pueden usar para la autenticación mutua de cliente/servidor.

## <a name="ws-reliablemessaging"></a>WS-ReliableMessaging

gRPC no proporciona un equivalente a WS-ReliableMessaging. La semántica de reintentos debe administrarse en el código, posiblemente con una biblioteca como [Polly](https://github.com/App-vNext/Polly). Al ejecutarse en Kubernetes o en entornos de orquestación similares, las [mallas de servicio](service-mesh.md) también pueden ayudar a proporcionar mensajería confiable entre servicios.

## <a name="ws-transaction-ws-coordination"></a>WS-Transaction, WS-Coordination

La implementación de WCF de transacciones distribuidas usa Microsoft Coordinador de transacciones distribuidas o MSDTC de Windows. Funciona con administradores de recursos que lo admiten específicamente, como SQL Server, MSMQ o sistemas de archivos de Windows. En el mundo de microservicios modernos, en parte debido a la amplia gama de tecnologías en uso, no hay ningún equivalente. Para obtener una descripción de las transacciones, consulte [el apéndice a](appendix.md).

>[!div class="step-by-step"]
>[Anterior](error-handling.md)
>[Siguiente](migrate-wcf-to-grpc.md)

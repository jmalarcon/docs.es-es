---
title: Procedimiento Creación de tareas precalculadas
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, creating pre-computed
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
ms.openlocfilehash: f5d2a70685fe0401d0219b99ada6936ac04691f2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123139"
---
# <a name="how-to-create-pre-computed-tasks"></a>Procedimiento Creación de tareas precalculadas
En este documento se describe cómo utilizar el método <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> para recuperar los resultados de las operaciones asincrónicas de descarga que se retienen en una memoria caché. El método <xref:System.Threading.Tasks.Task.FromResult%2A> devuelve un objeto <xref:System.Threading.Tasks.Task%601> terminado que contiene el valor proporcionado como su propiedad <xref:System.Threading.Tasks.Task%601.Result%2A>. Este método es útil cuando se realiza una operación asincrónica que devuelve un objeto <xref:System.Threading.Tasks.Task%601> y el resultado de ese objeto <xref:System.Threading.Tasks.Task%601> ya se ha calculado.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se descargan cadenas desde la Web. Define el método `DownloadStringAsync`. Este método descarga cadenas de la Web de forma asincrónica. En este ejemplo también se usa un objeto <xref:System.Collections.Concurrent.ConcurrentDictionary%602> para almacenar en caché los resultados de las operaciones anteriores. Si la dirección de entrada se mantiene en esta memoria caché, `DownloadStringAsync` utiliza el método <xref:System.Threading.Tasks.Task.FromResult%2A> para generar un objeto <xref:System.Threading.Tasks.Task%601> que incluye el contenido en esa dirección. En caso contrario, `DownloadStringAsync` descarga el archivo desde la Web y agrega el resultado a la memoria caché.  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 Este ejemplo calcula el tiempo necesario para descargar varias cadenas dos veces. El segundo conjunto de operaciones de descarga debe tardar menos tiempo que el primer conjunto porque los resultados se mantienen en la memoria caché. El método <xref:System.Threading.Tasks.Task.FromResult%2A> habilita el método `DownloadStringAsync` para crear objetos <xref:System.Threading.Tasks.Task%601> que contienen estos resultados precalculados.  
  
## <a name="see-also"></a>Vea también

- [Programación asincrónica basada en tareas](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)

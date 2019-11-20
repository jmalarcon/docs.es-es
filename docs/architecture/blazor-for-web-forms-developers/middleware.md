---
title: Módulos, controladores y middleware
description: Obtenga información sobre cómo controlar las solicitudes HTTP con módulos, controladores y middleware.
author: danroth27
ms.author: daroth
ms.date: 10/11/2019
ms.openlocfilehash: b0be6109b9226bddbb9cbe4cebf114fd2b2a6114
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2019
ms.locfileid: "73841208"
---
# <a name="modules-handlers-and-middleware"></a><span data-ttu-id="9c45a-103">Módulos, controladores y middleware</span><span class="sxs-lookup"><span data-stu-id="9c45a-103">Modules, handlers, and middleware</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="9c45a-104">Una aplicación ASP.NET Core se basa en una serie de middleware.</span><span class="sxs-lookup"><span data-stu-id="9c45a-104">An ASP.NET Core app is built upon a series of middleware.</span></span> <span data-ttu-id="9c45a-105">Los middleware son controladores que se organizan en una canalización para controlar solicitudes y respuestas.</span><span class="sxs-lookup"><span data-stu-id="9c45a-105">Middlewares are handlers, which are arranged into a pipeline to handle requests and responses.</span></span> <span data-ttu-id="9c45a-106">En una aplicación de formularios Web Forms, los controladores y módulos HTTP solucionan problemas similares.</span><span class="sxs-lookup"><span data-stu-id="9c45a-106">In a Web Forms app, HTTP handlers and modules solve similar problems.</span></span> <span data-ttu-id="9c45a-107">En ASP.NET Core, los módulos, los controladores, *global.asax.CS*y el ciclo de vida de la aplicación se reemplazan por middleware.</span><span class="sxs-lookup"><span data-stu-id="9c45a-107">In ASP.NET Core, modules, handlers, *Global.asax.cs*, and the app life cycle are replaced with middleware.</span></span> <span data-ttu-id="9c45a-108">En este capítulo, aprenderá qué middleware en el contexto de una aplicación increíblemente.</span><span class="sxs-lookup"><span data-stu-id="9c45a-108">In this chapter, you'll learn what middleware in the context of a Blazor app.</span></span>

## <a name="overview"></a><span data-ttu-id="9c45a-109">Información general</span><span class="sxs-lookup"><span data-stu-id="9c45a-109">Overview</span></span>

<span data-ttu-id="9c45a-110">La canalización de solicitudes de ASP.NET Core consiste en una secuencia de delegados de solicitud a los que se llama de uno en uno.</span><span class="sxs-lookup"><span data-stu-id="9c45a-110">The ASP.NET Core request pipeline consists of a sequence of request delegates, called one after the other.</span></span> <span data-ttu-id="9c45a-111">En el siguiente diagrama se muestra este concepto.</span><span class="sxs-lookup"><span data-stu-id="9c45a-111">The following diagram demonstrates the concept.</span></span> <span data-ttu-id="9c45a-112">El subproceso de ejecución sigue las flechas negras.</span><span class="sxs-lookup"><span data-stu-id="9c45a-112">The thread of execution follows the black arrows.</span></span>

![DUCCION](media/middleware/request-delegate-pipeline.png)

<span data-ttu-id="9c45a-114">El diagrama anterior carece de un concepto de eventos de ciclo de vida.</span><span class="sxs-lookup"><span data-stu-id="9c45a-114">The preceding diagram lacks a concept of lifecycle events.</span></span> <span data-ttu-id="9c45a-115">Este concepto es fundamental para el modo en que se administran las solicitudes de formularios Web Forms de ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9c45a-115">This concept is foundational to how ASP.NET Web Forms requests are handled.</span></span> <span data-ttu-id="9c45a-116">Este sistema facilita la tarea de pensar en qué proceso está ocurriendo y permite insertar middleware en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="9c45a-116">This system makes it easier to reason about what process is occurring and allows middleware to be inserted at any point.</span></span> <span data-ttu-id="9c45a-117">El middleware se ejecuta en el orden en que se agrega a la canalización de solicitudes.</span><span class="sxs-lookup"><span data-stu-id="9c45a-117">Middleware executes in the order in which it's added to the request pipeline.</span></span> <span data-ttu-id="9c45a-118">También se agregan en el código en lugar de en los archivos de configuración, normalmente en *Startup.CS*.</span><span class="sxs-lookup"><span data-stu-id="9c45a-118">They're also added in code instead of configuration files, usually in *Startup.cs*.</span></span>

## <a name="katana"></a><span data-ttu-id="9c45a-119">Katana</span><span class="sxs-lookup"><span data-stu-id="9c45a-119">Katana</span></span>

<span data-ttu-id="9c45a-120">Los lectores familiarizados con Katana se sienten cómodos en ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="9c45a-120">Readers familiar with Katana will feel comfortable in ASP.NET Core.</span></span> <span data-ttu-id="9c45a-121">De hecho, Katana es un marco del que se deriva ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="9c45a-121">In fact, Katana is a framework from which ASP.NET Core derives.</span></span> <span data-ttu-id="9c45a-122">Se introdujeron patrones similares de middleware y canalización para ASP.NET 4. x.</span><span class="sxs-lookup"><span data-stu-id="9c45a-122">It introduced similar middleware and pipeline patterns for ASP.NET 4.x.</span></span> <span data-ttu-id="9c45a-123">El middleware diseñado para Katana puede adaptarse para trabajar con la canalización de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="9c45a-123">Middleware designed for Katana can be adapted to work with the ASP.NET Core pipeline.</span></span>

## <a name="common-middleware"></a><span data-ttu-id="9c45a-124">Middleware común</span><span class="sxs-lookup"><span data-stu-id="9c45a-124">Common middleware</span></span>

<span data-ttu-id="9c45a-125">ASP.NET 4. x incluye muchos módulos.</span><span class="sxs-lookup"><span data-stu-id="9c45a-125">ASP.NET 4.x includes many modules.</span></span> <span data-ttu-id="9c45a-126">De forma similar, ASP.NET Core tiene también muchos componentes de middleware disponibles.</span><span class="sxs-lookup"><span data-stu-id="9c45a-126">In a similar fashion, ASP.NET Core has many middleware components available as well.</span></span> <span data-ttu-id="9c45a-127">En algunos casos, los módulos IIS se pueden usar con ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="9c45a-127">IIS modules may be used in some cases with ASP.NET Core.</span></span> <span data-ttu-id="9c45a-128">En otros casos, puede que el middleware de ASP.NET Core nativo esté disponible.</span><span class="sxs-lookup"><span data-stu-id="9c45a-128">In other cases, native ASP.NET Core middleware may be available.</span></span>

<span data-ttu-id="9c45a-129">En la tabla siguiente se enumeran los componentes y el middleware de reemplazo en ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="9c45a-129">The following table lists replacement middleware and components in ASP.NET Core.</span></span>

|<span data-ttu-id="9c45a-130">Module</span><span class="sxs-lookup"><span data-stu-id="9c45a-130">Module</span></span>                 |<span data-ttu-id="9c45a-131">Módulo ASP.NET 4. x</span><span class="sxs-lookup"><span data-stu-id="9c45a-131">ASP.NET 4.x module</span></span>           |<span data-ttu-id="9c45a-132">ASP.NET Core, opción</span><span class="sxs-lookup"><span data-stu-id="9c45a-132">ASP.NET Core option</span></span>|
|-----------------------|-----------------------------|-------------------|
|<span data-ttu-id="9c45a-133">Errores HTTP</span><span class="sxs-lookup"><span data-stu-id="9c45a-133">HTTP errors</span></span>            |`CustomErrorModule`          |[<span data-ttu-id="9c45a-134">Middleware de páginas de códigos de estado</span><span class="sxs-lookup"><span data-stu-id="9c45a-134">Status Code Pages Middleware</span></span>](/aspnet/core/fundamentals/error-handling#usestatuscodepages)|
|<span data-ttu-id="9c45a-135">Documento predeterminado</span><span class="sxs-lookup"><span data-stu-id="9c45a-135">Default document</span></span>       |`DefaultDocumentModule`      |[<span data-ttu-id="9c45a-136">Middleware de archivos predeterminados</span><span class="sxs-lookup"><span data-stu-id="9c45a-136">Default Files Middleware</span></span>](/aspnet/core/fundamentals/static-files#serve-a-default-document)|
|<span data-ttu-id="9c45a-137">Examen de directorios</span><span class="sxs-lookup"><span data-stu-id="9c45a-137">Directory browsing</span></span>     |`DirectoryListingModule`     |[<span data-ttu-id="9c45a-138">Middleware de exploración de directorios</span><span class="sxs-lookup"><span data-stu-id="9c45a-138">Directory Browsing Middleware</span></span>](/aspnet/core/fundamentals/static-files#enable-directory-browsing)|
|<span data-ttu-id="9c45a-139">Compresión dinámica</span><span class="sxs-lookup"><span data-stu-id="9c45a-139">Dynamic compression</span></span>    |`DynamicCompressionModule`   |[<span data-ttu-id="9c45a-140">Middleware de compresión de respuestas</span><span class="sxs-lookup"><span data-stu-id="9c45a-140">Response Compression Middleware</span></span>](/aspnet/core/performance/response-compression)|
|<span data-ttu-id="9c45a-141">Seguimiento de solicitudes con error</span><span class="sxs-lookup"><span data-stu-id="9c45a-141">Failed requests tracing</span></span>|`FailedRequestsTracingModule`|[<span data-ttu-id="9c45a-142">Registro de ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9c45a-142">ASP.NET Core Logging</span></span>](/aspnet/core/fundamentals/logging/index#tracesource-provider)|
|<span data-ttu-id="9c45a-143">Almacenamiento en caché de archivos</span><span class="sxs-lookup"><span data-stu-id="9c45a-143">File caching</span></span>           |`FileCacheModule`            |[<span data-ttu-id="9c45a-144">Middleware de almacenamiento en caché de respuestas</span><span class="sxs-lookup"><span data-stu-id="9c45a-144">Response Caching Middleware</span></span>](/aspnet/core/performance/caching/middleware)|
|<span data-ttu-id="9c45a-145">Almacenamiento en caché de HTTP</span><span class="sxs-lookup"><span data-stu-id="9c45a-145">HTTP caching</span></span>           |`HttpCacheModule`            |[<span data-ttu-id="9c45a-146">Middleware de almacenamiento en caché de respuestas</span><span class="sxs-lookup"><span data-stu-id="9c45a-146">Response Caching Middleware</span></span>](/aspnet/core/performance/caching/middleware)|
|<span data-ttu-id="9c45a-147">Registro HTTP</span><span class="sxs-lookup"><span data-stu-id="9c45a-147">HTTP logging</span></span>           |`HttpLoggingModule`          |[<span data-ttu-id="9c45a-148">Registro de ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9c45a-148">ASP.NET Core Logging</span></span>](/aspnet/core/fundamentals/logging/index)|
|<span data-ttu-id="9c45a-149">Redirección HTTP</span><span class="sxs-lookup"><span data-stu-id="9c45a-149">HTTP redirection</span></span>       |`HttpRedirectionModule`      |[<span data-ttu-id="9c45a-150">Middleware de reescritura de dirección URL</span><span class="sxs-lookup"><span data-stu-id="9c45a-150">URL Rewriting Middleware</span></span>](/aspnet/core/fundamentals/url-rewriting)|
|<span data-ttu-id="9c45a-151">filtros ISAPI</span><span class="sxs-lookup"><span data-stu-id="9c45a-151">ISAPI filters</span></span>          |`IsapiFilterModule`          |[<span data-ttu-id="9c45a-152">Middleware</span><span class="sxs-lookup"><span data-stu-id="9c45a-152">Middleware</span></span>](/aspnet/core/fundamentals/middleware/index)|
|<span data-ttu-id="9c45a-153">ISAPI</span><span class="sxs-lookup"><span data-stu-id="9c45a-153">ISAPI</span></span>                  |`IsapiModule`                |[<span data-ttu-id="9c45a-154">Middleware</span><span class="sxs-lookup"><span data-stu-id="9c45a-154">Middleware</span></span>](/aspnet/core/fundamentals/middleware/index)|
|<span data-ttu-id="9c45a-155">Filtrado de solicitudes</span><span class="sxs-lookup"><span data-stu-id="9c45a-155">Request filtering</span></span>      |`RequestFilteringModule`     |[<span data-ttu-id="9c45a-156">Middleware de reescritura de URL IRule</span><span class="sxs-lookup"><span data-stu-id="9c45a-156">URL Rewriting Middleware IRule</span></span>](/aspnet/core/fundamentals/url-rewriting#irule-based-rule)|
|<span data-ttu-id="9c45a-157">Reescritura de URL&#8224;</span><span class="sxs-lookup"><span data-stu-id="9c45a-157">URL rewriting&#8224;</span></span>   |`RewriteModule`              |[<span data-ttu-id="9c45a-158">Middleware de reescritura de dirección URL</span><span class="sxs-lookup"><span data-stu-id="9c45a-158">URL Rewriting Middleware</span></span>](/aspnet/core/fundamentals/url-rewriting)|
|<span data-ttu-id="9c45a-159">Compresión estática</span><span class="sxs-lookup"><span data-stu-id="9c45a-159">Static compression</span></span>     |`StaticCompressionModule`    |[<span data-ttu-id="9c45a-160">Middleware de compresión de respuestas</span><span class="sxs-lookup"><span data-stu-id="9c45a-160">Response Compression Middleware</span></span>](/aspnet/core/performance/response-compression)|
|<span data-ttu-id="9c45a-161">Contenido estático</span><span class="sxs-lookup"><span data-stu-id="9c45a-161">Static content</span></span>         |`StaticFileModule`           |[<span data-ttu-id="9c45a-162">Middleware de archivos estáticos</span><span class="sxs-lookup"><span data-stu-id="9c45a-162">Static File Middleware</span></span>](/aspnet/core/fundamentals/static-files)|
|<span data-ttu-id="9c45a-163">Autorización de URL</span><span class="sxs-lookup"><span data-stu-id="9c45a-163">URL authorization</span></span>      |`UrlAuthorizationModule`     |[<span data-ttu-id="9c45a-164">Identidad de ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9c45a-164">ASP.NET Core Identity</span></span>](/aspnet/core/security/authentication/identity)|

<span data-ttu-id="9c45a-165">Esta lista no es exhaustiva, pero debe dar una idea de la asignación que existe entre los dos marcos.</span><span class="sxs-lookup"><span data-stu-id="9c45a-165">This list isn't exhaustive but should give an idea of what mapping exists between the two frameworks.</span></span> <span data-ttu-id="9c45a-166">Para obtener una lista más detallada, vea [módulos de IIS con ASP.net Core](/aspnet/core/host-and-deploy/iis/modules).</span><span class="sxs-lookup"><span data-stu-id="9c45a-166">For a more detailed list, see [IIS modules with ASP.NET Core](/aspnet/core/host-and-deploy/iis/modules).</span></span>

## <a name="custom-middleware"></a><span data-ttu-id="9c45a-167">Middleware personalizado</span><span class="sxs-lookup"><span data-stu-id="9c45a-167">Custom middleware</span></span>

<span data-ttu-id="9c45a-168">Es posible que el middleware integrado no controle todos los escenarios necesarios para una aplicación.</span><span class="sxs-lookup"><span data-stu-id="9c45a-168">Built-in middleware may not handle all scenarios needed for an app.</span></span> <span data-ttu-id="9c45a-169">En tales casos, tiene sentido crear su propio middleware.</span><span class="sxs-lookup"><span data-stu-id="9c45a-169">In such cases, it makes sense to create your own middleware.</span></span> <span data-ttu-id="9c45a-170">Hay varias maneras de definir el middleware, siendo la más simple un delegado simple.</span><span class="sxs-lookup"><span data-stu-id="9c45a-170">There are multiple ways of defining middleware, with the simplest being a simple delegate.</span></span> <span data-ttu-id="9c45a-171">Considere el siguiente middleware, que acepta una solicitud de referencia cultural de una cadena de consulta:</span><span class="sxs-lookup"><span data-stu-id="9c45a-171">Consider the following middleware, which accepts a culture request from a query string:</span></span>

```csharp
public class Startup
{
    public void Configure(IApplicationBuilder app)
    {
        app.Use(async (context, next) =>
        {
            var cultureQuery = context.Request.Query["culture"];

            if (!string.IsNullOrWhiteSpace(cultureQuery))
            {
                var culture = new CultureInfo(cultureQuery);

                CultureInfo.CurrentCulture = culture;
                CultureInfo.CurrentUICulture = culture;
            }

            // Call the next delegate/middleware in the pipeline
            await next();
        });

        app.Run(async (context) =>
            await context.Response.WriteAsync(
                $"Hello {CultureInfo.CurrentCulture.DisplayName}"));
    }
}
```

<span data-ttu-id="9c45a-172">El middleware también se puede definir como clase, ya sea implementando la interfaz de `IMiddleware` o mediante la siguiente Convención de middleware.</span><span class="sxs-lookup"><span data-stu-id="9c45a-172">Middleware can also be defined as class, either by implementing the `IMiddleware` interface or by following middleware convention.</span></span> <span data-ttu-id="9c45a-173">Para obtener más información, consulte [escritura de middleware de ASP.net Core personalizado](/aspnet/core/fundamentals/middleware/write).</span><span class="sxs-lookup"><span data-stu-id="9c45a-173">For more information, see [Write custom ASP.NET Core middleware](/aspnet/core/fundamentals/middleware/write).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9c45a-174">[Anterior](data.md)
>[Siguiente](config.md)</span><span class="sxs-lookup"><span data-stu-id="9c45a-174">[Previous](data.md)
[Next](config.md)</span></span>
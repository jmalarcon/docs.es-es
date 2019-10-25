---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393911"
---
### <a name="logging-debuglogger-class-made-internal"></a><span data-ttu-id="139fb-101">Registro: la clase DebugLogger se ha convertido en interna</span><span class="sxs-lookup"><span data-stu-id="139fb-101">Logging: DebugLogger class made internal</span></span>

<span data-ttu-id="139fb-102">Antes de ASP.NET Core 3.0, el modificador de acceso de `DebugLogger` era `public`.</span><span class="sxs-lookup"><span data-stu-id="139fb-102">Prior to ASP.NET Core 3.0, `DebugLogger`'s access modifier was `public`.</span></span> <span data-ttu-id="139fb-103">En ASP.NET Core 3.0, el modificador de acceso se ha cambiado a `internal`.</span><span class="sxs-lookup"><span data-stu-id="139fb-103">In ASP.NET Core 3.0, the access modifier changed to `internal`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="139fb-104">Versión introducida</span><span class="sxs-lookup"><span data-stu-id="139fb-104">Version introduced</span></span>

<span data-ttu-id="139fb-105">3.0</span><span class="sxs-lookup"><span data-stu-id="139fb-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="139fb-106">Motivo del cambio</span><span class="sxs-lookup"><span data-stu-id="139fb-106">Reason for change</span></span>

<span data-ttu-id="139fb-107">El cambio se realiza para:</span><span class="sxs-lookup"><span data-stu-id="139fb-107">The change is being made to:</span></span>

* <span data-ttu-id="139fb-108">Aplicar la coherencia con otras implementaciones de registrador como `ConsoleLogger`.</span><span class="sxs-lookup"><span data-stu-id="139fb-108">Enforce consistency with other logger implementations such as `ConsoleLogger`.</span></span>
* <span data-ttu-id="139fb-109">Reducir la superficie de la API.</span><span class="sxs-lookup"><span data-stu-id="139fb-109">Reduce the API surface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="139fb-110">Acción recomendada</span><span class="sxs-lookup"><span data-stu-id="139fb-110">Recommended action</span></span>

<span data-ttu-id="139fb-111">Use el método de extensión <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> de `ILoggingBuilder` para habilitar el registro de depuración.</span><span class="sxs-lookup"><span data-stu-id="139fb-111">Use the <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` extension method to enable debug logging.</span></span> <span data-ttu-id="139fb-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> también sigue siendo `public` en caso de que el servicio se tenga que registrar de forma manual.</span><span class="sxs-lookup"><span data-stu-id="139fb-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> is also still `public` in the event the service needs to be registered manually.</span></span>

#### <a name="category"></a><span data-ttu-id="139fb-113">Categoría</span><span class="sxs-lookup"><span data-stu-id="139fb-113">Category</span></span>

<span data-ttu-id="139fb-114">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="139fb-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="139fb-115">API afectadas</span><span class="sxs-lookup"><span data-stu-id="139fb-115">Affected APIs</span></span>

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->
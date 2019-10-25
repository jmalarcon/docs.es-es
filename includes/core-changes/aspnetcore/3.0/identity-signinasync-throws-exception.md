---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394356"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a><span data-ttu-id="e42f2-101">Identity: SignInAsync produce una excepción para la identidad no autenticada</span><span class="sxs-lookup"><span data-stu-id="e42f2-101">Identity: SignInAsync throws exception for unauthenticated identity</span></span>

<span data-ttu-id="e42f2-102">De forma predeterminada, `SignInAsync` produce una excepción para las entidades de seguridad o identidades en las que `IsAuthenticated` es `false`.</span><span class="sxs-lookup"><span data-stu-id="e42f2-102">By default, `SignInAsync` throws an exception for principals / identities in which `IsAuthenticated` is `false`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e42f2-103">Versión introducida</span><span class="sxs-lookup"><span data-stu-id="e42f2-103">Version introduced</span></span>

<span data-ttu-id="e42f2-104">3.0</span><span class="sxs-lookup"><span data-stu-id="e42f2-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e42f2-105">Comportamiento anterior</span><span class="sxs-lookup"><span data-stu-id="e42f2-105">Old behavior</span></span>

<span data-ttu-id="e42f2-106">`SignInAsync` acepta entidades de seguridad e identidades, incluidas las identidades en las que `IsAuthenticated` es `false`.</span><span class="sxs-lookup"><span data-stu-id="e42f2-106">`SignInAsync` accepts any principals / identities, including identities in which `IsAuthenticated` is `false`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="e42f2-107">Comportamiento nuevo</span><span class="sxs-lookup"><span data-stu-id="e42f2-107">New behavior</span></span>

<span data-ttu-id="e42f2-108">De forma predeterminada, `SignInAsync` produce una excepción para las entidades de seguridad o identidades en las que `IsAuthenticated` es `false`.</span><span class="sxs-lookup"><span data-stu-id="e42f2-108">By default, `SignInAsync` throws an exception for principals / identities in which `IsAuthenticated` is `false`.</span></span> <span data-ttu-id="e42f2-109">Hay una nueva marca para suprimir este comportamiento, pero el comportamiento predeterminado ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="e42f2-109">There's a new flag to suppress this behavior, but the default behavior has changed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e42f2-110">Motivo del cambio</span><span class="sxs-lookup"><span data-stu-id="e42f2-110">Reason for change</span></span>

<span data-ttu-id="e42f2-111">El comportamiento anterior era problemático porque, de forma predeterminada, `[Authorize]` / `RequireAuthenticatedUser()` rechazó estas entidades de seguridad.</span><span class="sxs-lookup"><span data-stu-id="e42f2-111">The old behavior was problematic because, by default, these principals were rejected by `[Authorize]` / `RequireAuthenticatedUser()`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e42f2-112">Acción recomendada</span><span class="sxs-lookup"><span data-stu-id="e42f2-112">Recommended action</span></span>

<span data-ttu-id="e42f2-113">En ASP.NET Core 3.0, versión preliminar 6, hay una marca de `RequireAuthenticatedSignIn` en `AuthenticationOptions` que es `true` de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="e42f2-113">In ASP.NET Core 3.0 Preview 6, there's a `RequireAuthenticatedSignIn` flag on `AuthenticationOptions` that is `true` by default.</span></span> <span data-ttu-id="e42f2-114">Establezca esta marca en `false` para restaurar el comportamiento anterior.</span><span class="sxs-lookup"><span data-stu-id="e42f2-114">Set this flag to `false` to restore the old behavior.</span></span>

#### <a name="category"></a><span data-ttu-id="e42f2-115">Categoría</span><span class="sxs-lookup"><span data-stu-id="e42f2-115">Category</span></span>

<span data-ttu-id="e42f2-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e42f2-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e42f2-117">API afectadas</span><span class="sxs-lookup"><span data-stu-id="e42f2-117">Affected APIs</span></span>

<span data-ttu-id="e42f2-118">None</span><span class="sxs-lookup"><span data-stu-id="e42f2-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
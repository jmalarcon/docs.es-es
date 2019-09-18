---
title: Ensamblados con nombre seguro
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, about strong-named assemblies
- assemblies [.NET Framework], strong-named
ms.assetid: d4a80263-f3e0-4d81-9b61-f0cbeae3797b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67beeba6ce33fb1a8c3d02337d98282ccf30341a
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991292"
---
# <a name="strong-named-assemblies"></a><span data-ttu-id="fe548-102">Ensamblados con nombre seguro</span><span class="sxs-lookup"><span data-stu-id="fe548-102">Strong-named assemblies</span></span>

<span data-ttu-id="fe548-103">Al asignar un nombre seguro a un ensamblado, se crea una identidad única para este, lo que puede evitar conflictos de ensamblado.</span><span class="sxs-lookup"><span data-stu-id="fe548-103">Strong-naming an assembly creates a unique identity for the assembly, and can prevent assembly conflicts.</span></span>

## <a name="what-makes-a-strong-named-assembly"></a><span data-ttu-id="fe548-104">¿Cómo se obtiene un ensamblado con nombre seguro?</span><span class="sxs-lookup"><span data-stu-id="fe548-104">What makes a strong-named assembly?</span></span>

<span data-ttu-id="fe548-105">Para generar un ensamblado con nombre seguro es necesario usar la clave privada que se corresponda con la clave pública distribuida con el ensamblado, además del ensamblado en sí.</span><span class="sxs-lookup"><span data-stu-id="fe548-105">A strong named assembly is generated by using the private key that corresponds to the public key distributed with the assembly, and the assembly itself.</span></span> <span data-ttu-id="fe548-106">En el ensamblado se incluye el manifiesto del ensamblado, que contiene los nombres y los hash de todos los archivos que componen el ensamblado.</span><span class="sxs-lookup"><span data-stu-id="fe548-106">The assembly includes the assembly manifest, which contains the names and hashes of all the files that make up the assembly.</span></span> <span data-ttu-id="fe548-107">Los ensamblados que tengan el mismo nombre seguro deben ser idénticos.</span><span class="sxs-lookup"><span data-stu-id="fe548-107">Assemblies that have the same strong name should be identical.</span></span>

<span data-ttu-id="fe548-108">Para asignar nombres seguros a ensamblados puede usar Visual Studio o una herramienta de línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="fe548-108">You can strong-name assemblies by using Visual Studio or a command-line tool.</span></span> <span data-ttu-id="fe548-109">Para obtener más información, vea [Cómo: Firmar un ensamblado con un nombre seguro](sign-strong-name.md) o [Sn.exe (herramienta de nombre seguro)](../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="fe548-109">For more information, see [How to: Sign an assembly with a strong name](sign-strong-name.md) or [Sn.exe (Strong Name tool)](../../framework/tools/sn-exe-strong-name-tool.md).</span></span>

<span data-ttu-id="fe548-110">Al crear un ensamblado con nombre seguro, este contiene el nombre de texto simple del ensamblado, el número de versión, información opcional de referencia cultural, una firma digital y la clave pública que se corresponda con la clave privada usada para la firma.</span><span class="sxs-lookup"><span data-stu-id="fe548-110">When a strong-named assembly is created, it contains the simple text name of the assembly, the version number, optional culture information, a digital signature, and the public key that corresponds to the private key used for signing.</span></span>

> [!WARNING]
> <span data-ttu-id="fe548-111">Para garantizar la seguridad, no confíe únicamente en el uso de nombres seguros.</span><span class="sxs-lookup"><span data-stu-id="fe548-111">Do not rely on strong names for security.</span></span> <span data-ttu-id="fe548-112">Estos solo proporcionan una identidad única.</span><span class="sxs-lookup"><span data-stu-id="fe548-112">They provide a unique identity only.</span></span>

## <a name="why-strong-name-your-assemblies"></a><span data-ttu-id="fe548-113">¿Por qué asignar nombres seguros a los ensamblados?</span><span class="sxs-lookup"><span data-stu-id="fe548-113">Why strong-name your assemblies?</span></span>

<span data-ttu-id="fe548-114">Cuando se hace referencia a un ensamblado con nombre seguro, se espera obtener ciertas ventajas, como el control de versiones y la protección de nombres.</span><span class="sxs-lookup"><span data-stu-id="fe548-114">When you reference a strong-named assembly, you can expect certain benefits, such as versioning and naming protection.</span></span> <span data-ttu-id="fe548-115">En .NET Framework, los ensamblados con nombre seguro se pueden instalar en la caché global de ensamblados, lo cual es necesario para permitir algunos escenarios.</span><span class="sxs-lookup"><span data-stu-id="fe548-115">In the .NET Framework, strong-named assemblies can be installed in the global assembly cache, which is required to enable some scenarios.</span></span>

<span data-ttu-id="fe548-116">Los ensamblados con nombre seguro son útiles en los escenarios siguientes:</span><span class="sxs-lookup"><span data-stu-id="fe548-116">Strong-named assemblies are useful in the following scenarios:</span></span>

- <span data-ttu-id="fe548-117">Cuando quiere habilitar los ensamblados para hacer referencia a ensamblados con nombre seguro, o quiere dar acceso `friend` a sus ensamblados desde otros ensamblados con nombre seguro.</span><span class="sxs-lookup"><span data-stu-id="fe548-117">You want to enable your assemblies to be referenced by strong-named assemblies, or you want to give `friend` access to your assemblies from other strong-named assemblies.</span></span>

- <span data-ttu-id="fe548-118">Cuando una aplicación necesita acceder a versiones diferentes del mismo ensamblado.</span><span class="sxs-lookup"><span data-stu-id="fe548-118">An app needs access to different versions of the same assembly.</span></span> <span data-ttu-id="fe548-119">Esto quiere decir que necesita cargar en paralelo diferentes versiones de un ensamblado en el mismo dominio de la aplicación sin que surjan conflictos.</span><span class="sxs-lookup"><span data-stu-id="fe548-119">This means  you need different versions of an assembly to load side by side in the same app domain without conflict.</span></span> <span data-ttu-id="fe548-120">Por ejemplo, si existen diferentes extensiones de una API en ensamblados que tienen el mismo nombre simple, los nombres seguros proporcionan una identidad única para cada versión del ensamblado.</span><span class="sxs-lookup"><span data-stu-id="fe548-120">For example, if different extensions of an API exist in assemblies that have the same simple name, strong-naming provides a unique identity for each version of the assembly.</span></span>

- <span data-ttu-id="fe548-121">Cuando no quiere que el rendimiento de las aplicaciones que usan el ensamblado se vea afectado, por lo que el ensamblado debe ser de dominio neutro.</span><span class="sxs-lookup"><span data-stu-id="fe548-121">You do not want to negatively affect performance of apps using your assembly, so you want the assembly to be domain neutral.</span></span> <span data-ttu-id="fe548-122">Esto requiere nombres seguros, ya que se debe instalar un ensamblado de dominio neutro en la caché global de ensamblados.</span><span class="sxs-lookup"><span data-stu-id="fe548-122">This requires strong-naming because a domain-neutral assembly must be installed in the global assembly cache.</span></span>

- <span data-ttu-id="fe548-123">Cuando quiere centralizar el servicio de la aplicación mediante una directiva de edición, lo que significa que el ensamblado se debe instalar en la caché global de ensamblados.</span><span class="sxs-lookup"><span data-stu-id="fe548-123">You want to centralize servicing for your app by applying publisher policy, which means the assembly must be installed in the global assembly cache.</span></span>

<span data-ttu-id="fe548-124">Si es un desarrollador de código abierto y quiere obtener las ventajas de identidad de un ensamblado con nombre seguro, proteja la clave privada asociada con un ensamblado en el sistema de control de código fuente.</span><span class="sxs-lookup"><span data-stu-id="fe548-124">If you are an open-source developer and you want the identity benefits of a strong-named assembly, consider checking in the private key associated with an assembly to your source control system.</span></span>

## <a name="see-also"></a><span data-ttu-id="fe548-125">Vea también</span><span class="sxs-lookup"><span data-stu-id="fe548-125">See also</span></span>

- [<span data-ttu-id="fe548-126">Caché global de ensamblados</span><span class="sxs-lookup"><span data-stu-id="fe548-126">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
- [<span data-ttu-id="fe548-127">Cómo: Firmar un ensamblado con un nombre seguro</span><span class="sxs-lookup"><span data-stu-id="fe548-127">How to: Sign an assembly with a strong name</span></span>](sign-strong-name.md)
- [<span data-ttu-id="fe548-128">Sn.exe (herramienta de nombre seguro)</span><span class="sxs-lookup"><span data-stu-id="fe548-128">Sn.exe (Strong Name tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="fe548-129">Creación y uso de ensamblados con nombre seguro</span><span class="sxs-lookup"><span data-stu-id="fe548-129">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
---
ms.openlocfilehash: e16f0c8ede5e1a24d4fc4606c3c25225ea72e750
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929985"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a><span data-ttu-id="dd656-101">Ha cambiado la firma de JsonFactoryConverter.CreateConverter</span><span class="sxs-lookup"><span data-stu-id="dd656-101">JsonFactoryConverter.CreateConverter signature changed</span></span>

<span data-ttu-id="dd656-102">Para facilitar la composición de las clases <xref:System.Text.Json.Serialization.JsonConverterFactory>, se ha hecho público el método <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> y se le ha dado un segundo argumento de tipo <xref:System.Text.Json.JsonSerializerOptions>.</span><span class="sxs-lookup"><span data-stu-id="dd656-102">To facilitate the composition of <xref:System.Text.Json.Serialization.JsonConverterFactory> classes, the <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> method has been made public and given a second argument of type <xref:System.Text.Json.JsonSerializerOptions>.</span></span>

#### <a name="details"></a><span data-ttu-id="dd656-103">Detalles</span><span class="sxs-lookup"><span data-stu-id="dd656-103">Details</span></span>

<span data-ttu-id="dd656-104">La firma del método `CreateConverter` en .NET Core antes de la versión 3.0 (versión preliminar 8) era la siguiente:</span><span class="sxs-lookup"><span data-stu-id="dd656-104">The signature of the `CreateConverter` method in .NET Core prior to version 3.0 Preview 8 was:</span></span> 

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

<span data-ttu-id="dd656-105">En .NET Core 3.0 (versión preliminar 8) y en versiones posteriores es la siguiente:</span><span class="sxs-lookup"><span data-stu-id="dd656-105">In .NET Core 3.0 Preview 8 and later versions, it is:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

<span data-ttu-id="dd656-106">Antes de este cambio, era difícil crear convertidores de generadores sellados, ya que no había ninguna manera fácil de obtener la clase <xref:System.Text.Json.Serialization.JsonConverter%601>.</span><span class="sxs-lookup"><span data-stu-id="dd656-106">Before this change, it was difficult to compose sealed factory converters, since there was no easy way to get the <xref:System.Text.Json.Serialization.JsonConverter%601> from it.</span></span> <span data-ttu-id="dd656-107">Hacer público el patrón de diseño Factory Method y pasar la clase <xref:System.Text.Json.JsonSerializerOptions> actual permiten una composición mucho más flexible.</span><span class="sxs-lookup"><span data-stu-id="dd656-107">Making the factory method public and also passing the current <xref:System.Text.Json.JsonSerializerOptions> allow for much more flexible composition.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="dd656-108">Versión introducida</span><span class="sxs-lookup"><span data-stu-id="dd656-108">Version introduced</span></span>

<span data-ttu-id="dd656-109">3.0 (versión preliminar 8)</span><span class="sxs-lookup"><span data-stu-id="dd656-109">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="dd656-110">Acción recomendada</span><span class="sxs-lookup"><span data-stu-id="dd656-110">Recommended action</span></span>

<span data-ttu-id="dd656-111">Es necesario actualizar y volver a compilar las clases derivadas.</span><span class="sxs-lookup"><span data-stu-id="dd656-111">Derived classes need to be updated and recompiled.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="dd656-112">API afectadas</span><span class="sxs-lookup"><span data-stu-id="dd656-112">Affected APIs</span></span>

<span data-ttu-id="dd656-113"><xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dd656-113"><xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.</span></span>

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
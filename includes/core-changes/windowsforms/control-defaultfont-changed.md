---
ms.openlocfilehash: 843007ac6467584fbe6350b6ea19ef67609d73e2
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216916"
---
### <a name="controldefaultfont-changed-to-segoe-ui-9pt"></a>Cambio de `Control.DefaultFont` a `Segoe UI 9pt`

#### <a name="change-description"></a>Descripción del cambio

En .NET Framework, la propiedad <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> se estableció en `Microsoft Sans Serif 8pt`. En la figura siguiente se muestra una ventana en la que se usa la fuente predeterminada.

![fuente de control predeterminada en .NET Framework](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

En .NET Core, a partir de .NET Core 3.0, se establece en `Segoe UI 9pt` (la misma fuente que <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>). Como resultado de este cambio, los formularios y controles tendrán un tamaño predeterminado aproximadamente un 27 % más grande para tener en cuenta el mayor tamaño de la nueva fuente predeterminada. Por ejemplo:

![fuente de control predeterminada en .NET Core](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

Este cambio se realizó para alinearse con las [directrices para la experiencia de usuario de Windows](https://docs.microsoft.com/windows/win32/uxguide/vis-fonts#fonts-and-colors).

#### <a name="version-introduced"></a>Versión introducida

3.0

#### <a name="recommended-action"></a>Acción recomendada

Debido al cambio en el tamaño de los formularios y controles, asegúrese de que la aplicación se representa correctamente.

Para conservar la fuente original, establezca la fuente predeterminada del formulario en `Microsoft Sans Serif 8pt`. Por ejemplo:

```csharp
public MyForm()
{
    InitializeComponent();
    Font = new Font(new FontFamily("Microsoft Sans Serif"), 8f);
}
```

#### <a name="category"></a>Categoría

- Windows Forms

#### <a name="affected-apis"></a>API afectadas

Ninguno.

<!--

### Affected APIs

- Not detectable via API analysis

-->

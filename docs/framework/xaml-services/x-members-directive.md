---
title: Directiva de x:Members
ms.date: 03/30/2017
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
ms.openlocfilehash: ca42079c1c40a8fb3b1ddfc8f4a6f742768fa9e1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053771"
---
# <a name="xmembers-directive"></a>Directiva de x:Members
Contiene un conjunto de miembros que se definen en el marcado, que se aplican a la x:Class del elemento primario.  
  
## <a name="xaml-attribute-usage"></a>Uso de atributos XAML  
  
```xaml  
<object x:Class="className">  
  <x:Members>  
    oneOrMoreMembers  
  </x:Members  
</object>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`className`|Nombre de la clase de respaldo o clase parcial para la producción de XAML. Vea la sección Comentarios.|  
|`oneOrMoreMembers`|Uno o más elementos de objeto que representan definiciones de miembros. Normalmente, se `x:Property` trata de elementos de objeto. Vea la sección Comentarios.|  
  
## <a name="remarks"></a>Comentarios  
 En la implementación de los servicios de .NET Framework XAML, no hay ninguna clase de respaldo ni `x:Members`implementación de miembro subyacente para. `x:Members`es un miembro XAML especial que puede existir como miembro en cualquier tipo. En un flujo de nodo XAML `x:Members` , se representa como un miembro `Members`denominado, del espacio de nombres XAML del lenguaje XAML. El miembro `Members` contiene una lista genérica de solo lectura de `Member` objetos. En el marcado habitual, los miembros individuales se `x:Property` especifican como elementos de propiedad. `x:Property`es un tipo más preciso específicamente para las propiedades de tipos y se puede asignar a `x:Member`. Para obtener más información, consulte [la Directiva x:Property](x-property-directive.md).  
  
 Para admitir un uso práctico de `x:Members` como medio para especificar definiciones de miembros en el marcado, los miembros deben asociarse con una clase que se pueda modificar. El modelo previsto es que `x:Members` exista como miembro de un tipo que especifica una `x:Class`. Sin embargo, el mecanismo para asociar tipos y miembros o para generar definiciones de miembros dinámicas no se admite en el nivel de los servicios XAML de .NET Framework. De esto se encargan los marcos individuales que tienen modelos de aplicación compatibles con las definiciones de miembro de XAML. Normalmente, para admitir esta característica se necesitan acciones de compilación de MSBUILD que compilan XAML por marcado y, o bien lo integran con código subyacente o producen ensamblados puros a partir de XAML.  
  
## <a name="xmembers-for-windows-workflow-foundation"></a>x:Members para Windows Workflow Foundation  
 Por Windows Workflow Foundation, `x:Members` contiene los miembros de una actividad personalizada compuestas completamente en XAML o miembros dinámicos definidos por XAML para un diseñador de actividad con código subyacente. `x:Class` también se debe especificar en el elemento raíz de la producción de XAML. Esto no es un requisito de los servicios XAML de .NET Framework, pero es obligatorio cuando la producción de XAML se carga mediante las acciones de compilación de MSBUILD que admiten actividades personalizadas y XAML en Windows Workflow Foundation en general. `x:Members`debe ser el primer elemento secundario en el marcado del elemento de objeto que declara `x:Class`.

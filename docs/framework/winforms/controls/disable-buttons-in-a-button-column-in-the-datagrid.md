---
title: Procedimiento para deshabilitar botones en una columna de botones del control DataGridView de formularios Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], disabling buttons
- buttons [Windows Forms], disabling in button columns
- DataGridView control [Windows Forms], disabling button cells
ms.assetid: 5c344d01-013a-4a6b-8f8d-62ec9321d81e
ms.openlocfilehash: b8bb503186e41c682b0685e4c9c4bf0bb3adcbe8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967396"
---
# <a name="how-to-disable-buttons-in-a-button-column-in-the-windows-forms-datagridview-control"></a>Procedimiento para deshabilitar botones en una columna de botones del control DataGridView de formularios Windows Forms
El control <xref:System.Windows.Forms.DataGridView> incluye la clase <xref:System.Windows.Forms.DataGridViewButtonCell> para mostrar celdas con una interfaz de usuario (IU) como un botón. Sin embargo, <xref:System.Windows.Forms.DataGridViewButtonCell> no proporciona una manera de deshabilitar el aspecto del botón mostrado por la celda.  
  
 En el ejemplo de código siguiente, se muestra cómo personalizar la clase <xref:System.Windows.Forms.DataGridViewButtonCell> para mostrar botones que pueden aparecer deshabilitados. En el ejemplo se define un nuevo tipo de celda, `DataGridViewDisableButtonCell`, que deriva de <xref:System.Windows.Forms.DataGridViewButtonCell>. Este tipo de celda proporciona una nueva propiedad `Enabled`, que puede establecerse en `false` para dibujar un botón deshabilitado en la celda. El ejemplo también define un nuevo tipo de columna, `DataGridViewDisableButtonColumn`, que muestra objetos `DataGridViewDisableButtonCell`. Para demostrar este nuevo tipo de celda y de columna, el valor actual de cada <xref:System.Windows.Forms.DataGridViewCheckBoxCell> en el elemento primario <xref:System.Windows.Forms.DataGridView> determina si la propiedad `Enabled` de la `DataGridViewDisableButtonCell` en la misma fila es `true` o `false`.  
  
> [!NOTE]
> Al derivar de <xref:System.Windows.Forms.DataGridViewCell> o <xref:System.Windows.Forms.DataGridViewColumn> y agregar nuevas propiedades a la clase derivada, asegúrese de invalidar el método `Clone` para copiar las nuevas propiedades durante las operaciones de clonación. También debe llamar al método `Clone` de la clase base para copiar las propiedades de la clase base a la nueva celda o columna.  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Para este ejemplo se necesita:  
  
- Referencias a los ensamblados System, System.Drawing, System.Windows.Forms y System.Windows.Forms.VisualStyles.  
  
## <a name="see-also"></a>Vea también

- [Personalizar el control DataGridView de Windows Forms](customizing-the-windows-forms-datagridview-control.md)
- [Arquitectura del control DataGridView](datagridview-control-architecture-windows-forms.md)
- [Tipos de columnas en el control DataGridView de Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)

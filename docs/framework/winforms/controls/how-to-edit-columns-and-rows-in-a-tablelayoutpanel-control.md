---
title: Procedimiento para editar columnas y filas en un control TableLayoutPanel
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: 99ff3286592da0a097835b8f35d687475ca54fb0
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040294"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a>Procedimiento para editar columnas y filas en un control TableLayoutPanel

Puede usar el editor de la <xref:System.Windows.Forms.TableLayoutPanel> colección del control, denominado cuadro de diálogo estilos de **columna y fila** , para editar las filas y columnas de los controles.

> [!NOTE]
> Si desea que un control abarque varias filas o columnas, establezca las `RowSpan` propiedades y `ColumnSpan` en el control. Para obtener más información, vea [Tutorial: Organizar controles en Windows Forms mediante un control TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).
>
> Si desea alinear un control dentro de una celda, o si desea que un control se estire dentro de una celda, use la propiedad <xref:System.Windows.Forms.Control.Anchor%2A> del control. Para obtener más información, vea [Tutorial: Organizar controles en Windows Forms mediante un control TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).

## <a name="to-edit-rows-and-columns"></a>Para editar filas y columnas

1. Arrastre un control <xref:System.Windows.Forms.TableLayoutPanel> del **cuadro de herramientas** al formulario.

2. Haga clic <xref:System.Windows.Forms.TableLayoutPanel> en el glifo de la etiqueta inteligente del control (![glifo de etiqueta inteligente](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) y seleccione **Editar filas y columnas** para abrir el cuadro de diálogo **estilos de columna y fila** . También puede hacer clic con el botón <xref:System.Windows.Forms.TableLayoutPanel> derecho en el control y seleccionar **Editar filas y columnas** en el menú contextual.

3. Para agregar o quitar columnas, seleccione **columnas** en el cuadro de lista desplegable **tipo de miembro** .

4. Para agregar o quitar filas, seleccione **filas** en el cuadro de lista desplegable **tipo de miembro** .

5. Haga clic en el botón **Agregar** para agregar una fila o columna al final de la lista de **miembros** .

6. Haga clic en el botón **Insertar** para agregar una fila o columna delante del elemento seleccionado actualmente en la lista.

7. Si va a agregar una fila o una columna, seleccione el **tipo de tamaño** de la nueva fila o columna. Para obtener más información, consulta <xref:System.Windows.Forms.SizeType>.

8. Para quitar una fila o columna, haga clic en el botón **quitar** para eliminar el elemento seleccionado actualmente en la lista de **miembros** .

## <a name="see-also"></a>Vea también

- <xref:System.Windows.Forms.SizeType>
- [Control TableLayoutPanel](tablelayoutpanel-control-windows-forms.md)

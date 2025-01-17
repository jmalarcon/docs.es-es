---
title: Procedimiento para agrupar controles con el control Panel de formularios Windows Forms mediante el diseñador
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: cadfa715b140c63b216ec0ca2e6d6a6589ae3458
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040387"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a>Procedimiento para agrupar controles con el control Panel de formularios Windows Forms mediante el diseñador
Windows Forms <xref:System.Windows.Forms.Panel> controles se usan para agrupar otros controles. Hay tres razones para agrupar los controles. Una es la agrupación visual de los elementos de formulario relacionados para una interfaz de usuario clara; otro es la agrupación mediante programación, de botones de radio, por ejemplo; la última es para mover los controles como una unidad en tiempo de diseño.

## <a name="to-create-a-group-of-controls"></a>Para crear un grupo de controles

1. Arrastre un <xref:System.Windows.Forms.Panel> control desde la pestaña **Windows Forms** del cuadro de herramientas hasta un formulario.

2. Agregue otros controles al panel y dibuje cada uno dentro del panel.

     Si tiene controles existentes que desea incluir en un panel, puede seleccionar todos los controles, recortarlos en el portapapeles, seleccionar el <xref:System.Windows.Forms.Panel> control y, a continuación, pegarlos en el panel. También puede arrastrarlos al panel.

3. Opta Si desea agregar un borde a un panel, establezca su <xref:System.Windows.Forms.BorderStyle> propiedad. Hay tres opciones: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>y <xref:System.Windows.Forms.BorderStyle.None>.

## <a name="see-also"></a>Vea también

- [Panel (control)](panel-control-windows-forms.md)
- [Información general del control Panel](panel-control-overview-windows-forms.md)
- [Procedimientos: Establecer el fondo de un panel](how-to-set-the-background-of-a-windows-forms-panel.md)

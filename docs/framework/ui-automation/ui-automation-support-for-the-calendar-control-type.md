---
title: Compatibilidad de UI Automation para el tipo de control Calendar
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Calendar control type
- Calendar control type
- control types, Calendar
ms.assetid: e91a7393-a7f9-4838-a1a6-857438b24bc9
ms.openlocfilehash: 0096ce3703a04feece49eea2580d49b7d947ecb3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2019
ms.locfileid: "71041925"
---
# <a name="ui-automation-support-for-the-calendar-control-type"></a>Compatibilidad de UI Automation para el tipo de control Calendar
> [!NOTE]
> Esta documentación está dirigida a los desarrolladores de .NET Framework que quieran usar las clases [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] administradas definidas en el espacio de nombres <xref:System.Windows.Automation>. Para obtener la información más [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]reciente acerca [de, consulte API de automatización de Windows: Automatización](https://go.microsoft.com/fwlink/?LinkID=156746)de la interfaz de usuario.  
  
 En este tema se ofrece información sobre la compatibilidad de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] con el tipo de control Calendar. En [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], un tipo de control es un conjunto de condiciones que un control debe cumplir para poder usar la propiedad <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Entre las condiciones se incluyen instrucciones específicas para la estructura de árbol de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , valores de propiedad de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , patrones de control y eventos de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
 Los controles Calendar permiten a un usuario determinar la fecha y seleccionar otras fechas con facilidad.  
  
 En las secciones siguientes se definen la estructura de árbol de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] necesaria, las propiedades, los patrones de control y los eventos para el tipo de control Calendar. Los requisitos [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] se aplican a todos los controles de calendario, ya sean [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]o [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Estructura de árbol de automatización de interfaz de usuario necesaria  
 En la tabla siguiente se describe la vista de control y la vista de contenido del árbol de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] que pertenece a los controles de calendario y se describe lo que puede incluirse en cada vista. Para más información sobre el árbol [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , vea [UI Automation Tree Overview](ui-automation-tree-overview.md).  
  
|Vista de control|Vista de contenido|  
|------------------|------------------|  
|Calendario<br /><br /> <ul><li>DataGrid<br /><br /> <ul><li>Header (0 o 1)</li><li>HeaderItem (0 o 7; la cantidad depende del número de días que se muestren en columnas)</li><li>ListItem (la cantidad depende del número de días que se muestren)</li><li>Button (0 o 2; para la paginación de la vista de calendario)</li></ul></li></ul>|Calendario<br /><br /> -ListItem (la cantidad depende del número de días que se muestren)|  
  
 Los controles de calendario se pueden representar de muchas formas diferentes dentro de la interfaz de usuario. Los únicos controles que con seguridad están en la vista de control del árbol de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] son los controles de cuadrícula de datos, encabezado, elemento de encabezado y elemento de lista.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Propiedades necesarias para la automatización de la interfaz de usuario  
 En la tabla siguiente se muestran las propiedades de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] que tienen un valor o una definición que es especialmente relevante para los controles de calendario. Para obtener más información [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sobre las propiedades, vea [UI Automation Properties for clients](ui-automation-properties-for-clients.md).  
  
|Propiedad[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Valor|Notas|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Vea las notas.|El valor de esta propiedad debe ser único en todos los controles de una aplicación.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Vea las notas.|El rectángulo exterior que contiene el control completo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Vea las notas.|Se admite si hay un rectángulo delimitador. Si no todos los puntos que se encuentran dentro del rectángulo delimitador son seleccionables, y realiza pruebas de aciertos especializadas, invalide y ofrezca un punto en el que hacer clic.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Calendario|Este valor es el mismo para todos los marcos de trabajo [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|El control de calendario siempre se incluye en la vista de contenido del árbol de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|El control de calendario siempre se incluye en la vista de control del árbol de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Vea las notas.|Si el control puede recibir el enfoque del teclado, debe admitir esta propiedad.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Vea las notas.|La etiqueta del control de documento. Normalmente, se utiliza el título del documento.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"calendario"|Cadena localizada que corresponde al tipo de control Calendar.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Vea las notas.|Normalmente, el control de calendario recibe su nombre de la fecha del día actual.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Patrones de control necesarios para la automatización de la interfaz de usuario  
 En la tabla siguiente se muestran los patrones de control de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] que se deben admitir por todos los controles de calendario. Para más información sobre los patrones de control, vea [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md).  
  
|Patrón de control/Propiedad de patrón|Soporte técnico|Notas|  
|---------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Sí|El control de calendario siempre admite el patrón Grid porque los días en un mes son elementos que se pueden recorrer espacialmente.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Depende|La mayoría de los controles de calendario admiten voltear la vista por página. Se recomienda el patrón Scroll para admitir la navegación de paginación.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Depende|La mayoría de los controles de calendario conservan un determinado día, mes o año como una selección del subelemento. Algunos calendarios son de selección múltiple y otros solamente de selección sencilla.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Sí|El control de calendario siempre tiene un encabezado dentro de su subárbol para los días de la semana, por lo que se debe admitir el patrón Table.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Sin|El patrón de control Value no es necesario para los controles de calendario porque no se puede establecer el valor directamente en el control. Si una fecha concreta está asociada con el control, el patrón de control Selection debe proporcionar la información.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Eventos de automatización de la interfaz de usuario necesarios  
 En la tabla siguiente se muestran los eventos de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] que deben admitir todos los controles de calendario. Para más información sobre eventos, vea [UI Automation Events Overview](ui-automation-events-overview.md).  
  
|o[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Soporte técnico|Notas|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Requerido|None|  
|Evento cambiado por propiedad<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> .|Obligatorio|None|  
|Evento cambiado por propiedad<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> .|Obligatorio|None|  
|Evento cambiado por propiedad<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> .|Obligatorio|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Obligatorio|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Obligatorio|None|  
|Evento de cambio de propiedad<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty> .|Depende|None|  
|Evento cambiado por propiedad<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> .|Depende|Si el control admite el patrón de control Scroll, debe admitir este evento.|  
|Evento cambiado por propiedad<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> .|Depende|Si el control admite el patrón de control Scroll, debe admitir este evento.|  
|Evento cambiado por propiedad<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> .|Depende|Si el control admite el patrón de control Scroll, debe admitir este evento.|  
|Evento cambiado por propiedad<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> .|Depende|Si el control admite el patrón de control Scroll, debe admitir este evento.|  
|Evento cambiado por propiedad<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> .|Depende|Si el control admite el patrón de control Scroll, debe admitir este evento.|  
|Evento cambiado por propiedad<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> .|Depende|Si el control admite el patrón de control Scroll, debe admitir este evento.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Obligatorio|None|  
  
## <a name="see-also"></a>Vea también

- <xref:System.Windows.Automation.ControlType.Calendar>
- [Información general sobre tipos de control de Automatización de la interfaz de usuario](ui-automation-control-types-overview.md)
- [Información general sobre la Automatización de la interfaz de usuario](ui-automation-overview.md)

---
title: Compatibilidad de UI Automation con controles estándar
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 6cbf31c8a1cdf6e853e56445d22f4a7513bd1859
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042006"
---
# <a name="ui-automation-support-for-standard-controls"></a>Compatibilidad de UI Automation con controles estándar
> [!NOTE]
> Esta documentación está dirigida a los desarrolladores de .NET Framework que quieran usar las clases [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] administradas definidas en el espacio de nombres <xref:System.Windows.Automation>. Para obtener la información más [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]reciente acerca [de, consulte API de automatización de Windows: Automatización](https://go.microsoft.com/fwlink/?LinkID=156746)de la interfaz de usuario.  
  
 En este tema se incluye información sobre la compatibilidad de [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] con controles estándar en las aplicaciones desarrolladas para los marcos de trabajo [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]y [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] .  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a>Controles de Windows Presentation Foundation  
 Todos los elementos de control [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] que ofrecen información o compatibilidad para la interacción del usuario tienen compatibilidad nativa completa con [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Otros elementos, como paneles, no son visibles para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a>Controles de Win32  
 La mayoría de los controles [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] se exponen a [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] a través de los proveedores del cliente en UIAutomationClientsideProviders.dll. Este ensamblado se registra automáticamente para su uso con aplicaciones de cliente de automatización de la interfaz de usuario.  
  
 Solo se proporciona compatibilidad completa para controles desde la versión 6 de ComCtrl32.dll (disponibles con [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] y versiones posteriores).  
  
 Se admiten los siguientes controles.  
  
|Nombre de la clase|Tipo de control|  
|----------------|------------------|  
|Botón|Botón|  
|Botón|RadioButton|  
|Botón|Grupo|  
|Botón|CheckBox|  
|Botón|Hipervínculo|  
|Botón|SplitButton|  
|Botón|CheckBox|  
|ComboBoxEx32|ComboBox|  
|ComboBox|ComboBox|  
|Editar|Documento|  
|Editar|Editar|  
|SysLink|Hipervínculo|  
|estática|Text|  
|Estático|Image|  
|SysIPAddress32|Personalizados|  
|SysHeader32|Header/HeaderItem|  
|SysListView32|DataGrid|  
|SysListView32|Enumerar|  
|ListBox|Enumerar|  
|ListBox|ListItem|  
|#32768|Menú|  
|#32768|MenuItem|  
|msctls_progress32|ProgressBar|  
|RichEdit|Documento. Vea la nota.|  
|RichEdit20A|Documento|  
|RichEdit20W|Documento|  
|RichEdit50W|Documento|  
|ScrollBar|Slider|  
|msctls_trackbar32|Slider|  
|msctls_updown32|Spinner|  
|msctls_statusbar32|StatusBar|  
|SysTabControl32|Tab|  
|SysTabControl32|TabItem|  
|ToolbarWindow32|ToolBar|  
|ToolbarWindow32|MenuItem|  
|ToolbarWindow32|Botón|  
|ToolbarWindow32|CheckBox|  
|ToolbarWindow32|RadioButton|  
|ToolbarWindow32|Separador|  
|tooltips_class32|Información sobre herramientas|  
|#32774|Información sobre herramientas|  
|ReBarWindow32|Barra de herramientas|  
|SysTreeView32|Árbol|  
|SysTreeView32|TreeItem|  
  
 **Nota** El control RichEdit solo se admite para las versiones incluidas con [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (en RichEd20.dll versión 3.1 y posteriores, y MsftEdit.dll versión 4.1 y posteriores).  
  
 No se admiten los siguientes controles.  
  
|Nombre de la clase|Tipo de control|  
|----------------|------------------|  
|SysAnimate32|Image|  
|SysPager|Spinner|  
|SysDateTimePick32|Personalizados|  
|SysMonthCal32|Calendario|  
|MS_WINNOTE|Información sobre herramientas|  
|VBBubble|Información sobre herramientas|  
|ScrollBar (cuando se usa como control independiente)|Slider|  
|SuperGrid|Personalizados|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a>Controles de Windows Forms  
 Windows Forms controles se exponen a [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] a través de los proveedores del lado cliente en UIAutomationClientsideProviders. dll. Este ensamblado se registra automáticamente para su uso con aplicaciones de cliente de automatización de la interfaz de usuario.  
  
 Normalmente Windows Forms, los controles que son contenedores administrados [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] para controles comunes son compatibles [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]con. Se admiten los siguientes controles.  
  
|Nombre de la clase|  
|----------------|  
|Botón|  
|CheckBox|  
|CheckedListBox|  
|ColorDialog|  
|ComboBox|  
|FolderBrowser|  
|FontDialog|  
|GroupBox|  
|HScrollBar|  
|ImageList|  
|Etiqueta|  
|ListBox|  
|ListView|  
|MainMenu/ContextMenu|  
|MonthCalendar|  
|NotifyIcon|  
|OpenFileDialog|  
|PageSetupDialog|  
|PrintDialog|  
|ProgressBar|  
|RadioButton|  
|RichTextBox|  
|SaveFileDialog|  
|ScrollableControl|  
|SoundPlayer|  
|StatusBar|  
|TabControl/TabPage|  
|TextBox|  
|Temporizador|  
|ToolBar|  
|Información sobre herramientas|  
|Trackbar|  
|TreeView|  
|VscrollBar|  
|ExploradorWeb|  
  
 Los siguientes controles se exponen a [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] solo a través de la compatibilidad de Microsoft Active Accessibility. Es posible que algunas funciones no estén disponibles.  
  
|Nombre del control|  
|------------------|  
|BindingSource|  
|DataGrid|  
|DataGridView|  
|DataNavigator|  
|DomainUpDown|  
|ErrorProvider|  
|FlowLayoutPanel|  
|Form|  
|LinkLabel|  
|HelpProvider|  
|MaskedTextBox|  
|MenuStrip/ContextMenuStrip|  
|NumericUpDown|  
|Panel|  
|PictureBox|  
|PrintDocument|  
|PrintPreview-Control|  
|PrintPreview-Dialog|  
|PropertyGrid|  
|Control de usuario|  
|ToolStrip|  
|TableLayoutPanel|  
|SplitContainer/SplitterPanel|  
|Divisor|  
|RaftingContainer|  
|StatusStrip|  
  
## <a name="see-also"></a>Vea también

- [Tipos de control de Automatización de la interfaz de usuario](ui-automation-control-types.md)

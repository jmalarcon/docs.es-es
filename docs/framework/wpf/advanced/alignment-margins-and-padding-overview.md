---
title: Información general sobre alineación, márgenes y relleno
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- margins [WPF]
- padding [WPF]
- aligning [WPF]
ms.assetid: 9c6a2009-9b86-4e40-8605-0a2664dc3973
ms.openlocfilehash: bf351b6df972dc992f214ddfe899bfa808d0cd53
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963633"
---
# <a name="alignment-margins-and-padding-overview"></a>Información general sobre alineación, márgenes y relleno
La <xref:System.Windows.FrameworkElement> clase expone varias propiedades que se usan para colocar de forma precisa los elementos secundarios. En este tema se tratan cuatro de las propiedades más importantes <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>: <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A>, y <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>. Es importante comprender los efectos de estas propiedades, ya que proporcionan la base para controlar la posición de los elementos de las aplicaciones de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  

<a name="wcpsdk_layout_amp_introduction"></a>   
## <a name="introduction-to-element-positioning"></a>Introducción al posicionamiento de elementos  
 Existen numerosas maneras de posicionar elementos mediante [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Sin embargo, conseguir un diseño idóneo va más allá de <xref:System.Windows.Controls.Panel> simplemente elegir el elemento correcto. El control preciso de la posición requiere un conocimiento <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>de <xref:System.Windows.FrameworkElement.Margin%2A>las <xref:System.Windows.Controls.Border.Padding%2A>propiedades, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> , y.  
  
 La siguiente ilustración muestra un escenario de diseño que usa varias propiedades de posicionamiento.  
  
 ![Ejemplo de propiedades de posicionamiento de WPF](./media/layout-margins-padding-alignment-graphic1.PNG "layout_margins_padding_alignment_graphic1")  
  
 A primera vista, los <xref:System.Windows.Controls.Button> elementos de esta ilustración pueden parecer colocados de forma aleatoria. Sin embargo, sus posiciones se controlan realmente de forma precisa mediante una combinación de márgenes, alineaciones y relleno.  
  
 En el ejemplo siguiente se describe cómo crear el diseño de la ilustración anterior. Un <xref:System.Windows.Controls.Border> elemento encapsula un elemento primario <xref:System.Windows.Controls.StackPanel>, con un <xref:System.Windows.Controls.Border.Padding%2A> valor de 15 píxeles independientes del dispositivo. Esta cuenta para la banda <xref:System.Windows.Media.Brushes.LightBlue%2A> estrecha que rodea al elemento secundario <xref:System.Windows.Controls.StackPanel>. Los elementos secundarios de <xref:System.Windows.Controls.StackPanel> se usan para ilustrar cada una de las distintas propiedades de posicionamiento que se detallan en este tema. Se <xref:System.Windows.Controls.Button> usan tres elementos para mostrar las <xref:System.Windows.FrameworkElement.Margin%2A> propiedades y <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> .  
  
 [!code-csharp[MPALayoutSampleIntro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutSampleIntro/CSharp/MPA_Layout_Sample_Intro.cs#1)]
 [!code-vb[MPALayoutSampleIntro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutSampleIntro/VisualBasic/MPALayoutIntro.vb#1)]  
  
 En el siguiente diagrama se proporciona una vista de primer plano de las distintas propiedades de posicionamiento que se usan en el ejemplo anterior. En las siguientes secciones de este tema se describe con más detalle cómo usar cada propiedad de posicionamiento.  
  
 ![Propiedades de posicionamiento con llamadas de pantalla](./media/layout-margins-padding-alignment-graphic2.PNG "layout_margins_padding_alignment_graphic2")  
  
<a name="wcpsdk_layout_amp_alignment_properties"></a>   
## <a name="understanding-alignment-properties"></a>Explicación de las propiedades Alignment  
 Las <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propiedades <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> y describen cómo se debe colocar un elemento secundario dentro del espacio de diseño asignado de un elemento primario. Al usar estas propiedades juntas, puede posicionar los elementos secundarios con precisión. Por ejemplo, los elementos secundarios de <xref:System.Windows.Controls.DockPanel> pueden especificar cuatro alineaciones horizontales diferentes <xref:System.Windows.HorizontalAlignment.Left>: <xref:System.Windows.HorizontalAlignment.Right>, o <xref:System.Windows.HorizontalAlignment.Center>, o para <xref:System.Windows.HorizontalAlignment.Stretch> rellenar el espacio disponible. Para el posicionamiento vertical existen valores similares.  
  
> [!NOTE]
> Las propiedades y <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Width%2A> establecidas explícitamente en un elemento tienen prioridad sobre <xref:System.Windows.HorizontalAlignment.Stretch> el valor de la propiedad. <xref:System.Windows.FrameworkElement.Height%2A>Al intentar establecer, y <xref:System.Windows.FrameworkElement.Width%2A>un <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> valor de `Stretch` , se omite la `Stretch` solicitud.  
  
<a name="wcpsdk_layout_amp_horizontalalignment_properties"></a>   
### <a name="horizontalalignment-property"></a>Propiedad HorizontalAlignment  
 La <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propiedad declara las características de la alineación horizontal que se van a aplicar a los elementos secundarios. En la tabla siguiente se muestra cada uno de los valores <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> posibles de la propiedad.  
  
|Member|DESCRIPCIÓN|  
|------------|-----------------|  
|<xref:System.Windows.HorizontalAlignment.Left>|Los elementos secundarios se alinean a la izquierda del espacio de diseño asignado del elemento primario.|  
|<xref:System.Windows.HorizontalAlignment.Center>|Los elementos secundarios se alinean en el centro del espacio de diseño asignado del elemento primario.|  
|<xref:System.Windows.HorizontalAlignment.Right>|Los elementos secundarios se alinean a la derecha del espacio de diseño asignado del elemento primario.|  
|<xref:System.Windows.HorizontalAlignment.Stretch>Predeterminada|Los elementos secundarios se ajustan para rellenar el espacio de diseño asignado del elemento primario. Los <xref:System.Windows.FrameworkElement.Width%2A> valores <xref:System.Windows.FrameworkElement.Height%2A> explícitos y tienen prioridad.|  
  
 En el ejemplo siguiente se muestra cómo aplicar <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> la propiedad <xref:System.Windows.Controls.Button> a los elementos. Se muestran todos los valores de atributo para ilustrar mejor los distintos comportamientos de representación.  
  
 [!code-csharp[MPALayoutHorizontalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/CSharp/MPA_Layout_HorizontalAlignment.cs#2)]
 [!code-vb[MPALayoutHorizontalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/VisualBasic/MPA_Layout_HorizontalAlignment.vb#2)]  
  
 El código anterior produce un diseño similar al de la siguiente imagen. Los efectos de posicionamiento de <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> cada valor están visibles en la ilustración.  
  
 ![Ejemplo HorizontalAlignment](./media/layout-horizontal-alignment-graphic.PNG "layout_horizontal_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_verticalalignment_properties"></a>   
### <a name="verticalalignment-property"></a>Propiedad VerticalAlignment  
 La <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> propiedad describe las características de alineación vertical que se van a aplicar a los elementos secundarios. En la tabla siguiente se muestra cada uno de los valores <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> posibles de la propiedad.  
  
|Member|DESCRIPCIÓN|  
|------------|-----------------|  
|<xref:System.Windows.VerticalAlignment.Top>|Los elementos secundarios se alinean en la parte superior del espacio de diseño asignado del elemento primario.|  
|<xref:System.Windows.VerticalAlignment.Center>|Los elementos secundarios se alinean en el centro del espacio de diseño asignado del elemento primario.|  
|<xref:System.Windows.VerticalAlignment.Bottom>|Los elementos secundarios se alinean en la parte inferior del espacio de diseño asignado del elemento primario.|  
|<xref:System.Windows.VerticalAlignment.Stretch>Predeterminada|Los elementos secundarios se ajustan para rellenar el espacio de diseño asignado del elemento primario. Los <xref:System.Windows.FrameworkElement.Width%2A> valores <xref:System.Windows.FrameworkElement.Height%2A> explícitos y tienen prioridad.|  
  
 En el ejemplo siguiente se muestra cómo aplicar <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> la propiedad <xref:System.Windows.Controls.Button> a los elementos. Se muestran todos los valores de atributo para ilustrar mejor los distintos comportamientos de representación. Para los fines de este ejemplo, <xref:System.Windows.Controls.Grid> se usa un elemento con líneas de cuadrícula visibles como elemento primario para ilustrar mejor el comportamiento de diseño de cada valor de propiedad.  
  
 [!code-csharp[MPALayoutVerticalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutVerticalAlignment/CSharp/MPA_Layout_VerticalAlignment.cs#2)]
 [!code-vb[MPALayoutVerticalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutVerticalAlignment/VisualBasic/MPA_Layout_VerticalAlignment.vb#2)]
 [!code-xaml[MPALayoutVerticalAlignment#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MPALayoutVerticalAlignment/XAML/default.xaml#2)]  
  
 El código anterior produce un diseño similar al de la siguiente imagen. Los efectos de posicionamiento de <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> cada valor están visibles en la ilustración.  
  
 ![Ejemplo de propiedad VerticalAlignment](./media/layout-vertical-alignment-graphic.PNG "layout_vertical_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_margin_properties"></a>   
## <a name="understanding-margin-properties"></a>Explicación de las propiedades Margin  
 La <xref:System.Windows.FrameworkElement.Margin%2A> propiedad describe la distancia entre un elemento y sus elementos secundarios o del mismo nivel. <xref:System.Windows.FrameworkElement.Margin%2A>los valores pueden ser uniformes, mediante una sintaxis `Margin="20"`como. Con esta sintaxis, se aplicaría un uniforme <xref:System.Windows.FrameworkElement.Margin%2A> de 20 píxeles independientes del dispositivo al elemento. <xref:System.Windows.FrameworkElement.Margin%2A>los valores también pueden adoptar la forma de cuatro valores distintos, cada uno de los cuales describe un margen distinto para aplicar a la izquierda, superior, derecha e inferior (en ese orden) `Margin="0,10,5,25"`, como. El uso correcto de <xref:System.Windows.FrameworkElement.Margin%2A> la propiedad permite un control muy exhaustivo de la posición de representación de un elemento y la posición de representación de sus elementos vecinos y secundarios.  
  
> [!NOTE]
> Un margen distinto de cero aplica espacio fuera del y <xref:System.Windows.FrameworkElement.ActualWidth%2A> <xref:System.Windows.FrameworkElement.ActualHeight%2A>del elemento.  
  
 En el ejemplo siguiente se muestra cómo aplicar márgenes uniformes alrededor de un <xref:System.Windows.Controls.Button> grupo de elementos. Los <xref:System.Windows.Controls.Button> elementos se espacian uniformemente con un búfer de margen de diez píxeles en cada dirección.  
  
 [!code-cpp[MarginPaddingAlignmentSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#1)]
 [!code-csharp[MarginPaddingAlignmentSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#1)]
 [!code-vb[MarginPaddingAlignmentSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#1)]
 [!code-xaml[MarginPaddingAlignmentSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#1)]  
  
 En muchos casos, un margen uniforme no resulta apropiado. En estos casos, se puede aplicar un espaciado no uniforme. En el ejemplo siguiente se muestra cómo aplicar un espaciado de margen no uniforme a los elementos secundarios. Los márgenes se describen en este orden: izquierdo, superior, derecho e inferior.  
  
 [!code-cpp[MarginPaddingAlignmentSample#2](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#2)]
 [!code-csharp[MarginPaddingAlignmentSample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#2)]
 [!code-vb[MarginPaddingAlignmentSample#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#2)]
 [!code-xaml[MarginPaddingAlignmentSample#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#2)]  
  
<a name="wcpsdk_layout_amp_padding_properties"></a>   
## <a name="understanding-the-padding-property"></a>Descripción de la propiedad Padding  
 El relleno es similar <xref:System.Windows.FrameworkElement.Margin%2A> a en la mayoría de los aspectos. La propiedad padding solo se expone en algunas clases, principalmente por comodidad <xref:System.Windows.Documents.Block>:, <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Control>y <xref:System.Windows.Controls.TextBlock> son ejemplos de clases que exponen una propiedad padding. La <xref:System.Windows.Controls.Border.Padding%2A> propiedad amplía el tamaño efectivo de un elemento secundario por el valor especificado <xref:System.Windows.Thickness> .  
  
 En el ejemplo siguiente se muestra cómo <xref:System.Windows.Controls.Border.Padding%2A> aplicar a un <xref:System.Windows.Controls.Border> elemento primario.  
  
 [!code-cpp[MarginPaddingAlignmentSample#3](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#3)]
 [!code-csharp[MarginPaddingAlignmentSample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#3)]
 [!code-vb[MarginPaddingAlignmentSample#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#3)]
 [!code-xaml[MarginPaddingAlignmentSample#3](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#3)]  
  
<a name="wcpsdk_layout_amp_summary"></a>   
## <a name="using-alignment-margins-and-padding-in-an-application"></a>Uso de las propiedades Alignment, Margin y Padding en una aplicación  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A> [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]y proporcionanelcontroldeposicionamientonecesarioparacrearuncomplejo.<xref:System.Windows.FrameworkElement.VerticalAlignment%2A> Puede usar los efectos de cada propiedad para cambiar el posicionamiento de los elementos secundarios, lo que ofrece flexibilidad en la creación de aplicaciones dinámicas y experiencias de usuario.  
  
 En el ejemplo siguiente se muestra cada uno de los conceptos que se detallan en este tema. Al basarse en la infraestructura que se encuentra en el primer ejemplo de este tema, <xref:System.Windows.Controls.Grid> en este ejemplo se agrega un <xref:System.Windows.Controls.Border> elemento como elemento secundario de en el primer ejemplo. <xref:System.Windows.Controls.Border.Padding%2A>se aplica al elemento primario <xref:System.Windows.Controls.Border> . Se <xref:System.Windows.Controls.Grid> utiliza para particionar el espacio entre tres <xref:System.Windows.Controls.StackPanel> elementos secundarios. <xref:System.Windows.Controls.Button>los elementos se usan de nuevo para mostrar los distintos <xref:System.Windows.FrameworkElement.Margin%2A> efectos <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>de y. <xref:System.Windows.Controls.TextBlock>los elementos se agregan <xref:System.Windows.Controls.ColumnDefinition> a cada una de ellas para definir mejor las <xref:System.Windows.Controls.Button> distintas propiedades que se aplican a los elementos de cada columna.  
  
 [!code-cpp[MarginPaddingAlignmentSample#4](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#4)]
 [!code-csharp[MarginPaddingAlignmentSample#4](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#4)]
 [!code-vb[MarginPaddingAlignmentSample#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#4)]
 [!code-xaml[MarginPaddingAlignmentSample#4](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#4)]  
  
 Cuando se compila, la aplicación anterior produce una [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] similar a la de la siguiente ilustración. Los efectos de los distintos valores de propiedad son evidentes en el espaciado entre los elementos, y los valores de propiedad significativos de los elementos <xref:System.Windows.Controls.TextBlock> de cada columna se muestran dentro de los elementos.  
  
 ![Varias propiedades de posicionamiento en una aplicación](./media/layout-margins-padding-aligment-graphic3.PNG "layout_margins_padding_aligment_graphic3")  
  
<a name="wcpsdk_layout_amp_alignment_whatsnext"></a>   
## <a name="whats-next"></a>Pasos adicionales  
 La colocación de las propiedades <xref:System.Windows.FrameworkElement> definidas por la clase permite un control preciso [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de la ubicación de los elementos en las aplicaciones. Ahora dispone de varias técnicas que puede usar para posicionar mejor los elementos mediante [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Existen recursos adicionales que explican el diseño de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] con mayor detalle. El tema [información general](../controls/panels-overview.md) de los paneles contiene más detalles <xref:System.Windows.Controls.Panel> sobre los distintos elementos. El tema [Tutorial: Mi primera aplicación](../getting-started/walkthrough-my-first-wpf-desktop-application.md) de escritorio de WPF presenta técnicas avanzadas que usan elementos de diseño para colocar componentes y enlazar sus acciones a los orígenes de datos.  
  
## <a name="see-also"></a>Vea también

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- <xref:System.Windows.FrameworkElement.Margin%2A>
- [Información general sobre elementos Panel](../controls/panels-overview.md)
- [Diseño](layout.md)
- [Ejemplo WPF Layout Gallery](https://go.microsoft.com/fwlink/?LinkID=160054)

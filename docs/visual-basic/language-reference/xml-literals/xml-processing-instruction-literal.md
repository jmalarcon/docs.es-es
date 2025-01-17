---
title: Literal de instrucción de procesamiento XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
ms.openlocfilehash: c589d3f4ac6bbb9aa9b2b8f2535888bddbf9c934
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958481"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a>Literal de instrucción de procesamiento XML (Visual Basic)
Literal que representa un <xref:System.Xml.Linq.XProcessingInstruction> objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a>Elementos  
 `<?`  
 Necesario. Denota el inicio del literal de instrucción de procesamiento XML.  
  
 `piName`  
 Necesario. Nombre que indica la aplicación a la que se destina la instrucción de procesamiento. No puede comenzar por "XML" o "XML".  
  
 `piData`  
 Opcional. Cadena que indica cómo la aplicación de `piName` destino debe procesar el documento XML.  
  
 `?>`  
 Necesario. Denota el final de la instrucción de procesamiento.  
  
## <a name="return-value"></a>Valor devuelto  
 Un objeto <xref:System.Xml.Linq.XProcessingInstruction>.  
  
## <a name="remarks"></a>Comentarios  
 Los literales de instrucciones de procesamiento XML indican cómo deben procesar las aplicaciones un documento XML. Cuando una aplicación carga un documento XML, la aplicación puede comprobar las instrucciones de procesamiento XML para determinar cómo procesar el documento. La aplicación interpreta el significado de `piName` y. `piData`  
  
 El literal de documento XML utiliza una sintaxis similar a la de la instrucción de procesamiento XML. Para obtener más información, vea [literal de documento XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
> [!NOTE]
> El `piName` elemento no puede comenzar con las cadenas "XML" o "XML", ya que la especificación XML 1,0 reserva esos identificadores.  
  
 Puede asignar un literal de instrucción de procesamiento XML a una variable o incluirlo en un literal de documento XML.  
  
> [!NOTE]
> Un literal XML puede abarcar varias líneas sin necesidad de caracteres de continuación de línea. Esto le permite copiar contenido de un documento XML y pegarlo directamente en un programa de Visual Basic.  
  
 El compilador Visual Basic convierte el literal de instrucción de procesamiento XML en una <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> llamada al constructor.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se crea una instrucción de procesamiento que identifica una hoja de estilos para un documento XML.  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a>Vea también

- <xref:System.Xml.Linq.XProcessingInstruction>
- [Literal de documento XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [Literales XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Crear XML en Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)

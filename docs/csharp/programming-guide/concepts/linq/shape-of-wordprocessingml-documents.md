---
title: Forma de documentos WordprocessingML (C#)
ms.date: 07/20/2015
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
ms.openlocfilehash: 84d893267c37ecf99a457ebb683d0451e2b4b68f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591054"
---
# <a name="shape-of-wordprocessingml-documents-c"></a>Forma de documentos WordprocessingML (C#)
En este tema se presenta la forma XML de un documento WordprocessingML.  
  
## <a name="microsoft-office-formats"></a>Formatos de Microsoft Office  
 El formato de archivo nativo para el sistema Microsoft Office 2007 es XML abierto de Office (comúnmente denominado XML abierto). XML abierto es un formato basado en XML que sigue la norma Ecma y que actualmente está sometido al proceso de estándares ISO-IEC. El lenguaje de marcado para los archivos de procesamiento de texto en XML abierto se denomina WordprocessingML. Este tutorial usa los archivos de origen WordprocessingML como datos para los ejemplos.  
  
 Si está utilizando Microsoft Office 2003, puede guardar documentos en el formato XML abierto de Office si ha instalado el Paquete de compatibilidad de Microsoft Office para los formatos de archivo Word, Excel y PowerPoint 2007.  
  
## <a name="the-shape-of-wordprocessingml-documents"></a>Forma de los documentos WordprocessingML  
 Lo primero que hay que comprender es la forma de los documentos WordprocessingML. Un documento WordprocessingML contiene un elemento de Body (con el nombre `w:body`) que contiene los párrafos del documento. Cada párrafo contiene una o más ejecuciones de texto (denominadas `w:r`). Cada ejecución de texto contiene uno o más fragmentos de texto (con el nombre `w:t`).  
  
 A continuación se muestra un documento WordprocessingML muy sencillo:  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<w:document  
xmlns:ve="http://schemas.openxmlformats.org/markup-compatibility/2006"  
xmlns:o="urn:schemas-microsoft-com:office:office"  
xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"  
xmlns:m="http://schemas.openxmlformats.org/officeDocument/2006/math"  
xmlns:v="urn:schemas-microsoft-com:vml"  
xmlns:wp="http://schemas.openxmlformats.org/drawingml/2006/wordprocessingDrawing"  
xmlns:w10="urn:schemas-microsoft-com:office:word"  
xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
xmlns:wne="http://schemas.microsoft.com/office/word/2006/wordml">  
  <w:body>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is a paragraph.</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is another paragraph.</w:t>  
      </w:r>  
    </w:p>  
  </w:body>  
</w:document>  
```  
  
 Este documento contiene dos párrafos. Contienen una ejecución de texto única y cada ejecución de texto contiene un solo fragmento de texto.  
  
 La forma más sencilla de ver el contenido de un documento WordprocessingML en forma XML es crear un documento mediante Microsoft Word, guardarlo y después ejecutar el siguiente programa que muestra XML en la consola.  
  
 Este ejemplo utiliza las clases que se encuentran en el ensamblado WindowsBase. Utiliza los tipos del espacio de nombres <xref:System.IO.Packaging?displayProperty=nameWithType>.  
  
```csharp  
const string documentRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string wordmlNamespace =  
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
using (Package wdPackage = Package.Open("SampleDoc.docx", FileMode.Open, FileAccess.Read))  
{  
    PackageRelationship relationship =  
        wdPackage  
        .GetRelationshipsByType(documentRelationshipType)  
        .FirstOrDefault();  
    if (relationship != null)  
    {  
        Uri documentUri =  
            PackUriHelper.ResolvePartUri(  
                new Uri("/", UriKind.Relative),  
                relationship.TargetUri);  
        PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
        //  Get the officeDocument part from the package.  
        //  Load the XML in the part into an XDocument instance.  
        XDocument xdoc =  
            XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
        Console.WriteLine(xdoc.Root);  
    }  
}  
```  
  
## <a name="external-resources"></a>Recursos externos  
 [Introducción a los formatos de archivo Office (2007) Open XML](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205%28v=office.12%29)  
 [Información general de WordprocessingML](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812%28v=office.11%29)  
 [Anatomía de un archivo WordProcessingML](http://officeopenxml.com/anatomyofOOXML.php)  
 [Introducción a WordprocessingML](https://ericwhite.com/blog/introduction-to-wordprocessingml-series/)  
 [Office 2003: página de descarga de esquemas de referencia XML](https://www.microsoft.com/download/details.aspx?id=101)  
  
## <a name="see-also"></a>Vea también

- [Tutorial: Manipulación de contenido en un documento WordprocessingML (C#)](./shape-of-wordprocessingml-documents.md)

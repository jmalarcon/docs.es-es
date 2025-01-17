---
title: 'Cómo: proyectar un tipo anónimo (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 30b42987-0e0e-4b2b-adb1-5255ddfbcd7b
ms.openlocfilehash: 9a4498913cdcff0f813f184be18816e4dc5179b1
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321498"
---
# <a name="how-to-project-an-anonymous-type-visual-basic"></a>Cómo: proyectar un tipo anónimo (Visual Basic)
En algunos casos quizás desee proyectar una consulta a un nuevo tipo, aunque sepa que solo utilizará este tipo durante un breve período. Crear un nuevo tipo solamente para usarlo en la proyección conlleva mucho trabajo adicional. En este caso un enfoque más eficiente consiste en proyectar en un tipo anónimo. Los tipos anónimos permiten definir una clase y, a continuación, declarar e inicializar un objeto de esa clase, sin dar un nombre a la clase.  
  
 Los tipos anónimos son la implementación de C# del concepto matemático de *tupla*. El término matemático tupla se originó de la secuencia único, doble, triple, cuádruple, quíntuple, n-tuple. Se refiere a una secuencia finita de objetos, cada uno de un tipo específico. A veces se denomina una lista de pares nombre/valor. Por ejemplo, el contenido de una dirección en el documento XML [Archivo XML de ejemplo: Pedido de compra común (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md) se podría expresar de la siguiente manera:  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 Cuando se crea una instancia de un tipo anónimo, resulta práctico pensar en ella como si se creara una tupla de orden n. Si escribe una consulta que crea una tupla en la cláusula `Select`, la consulta devuelve un `IEnumerable` de la tupla.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, la cláusula `Select` proyecta un tipo anónimo. A continuación, el ejemplo utiliza `Dim` para crear el objeto `IEnumerable`. En el bucle `For Each`, la variable de iteración se convierte en una instancia del tipo anónimo creado en la expresión de consulta.  
  
 En este ejemplo se usa el siguiente documento XML: [Archivo XML de muestra: clientes y pedidos (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
```vb  
Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")  
Dim custList = _  
    From el In custOrd.<Customers>.<Customer> _  
    Select New With { _  
        .CustomerID = el.@<CustomerID>, _  
        .CompanyName = el.<CompanyName>.Value, _  
        .ContactName = el.<ContactName>.Value _  
    }  
For Each cust In custList  
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName)  
Next  
```  
  
 Este código genera el siguiente resultado:  
  
```console  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a>Vea también

- [Proyecciones y transformaciones (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)

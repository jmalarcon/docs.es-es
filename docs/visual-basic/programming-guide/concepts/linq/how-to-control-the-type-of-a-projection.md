---
title: Procedimiento Controlar el tipo de una proyección (Visual Basic)
ms.date: 07/20/2015
ms.assetid: a0171276-0b46-4817-aee5-a8d5191b12fe
ms.openlocfilehash: 8ec53d1f8e0ae4957857d4b71fddd05205dee6b5
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351746"
---
# <a name="how-to-control-the-type-of-a-projection-visual-basic"></a>Procedimiento Controlar el tipo de una proyección (Visual Basic)
La proyección es el proceso de tomar un conjunto de datos, filtrarlo, cambiar su forma e incluso cambiar su tipo. La mayoría de las expresiones de consulta realizan proyecciones. La mayor parte de las expresiones de consulta de esta sección se evalúan como <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>, aunque puede controlar el tipo de proyección para crear colecciones de otros tipos. En este tema se explica cómo hacerlo.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, se define un nuevo tipo, `Customer`. La expresión de consulta crea una instancia de nuevos objetos `Customer` en la cláusula `Select`. Esto hace que el tipo de la expresión de consulta sea <xref:System.Collections.Generic.IEnumerable%601> de `Customer`.  
  
 Este ejemplo utiliza el siguiente documento XML: [Archivo XML de ejemplo: Clientes y pedidos (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
```vb  
Public Class Customer  
    Private customerIDValue As String  
    Public Property CustomerID() As String  
        Get  
            Return customerIDValue  
        End Get  
        Set(ByVal value As String)  
            customerIDValue = value  
        End Set  
    End Property  
  
    Private companyNameValue As String  
    Public Property CompanyName() As String  
        Get  
            Return companyNameValue  
        End Get  
        Set(ByVal value As String)  
            companyNameValue = value  
        End Set  
    End Property  
  
    Private contactNameValue As String  
    Public Property ContactName() As String  
        Get  
            Return contactNameValue  
        End Get  
        Set(ByVal value As String)  
            contactNameValue = value  
        End Set  
    End Property  
  
    Public Sub New(ByVal customerID As String, _  
                   ByVal companyName As String, _  
                   ByVal contactName As String)  
        CustomerIDValue = customerID  
        CompanyNameValue = companyName  
        ContactNameValue = contactName  
    End Sub  
  
    Public Overrides Function ToString() As String  
        Return String.Format("{0}:{1}:{2}", Me.CustomerID, Me.CompanyName, Me.ContactName)  
    End Function  
End Class  
  
Sub Main()  
    Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")  
    Dim custList As IEnumerable(Of Customer) = _  
        From el In custOrd.<Customers>.<Customer> _  
        Select New Customer( _  
            el.@<CustomerID>, _  
            el.<CompanyName>.Value, _  
            el.<ContactName>.Value _  
        )  
    For Each cust In custList  
        Console.WriteLine(cust)  
    Next  
End Sub  
```  
  
 Este código genera el siguiente resultado:  
  
```console  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a>Vea también

- <xref:System.Linq.Enumerable.Select%2A>
- [Proyecciones y transformaciones (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)

---
title: Option Strict (instrucción) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Strict
- vb.OptionStrict
helpviewer_keywords:
- Strict keyword [Visual Basic]
- Option Strict statement [Visual Basic]
- conversions [Visual Basic], implicit
- late binding [Visual Basic]
- implicit conversions [Visual Basic]
ms.assetid: 5883e0c1-a920-4274-8e46-b0ff047eaee5
ms.openlocfilehash: 8b7dfcfa394ed2c45adec9661ee1ea5823435223
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775439"
---
# <a name="option-strict-statement"></a>Option Strict Statement
Restringe las conversiones de tipos de datos implícitos solo a las conversiones de ampliación, no permite el enlace en tiempo de ejecución y no permite los tipos implícitos que generan un tipo de `Object`.  
  
## <a name="syntax"></a>Sintaxis  
  
```vb  
Option Strict { On | Off }  
```  
  
## <a name="parts"></a>Elementos  
  
|Término|de esquema JSON|  
|---|---|  
|`On`|Opcional. Habilita la comprobación de `Option Strict`.|  
|`Off`|Opcional. Deshabilita la comprobación de `Option Strict`.|  
  
## <a name="remarks"></a>Comentarios  
 Cuando `Option Strict On` o `Option Strict` aparece en un archivo, las condiciones siguientes producen un error en tiempo de compilación:  
  
- Conversiones de restricción implícitas  
  
- Enlace en tiempo de ejecución  
  
- Tipos implícitos que dan como resultado un tipo `Object`  
  
> [!NOTE]
> En las configuraciones de advertencia que se pueden establecer en la [Página compilar, diseñador de proyectos (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), hay tres opciones de configuración que se corresponden con las tres condiciones que causan un error en tiempo de compilación. Para obtener información sobre cómo usar estos valores, vea [para establecer configuraciones de advertencia en el IDE](../../../visual-basic/language-reference/statements/option-strict-statement.md#conditions) más adelante en este tema.  
  
 La instrucción `Option Strict Off` desactiva la comprobación de errores y advertencias para las tres condiciones, incluso si la configuración de IDE asociada especifica que se activen estos errores o advertencias. La instrucción `Option Strict On` activa la comprobación de errores y advertencias para las tres condiciones, incluso si la configuración de IDE asociada especifica que se desactiven estos errores o advertencias.  
  
 Si se utiliza, la instrucción `Option Strict` debe aparecer antes que cualquier otra instrucción de código en un archivo.  
  
 Cuando se establece `Option Strict` en `On`, Visual Basic comprueba que los tipos de datos se especifican para todos los elementos de programación. Los tipos de datos se pueden especificar explícitamente o especificarse mediante la inferencia de tipo local. Se recomienda especificar los tipos de datos para todos los elementos de programación, por las razones siguientes:  
  
- Habilita la compatibilidad con IntelliSense para las variables y los parámetros. Esto le permite ver sus propiedades y otros miembros a medida que escribe código.  
  
- Permite que el compilador realice la comprobación de tipos. La comprobación de tipos le ayuda a encontrar instrucciones que pueden producir errores en tiempo de ejecución debido a errores de conversión de tipos. También identifica las llamadas a métodos en objetos que no admiten esos métodos.  
  
- Acelera la ejecución del código. Una razón para esto es que, si no se especifica un tipo de datos para un elemento de programación, el compilador Visual Basic le asigna el tipo de `Object`. Es posible que el código compilado tenga que realizar una conversión entre `Object` y otros tipos de datos, lo que reduce el rendimiento.  
  
## <a name="implicit-narrowing-conversion-errors"></a>Errores de conversión de restricción implícita  
 Los errores de conversión de restricción implícita se producen cuando existe una conversión de tipos de datos implícita que es una conversión de restricción.  
  
 Visual Basic puede convertir muchos tipos de datos en otros tipos de datos. La pérdida de datos puede producirse cuando el valor de un tipo de datos se convierte en un tipo de datos que tiene menos precisión o menor capacidad. Se produce un error en tiempo de ejecución si se produce un error en una conversión de restricción. `Option Strict` garantiza la notificación en tiempo de compilación de estas conversiones de restricción para que pueda evitarlas. Para obtener más información, vea [conversiones implícitas y explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) , y [conversiones de ampliación y de restricción](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 Entre las conversiones que pueden producir errores se incluyen las conversiones implícitas que se producen en expresiones. Para obtener más información, vea los temas siguientes:  
  
- [Operador +](../../../visual-basic/language-reference/operators/addition-operator.md)  
  
- [Operador +=](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
  
- [Operador (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
  
- [/= (Operador) (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
  
- [Char (tipo de datos)](../../../visual-basic/language-reference/data-types/char-data-type.md)  
  
 Al concatenar cadenas mediante el [operador &](../../../visual-basic/language-reference/operators/concatenation-operator.md), se considera que todas las conversiones de las cadenas son de ampliación. Por lo tanto, estas conversiones no generan un error de conversión de restricción implícita, aun cuando `Option Strict` esté activada.  
  
 Cuando se llama a un método que tiene un argumento que tiene un tipo de datos diferente del parámetro correspondiente, una conversión de restricción produce un error en tiempo de compilación si `Option Strict` está activado. Puede evitar el error en tiempo de compilación mediante una conversión de ampliación o una conversión explícita.  
  
 Los errores de conversión de restricción implícita se suprimen en tiempo de compilación para las conversiones de los elementos de una colección de `For Each…Next` a la variable de control de bucle. Esto sucede incluso si `Option Strict` está activada. Para obtener más información, vea la sección acerca de las conversiones de restricción en [for each... Instrucción siguiente](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
## <a name="late-binding-errors"></a>Errores de enlace en tiempo de ejecución  
 Un objeto se enlaza en tiempo de ejecución cuando se asigna a una propiedad o un método de una variable que se declara como variable de tipo `Object`. Para obtener más información, vea [enlace anticipado y en tiempo de ejecución](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).  
  
## <a name="implicit-object-type-errors"></a>Errores de tipo de objeto implícito  
 Los errores de tipo de objeto implícito se producen cuando no se puede inferir un tipo adecuado para una variable declarada, por lo que se infiere un tipo de `Object`. Esto se produce principalmente cuando se usa una instrucción `Dim` para declarar una variable sin usar una cláusula `As` y `Option Infer` está desactivado. Para obtener más información, vea la [instrucción Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) y la [especificación del lenguaje Visual Basic](../../../visual-basic/reference/language-specification/index.md).  
  
 En el caso de los parámetros de método, la cláusula `As` es opcional si `Option Strict` está en OFF. Sin embargo, si cualquiera de los parámetros utiliza una cláusula `As`, todos deben usarlo. Si `Option Strict` está activada, se requiere la cláusula `As` para cada definición de parámetro.  
  
 Si declara una variable sin usar una cláusula `As` y la establece en `Nothing`, la variable tiene un tipo de `Object`. En este caso, no se produce ningún error en tiempo de compilación cuando `Option Strict` está activada y `Option Infer` está activada. Un ejemplo de esto es `Dim something = Nothing`.  
  
### <a name="default-data-types-and-values"></a>Tipos de datos y valores predeterminados  
 En la tabla siguiente se describen los resultados de diversas combinaciones de especificar el tipo de datos y el inicializador en una [instrucción Dim](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
|¿Tipo de datos especificado?|¿Inicializador especificado?|Ejemplo|Resultado|  
|---|---|---|---|  
|No|No|`Dim qty`|Si `Option Strict` está desactivado (valor predeterminado), la variable se establece en `Nothing`.<br /><br /> Si `Option Strict` está activado, se produce un error en tiempo de compilación.|  
|No|Sí|`Dim qty = 5`|Si `Option Infer` está activado (valor predeterminado), la variable toma el tipo de datos del inicializador. Vea [inferencia de tipo de local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Si `Option Infer` está desactivado y `Option Strict` está desactivado, la variable toma el tipo de datos de `Object`.<br /><br /> Si `Option Infer` está desactivado y `Option Strict` está activado, se produce un error en tiempo de compilación.|  
|Sí|No|`Dim qty As Integer`|La variable se inicializa con el valor predeterminado del tipo de datos. Para obtener más información, vea [Dim (instrucción](../../../visual-basic/language-reference/statements/dim-statement.md)).|  
|Sí|Sí|`Dim qty  As Integer = 5`|Si el tipo de datos del inicializador no es convertible al tipo de datos especificado, se produce un error en tiempo de compilación.|  
  
## <a name="when-an-option-strict-statement-is-not-present"></a>Cuando una instrucción Option Strict no está presente  
 Si el código fuente no contiene una instrucción `Option Strict`, se usa el valor **Option Strict** en la [Página compilar, el diseñador de proyectos (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) . La **Página compilar** tiene valores que proporcionan un control adicional sobre las condiciones que generan un error.  
  
 Si usa el compilador de línea de comandos, puede usar la opción del compilador [-OptionStrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) para especificar un valor para `Option Strict`.  
  
### <a name="to-set-option-strict-in-the-ide"></a>Para establecer Option Strict en el IDE  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
1. En el **Explorador de soluciones**, seleccione un proyecto. En el menú **Proyecto**, haga clic en **Propiedades**.  
  
2. En la pestaña **compilar** , establezca el valor en el cuadro **Option Strict** .  
  
### <a name="conditions"></a>Para establecer configuraciones de advertencia en el IDE  
 Cuando use la [Página compilar, el diseñador de proyectos (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) en lugar de una instrucción `Option Strict`, tendrá un control adicional sobre las condiciones que generan errores. La sección **configuraciones de advertencia** de la **Página compilar** tiene valores de configuración que corresponden a las tres condiciones que causan un error en tiempo de compilación cuando `Option Strict` está activada. Estas opciones son las siguientes:  
  
- **Conversión implícita**  
  
- **Enlace en tiempo de ejecución; la llamada podría generar un error en tiempo de ejecución**  
  
- **Tipo implícito; se supone el objeto**  
  
 Al establecer **Option Strict** en **On**, estos tres valores de configuración de advertencias se establecen en **Error**. Al establecer **Option Strict** en **Off**, las tres opciones se establecen en **None**.  
  
 Puede cambiar individualmente cada valor de configuración de advertencia por **None**, **Warning** o **Error**. Si se establecen las tres opciones de configuración de advertencia en **Error**, `On` aparece en el cuadro `Option strict`. Si se establecen las tres en **None**, `Off` aparece en este cuadro. Para cualquier otra combinación de estas opciones, aparece **(personalizado)** .  
  
### <a name="to-set-the-option-strict-default-setting-for-new-projects"></a>Para establecer la configuración predeterminada de Option Strict para los nuevos proyectos  
 Al crear un proyecto, el valor **Option Strict** de la pestaña **compilar** se establece en el valor **Option Strict** del cuadro de diálogo **Opciones** .  
  
 Para establecer `Option Strict` en este cuadro de diálogo, en el menú **herramientas** , haga clic en **Opciones**. En el cuadro de diálogo **Opciones**, expanda **Proyectos y soluciones** y, después, haga clic en **Valores predeterminados de VB**. La configuración predeterminada inicial en los **valores predeterminados de VB** es `Off`.  
  
### <a name="to-set-option-strict-on-the-command-line"></a>Para establecer Option Strict en la línea de comandos  
 Incluya la opción del compilador [-OptionStrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) en el comando **VBC** .  
  
## <a name="example"></a>Ejemplo  
 En los siguientes ejemplos se muestran errores en tiempo de compilación causados por conversiones de tipo implícitas que son conversiones de restricción. Esta categoría de errores corresponde a la condición de **conversión implícita** en la **Página compilar**.  
  
 [!code-vb[VbVbalrStatements#161](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#161)]  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un error en tiempo de compilación causado por el enlace en tiempo de ejecución. Esta categoría de errores corresponde al enlace en tiempo de **ejecución; la llamada podría producir un error en** la condición de tiempo de ejecución en la **Página de compilación**.  
  
 [!code-vb[VbVbalrStatements#162](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#162)]  
  
## <a name="example"></a>Ejemplo  
 En los siguientes ejemplos se muestran errores causados por variables declaradas con un tipo implícito de `Object`. Esta categoría de errores corresponde al **tipo implícito; se supone** que el objeto es una condición en la **Página de compilación**.  
  
 [!code-vb[VbVbalrStatements#163](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#163)]  
  
 [!code-vb[VbVbalrStatements#164](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#164)]  
  
## <a name="see-also"></a>Vea también

- [Conversiones de ampliación y de restricción](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Conversiones implícitas y explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Página Compilación, Diseñador de proyectos (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [Option Explicit (instrucción)](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Funciones de conversión de tipos](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Obtener acceso a los miembros de un objeto](../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [Expresiones incrustadas en XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Conversión de delegado flexible](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Enlace en tiempo de ejecución en las soluciones de Office](/visualstudio/vsto/late-binding-in-office-solutions)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [Valores predeterminados de Visual Basic, Proyectos, Cuadro de diálogo Opciones](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)

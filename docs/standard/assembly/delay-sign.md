---
title: Retraso de la firma de un ensamblado
ms.date: 08/19/2019
helpviewer_keywords:
- deferring assembly signing
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, delaying assembly signing
- partial assembly signing
ms.assetid: 9d300e17-5bf1-4360-97da-2aa55efd9070
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: e7679520e246ab3eda03e6f0e0d092c7d09f1845
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991320"
---
# <a name="delay-sign-an-assembly"></a><span data-ttu-id="b9ba0-102">Retraso de la firma de un ensamblado</span><span class="sxs-lookup"><span data-stu-id="b9ba0-102">Delay-sign an assembly</span></span>

<span data-ttu-id="b9ba0-103">Una organización podría tener un par de claves muy bien guardado al que los desarrolladores no pudieran acceder cada día.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-103">An organization can have a closely guarded key pair that developers can't access on a daily basis.</span></span> <span data-ttu-id="b9ba0-104">La clave pública suele estar disponible, pero el acceso a la clave privada estaría restringido a algunas personas.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-104">The public key is often available, but access to the private key is restricted to only a few individuals.</span></span> <span data-ttu-id="b9ba0-105">Al desarrollar ensamblados con nombres seguros, cada ensamblado que hace referencia al ensamblado de destino con nombre seguro contiene el token de la clave pública usada para asignar un nombre seguro al ensamblado de destino.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-105">When developing assemblies with strong names, each assembly that references the strong-named target assembly contains the token of the public key used to give the target assembly a strong name.</span></span> <span data-ttu-id="b9ba0-106">Esto requiere que la clave pública esté disponible durante el proceso de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-106">This requires that the public key be available during the development process.</span></span>

<span data-ttu-id="b9ba0-107">Puede usar la firma retardada o parcial en tiempo de compilación para reservar espacio en el archivo portable ejecutable (PE) para la firma de nombre seguro, pero retrase la firma real hasta una fase posterior, normalmente, justo antes de enviar el ensamblado.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-107">You can use delayed or partial signing at build time to reserve space in the portable executable (PE) file for the strong name signature, but defer the actual signing until some later stage, usually just before shipping the assembly.</span></span>

<span data-ttu-id="b9ba0-108">Para retrasar la firma de un ensamblado:</span><span class="sxs-lookup"><span data-stu-id="b9ba0-108">To delay-sign an assembly:</span></span>

1. <span data-ttu-id="b9ba0-109">Obtenga la parte de la clave pública del par de claves de la organización que se encargará de la firma.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-109">Get the public key portion of the key pair from the organization that will do the eventual signing.</span></span> <span data-ttu-id="b9ba0-110">Normalmente, esta clave tiene la forma de un archivo *.snk*, el cual se puede crear mediante la [herramienta de nombre seguro (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) proporcionada por Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-110">Typically this key is in the form of an *.snk* file, which can be created using the [Strong Name tool (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) provided by the Windows SDK.</span></span>

2. <span data-ttu-id="b9ba0-111">Se anota el código fuente del ensamblado con dos atributos personalizados de <xref:System.Reflection>:</span><span class="sxs-lookup"><span data-stu-id="b9ba0-111">Annotate the source code for the assembly with two custom attributes from <xref:System.Reflection>:</span></span>

   - <span data-ttu-id="b9ba0-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, que pasa el nombre del archivo que contiene la clave pública como parámetro a su constructor.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, which passes the name of the file containing the public key as a parameter to its constructor.</span></span>

   - <span data-ttu-id="b9ba0-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, que indica que se está retrasando la firma. Para ello, se pasa **true** como parámetro a su constructor.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, which indicates that delay signing is being used by passing **true** as a parameter to its constructor.</span></span>

   <span data-ttu-id="b9ba0-114">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="b9ba0-114">For example:</span></span>

   ```cpp
   [assembly:AssemblyKeyFileAttribute("myKey.snk")];
   [assembly:AssemblyDelaySignAttribute(true)];
   ```

   ```csharp
   [assembly:AssemblyKeyFileAttribute("myKey.snk")]
   [assembly:AssemblyDelaySignAttribute(true)]
   ```

   ```vb
   <Assembly:AssemblyKeyFileAttribute("myKey.snk")>
   <Assembly:AssemblyDelaySignAttribute(True)>
   ```

3. <span data-ttu-id="b9ba0-115">El compilador inserta la clave pública en el manifiesto del ensamblado y reserva espacio en el archivo PE para la firma de nombre seguro completo.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-115">The compiler inserts the public key into the assembly manifest and reserves space in the PE file for the full strong name signature.</span></span> <span data-ttu-id="b9ba0-116">La clave pública real se debe guardar mientras se compila el ensamblado para que otros ensamblados que hagan referencia a este puedan obtenerla y guardarla en su propia referencia al ensamblado.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-116">The real public key must be stored while the assembly is built so that other assemblies that reference this assembly can obtain the key to store in their own assembly reference.</span></span>

4. <span data-ttu-id="b9ba0-117">Dado que el ensamblado no tiene una firma de nombre seguro válida, la comprobación de firma debe estar desactivada.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-117">Because the assembly does not have a valid strong name signature, the verification of that signature must be turned off.</span></span> <span data-ttu-id="b9ba0-118">Puede hacerlo mediante la opción **–Vr** con la herramienta de nombre seguro.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-118">You can do this by using the **–Vr** option with the Strong Name tool.</span></span>

     <span data-ttu-id="b9ba0-119">En el ejemplo siguiente se desactiva la comprobación para un ensamblado denominado *myAssembly.dll*.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-119">The following example turns off verification for an assembly called *myAssembly.dll*.</span></span>

   ```console
   sn –Vr myAssembly.dll
   ```

   <span data-ttu-id="b9ba0-120">Para desactivar la comprobación en plataformas en las que no se puede ejecutar la herramienta de nombre seguro, como los microprocesadores de Advanced RISC Machine (ARM), use la opción **–Vk** para crear un archivo del Registro.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-120">To turn off verification on platforms where you can’t run the Strong Name tool, such as Advanced RISC Machine (ARM) microprocessors, use the **–Vk** option to create a registry file.</span></span> <span data-ttu-id="b9ba0-121">Importe el archivo del Registro en el Registro del equipo en el que quiere desactivar la comprobación.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-121">Import the registry file into the registry on the computer where you want to turn off verification.</span></span> <span data-ttu-id="b9ba0-122">En el ejemplo siguiente se crea un archivo del Registro para `myAssembly.dll`.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-122">The following example creates a registry file for `myAssembly.dll`.</span></span>

   ```console
   sn –Vk myRegFile.reg myAssembly.dll
   ```

   <span data-ttu-id="b9ba0-123">Con la opción **–Vr** o **–Vk**, puede incluir opcionalmente un archivo *.snk* para probar la firma de la clave.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-123">With either the **–Vr** or **–Vk** option, you can optionally include an *.snk* file for test key signing.</span></span>

   > [!WARNING]
   > <span data-ttu-id="b9ba0-124">Para garantizar la seguridad, no confíe únicamente en el uso de nombres seguros.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-124">Do not rely on strong names for security.</span></span> <span data-ttu-id="b9ba0-125">Estos solo proporcionan una identidad única.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-125">They provide a unique identity only.</span></span>

   > [!NOTE]
   > <span data-ttu-id="b9ba0-126">Si usa la firma retardada durante el desarrollo con Visual Studio en un equipo de 64 bits y compila un ensamblado para **Cualquier CPU**, es posible que deba aplicar la opción **-Vr** dos veces.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-126">If you use delay signing during development with Visual Studio on a 64-bit computer, and you compile an assembly for **Any CPU**, you might have to apply the **-Vr** option twice.</span></span> <span data-ttu-id="b9ba0-127">(En Visual Studio, **Cualquier CPU** es un valor de la propiedad de compilación **Destino de la plataforma**. Cuando se compila desde la línea de comandos, es el valor predeterminado). Para ejecutar la aplicación desde la línea de comandos o desde el Explorador de archivos, use la versión de 64 bits de [Sn.exe (herramienta de nombre seguro)](../../framework/tools/sn-exe-strong-name-tool.md) para aplicar la opción **-Vr** al ensamblado.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-127">(In Visual Studio, **Any CPU** is a value of the **Platform Target** build property; when you compile from the command line, it is the default.) To run your application from the command line or from File Explorer, use the 64-bit version of the [Sn.exe (Strong Name tool)](../../framework/tools/sn-exe-strong-name-tool.md) to apply the **-Vr** option to the assembly.</span></span> <span data-ttu-id="b9ba0-128">Para cargar el ensamblado en Visual Studio en tiempo de diseño (por ejemplo, si el ensamblado contiene componentes que usan otros ensamblados de la aplicación), use la versión de 32 bits de la herramienta de nombre seguro.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-128">To load the assembly into Visual Studio at design time (for example, if the assembly contains components that are used by other assemblies in your application), use the 32-bit version of the strong-name tool.</span></span> <span data-ttu-id="b9ba0-129">Esto se debe a que el compilador Just-In-Time (JIT) compila el ensamblado en código nativo de 64 bits cuando el ensamblado se ejecuta desde la línea de comandos y en código nativo de 32 bits cuando el ensamblado se carga en el entorno de tiempo de diseño.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-129">This is because the just-in-time (JIT) compiler compiles the assembly to 64-bit native code when the assembly is run from the command line, and to 32-bit native code when the assembly is loaded into the design-time environment.</span></span>

5. <span data-ttu-id="b9ba0-130">Después, normalmente justo antes del envío, se envía el ensamblado a la autoridad de firma de la organización para que lleve a cabo la firma de nombre seguro real mediante la opción **–R** con la herramienta de nombre seguro.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-130">Later, usually just before shipping, you submit the assembly to your organization's signing authority for the actual strong name signing using the **–R** option with the Strong Name tool.</span></span>

   <span data-ttu-id="b9ba0-131">En el ejemplo siguiente se firma un ensamblado denominado *myAssembly.dll* con un nombre seguro mediante el par de claves *sgKey.snk*.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-131">The following example signs an assembly called *myAssembly.dll* with a strong name using the *sgKey.snk* key pair.</span></span>

   ```console
   sn -R myAssembly.dll sgKey.snk
   ```

## <a name="see-also"></a><span data-ttu-id="b9ba0-132">Vea también</span><span class="sxs-lookup"><span data-stu-id="b9ba0-132">See also</span></span>

- [<span data-ttu-id="b9ba0-133">Creación de ensamblados</span><span class="sxs-lookup"><span data-stu-id="b9ba0-133">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="b9ba0-134">Cómo: Crear un par de claves privada y pública</span><span class="sxs-lookup"><span data-stu-id="b9ba0-134">How to: Create a public-private key pair</span></span>](create-public-private-key-pair.md)
- [<span data-ttu-id="b9ba0-135">Sn.exe (herramienta de nombre seguro)</span><span class="sxs-lookup"><span data-stu-id="b9ba0-135">Sn.exe (Strong Name tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="b9ba0-136">Programación con ensamblados</span><span class="sxs-lookup"><span data-stu-id="b9ba0-136">Program with assemblies</span></span>](program.md)
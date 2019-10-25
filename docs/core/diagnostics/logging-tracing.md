---
title: 'Registro y seguimiento: .NET Core'
description: Introducción al registro y seguimiento de .NET Core.
author: sdmaclea
ms.author: stmaclea
ms.date: 08/05/2019
ms.openlocfilehash: 46e64a7f60b88c26ceef9ac817be885bfa180c8e
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "72303657"
---
# <a name="net-core-logging-and-tracing"></a><span data-ttu-id="37c2f-103">Registro y seguimiento de .NET Core</span><span class="sxs-lookup"><span data-stu-id="37c2f-103">.NET Core logging and tracing</span></span>

<span data-ttu-id="37c2f-104">El registro y el seguimiento son en realidad dos nombres para la misma técnica.</span><span class="sxs-lookup"><span data-stu-id="37c2f-104">Logging and tracing are really two names for the same technique.</span></span> <span data-ttu-id="37c2f-105">Esta sencilla técnica se ha usado desde el inicio de la era de la informática.</span><span class="sxs-lookup"><span data-stu-id="37c2f-105">The simple technique has been used since the early days of computers.</span></span> <span data-ttu-id="37c2f-106">Simplemente implica instrumentar una aplicación para escribir la salida que se va a consumir más adelante.</span><span class="sxs-lookup"><span data-stu-id="37c2f-106">It simply involves instrumenting an application to write output to be consumed later.</span></span>

## <a name="reasons-to-use-logging-and-tracing"></a><span data-ttu-id="37c2f-107">Motivos para usar el registro y seguimiento</span><span class="sxs-lookup"><span data-stu-id="37c2f-107">Reasons to use logging and tracing</span></span>

<span data-ttu-id="37c2f-108">Esta técnica sencilla es sorprendentemente eficaz.</span><span class="sxs-lookup"><span data-stu-id="37c2f-108">This simple technique is surprisingly powerful.</span></span> <span data-ttu-id="37c2f-109">Se puede usar en situaciones en las que se produzca un error en un depurador:</span><span class="sxs-lookup"><span data-stu-id="37c2f-109">It can be used in situations where a debugger fails:</span></span>

- <span data-ttu-id="37c2f-110">Las incidencias que se producen durante largos períodos de tiempo pueden ser difíciles de depurar con un depurador tradicional.</span><span class="sxs-lookup"><span data-stu-id="37c2f-110">Issues occurring over long periods of time, can be difficult to debug with a traditional debugger.</span></span> <span data-ttu-id="37c2f-111">Los registros permiten una revisión detallada de evaluación que abarca períodos largos de tiempo.</span><span class="sxs-lookup"><span data-stu-id="37c2f-111">Logs allow for detailed post-mortem review spanning long periods of time.</span></span> <span data-ttu-id="37c2f-112">En cambio, los depuradores están restringidos a análisis en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="37c2f-112">In contrast, debuggers are constrained to real-time analysis.</span></span>
- <span data-ttu-id="37c2f-113">Las aplicaciones multiproceso y las aplicaciones distribuidas a menudo son difíciles de depurar.</span><span class="sxs-lookup"><span data-stu-id="37c2f-113">Multi-threaded applications and distributed applications are often difficult to debug.</span></span>  <span data-ttu-id="37c2f-114">Adjuntar un depurador tiende a modificar los comportamientos.</span><span class="sxs-lookup"><span data-stu-id="37c2f-114">Attaching a debugger tends to modify behaviors.</span></span> <span data-ttu-id="37c2f-115">Los registros detallados se pueden analizar, según sea necesario, para comprender sistemas complejos.</span><span class="sxs-lookup"><span data-stu-id="37c2f-115">Detailed logs can be analyzed as needed to understand complex systems.</span></span>
- <span data-ttu-id="37c2f-116">Las incidencias en las aplicaciones distribuidas pueden surgir de una interacción compleja entre muchos componentes y puede que no sea razonable conectar un depurador en todas las partes del sistema.</span><span class="sxs-lookup"><span data-stu-id="37c2f-116">Issues in distributed applications may arise from a complex interaction between many components and it may not be reasonable to connect a debugger to every part of the system.</span></span>
- <span data-ttu-id="37c2f-117">Muchos servicios no deben estar detenidos.</span><span class="sxs-lookup"><span data-stu-id="37c2f-117">Many services shouldn't be stalled.</span></span> <span data-ttu-id="37c2f-118">Al adjuntar un depurador a menudo se producen errores de tiempo de expiración.</span><span class="sxs-lookup"><span data-stu-id="37c2f-118">Attaching a debugger often causes timeout failures.</span></span>
- <span data-ttu-id="37c2f-119">Las incidencias no siempre están previstas.</span><span class="sxs-lookup"><span data-stu-id="37c2f-119">Issues aren't always foreseen.</span></span> <span data-ttu-id="37c2f-120">El registro y seguimiento están diseñados para una baja sobrecarga, de modo que los programas siempre pueden grabarse en caso de que se produzca una incidencia.</span><span class="sxs-lookup"><span data-stu-id="37c2f-120">Logging and tracing are designed for low overhead so that programs can always be recording in case an issue occurs.</span></span>

## <a name="net-core-apis"></a><span data-ttu-id="37c2f-121">API de .NET Core</span><span class="sxs-lookup"><span data-stu-id="37c2f-121">.NET Core APIs</span></span>

### <a name="print-style-apis"></a><span data-ttu-id="37c2f-122">API de estilo de impresión</span><span class="sxs-lookup"><span data-stu-id="37c2f-122">Print style APIs</span></span>

<span data-ttu-id="37c2f-123">Cada una de las clases <xref:System.Console?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace?displayProperty=nameWithType> y <xref:System.Diagnostics.Debug?displayProperty=nameWithType> proporcionan API de estilo de impresión parecidas para el registro.</span><span class="sxs-lookup"><span data-stu-id="37c2f-123">The <xref:System.Console?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes each provide similar print style APIs convenient for logging.</span></span>

<span data-ttu-id="37c2f-124">La elección de la API de estilo de impresión que se va a usar depende de usted.</span><span class="sxs-lookup"><span data-stu-id="37c2f-124">The choice of which print style API to use is up to you.</span></span> <span data-ttu-id="37c2f-125">Las principales diferencias son:</span><span class="sxs-lookup"><span data-stu-id="37c2f-125">The key differences are:</span></span>

- <xref:System.Console?displayProperty=nameWithType>
  - <span data-ttu-id="37c2f-126">Siempre está habilitada y siempre escribe en la consola.</span><span class="sxs-lookup"><span data-stu-id="37c2f-126">Always enabled and always writes to the console.</span></span>
  - <span data-ttu-id="37c2f-127">Resulta útil para la información que es posible que el cliente necesite ver en la versión.</span><span class="sxs-lookup"><span data-stu-id="37c2f-127">Useful for information that your customer may need to see in the release.</span></span>
  - <span data-ttu-id="37c2f-128">Dado que es el enfoque más sencillo, a menudo se usa para la depuración temporal ad hoc.</span><span class="sxs-lookup"><span data-stu-id="37c2f-128">Because it's the simplest approach, it's often used for ad-hoc temporary debugging.</span></span> <span data-ttu-id="37c2f-129">Este código de depuración a veces no se registra nunca en el control de código fuente.</span><span class="sxs-lookup"><span data-stu-id="37c2f-129">This debug code is often never checked in to source control.</span></span>
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - <span data-ttu-id="37c2f-130">Solo se habilita cuando se define `TRACE`.</span><span class="sxs-lookup"><span data-stu-id="37c2f-130">Only enabled when `TRACE` is defined.</span></span>
  - <span data-ttu-id="37c2f-131">Escribe en el elemento <xref:System.Diagnostics.Trace.Listeners> adjuntado, de forma predeterminada, <xref:System.Diagnostics.DefaultTraceListener>.</span><span class="sxs-lookup"><span data-stu-id="37c2f-131">Writes to attached <xref:System.Diagnostics.Trace.Listeners>, by default the <xref:System.Diagnostics.DefaultTraceListener>.</span></span>
  - <span data-ttu-id="37c2f-132">Use esta API cuando cree registros que se vayan a habilitar en la mayoría de compilaciones.</span><span class="sxs-lookup"><span data-stu-id="37c2f-132">Use this API when creating logs that will be enabled in most builds.</span></span>
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - <span data-ttu-id="37c2f-133">Solo se habilita cuando se define `DEBUG`.</span><span class="sxs-lookup"><span data-stu-id="37c2f-133">Only enabled when `DEBUG` is defined.</span></span>
  - <span data-ttu-id="37c2f-134">Escribe en un depurador adjuntado.</span><span class="sxs-lookup"><span data-stu-id="37c2f-134">Writes to an attached debugger.</span></span>
  - <span data-ttu-id="37c2f-135">En `*nix`, escribe en stderr si se establece `COMPlus_DebugWriteToStdErr`.</span><span class="sxs-lookup"><span data-stu-id="37c2f-135">On `*nix` writes to stderr if `COMPlus_DebugWriteToStdErr` is set.</span></span>
  - <span data-ttu-id="37c2f-136">Use esta API cuando cree registros que se vayan a habilitar solo en las compilaciones de depuración.</span><span class="sxs-lookup"><span data-stu-id="37c2f-136">Use this API when creating logs that will be enabled only in debug builds.</span></span>

### <a name="logging-events"></a><span data-ttu-id="37c2f-137">Eventos de registro</span><span class="sxs-lookup"><span data-stu-id="37c2f-137">Logging events</span></span>

<span data-ttu-id="37c2f-138">Las siguientes API están más orientadas a eventos.</span><span class="sxs-lookup"><span data-stu-id="37c2f-138">The following APIs are more event oriented.</span></span> <span data-ttu-id="37c2f-139">En lugar de registrar cadenas sencillas, registran objetos de evento.</span><span class="sxs-lookup"><span data-stu-id="37c2f-139">Rather than logging simple strings they log event objects.</span></span>

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - <span data-ttu-id="37c2f-140">EventSource es la API de seguimiento de .NET Core de raíz principal.</span><span class="sxs-lookup"><span data-stu-id="37c2f-140">EventSource is the primary root .NET Core tracing API.</span></span>
  - <span data-ttu-id="37c2f-141">Disponible en todas las versiones .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="37c2f-141">Available in all .NET Standard versions.</span></span>
  - <span data-ttu-id="37c2f-142">Solo permite el seguimiento de objetos serializables.</span><span class="sxs-lookup"><span data-stu-id="37c2f-142">Only allows tracing serializable objects.</span></span>
  - <span data-ttu-id="37c2f-143">Escribe en los [clientes de escucha de evento](xref:System.Diagnostics.Tracing.EventListener) adjuntados.</span><span class="sxs-lookup"><span data-stu-id="37c2f-143">Writes to the attached [event listeners](xref:System.Diagnostics.Tracing.EventListener).</span></span>
  - <span data-ttu-id="37c2f-144">.NET Core proporciona clientes de escucha para:</span><span class="sxs-lookup"><span data-stu-id="37c2f-144">.NET Core provides listeners for:</span></span>
    - <span data-ttu-id="37c2f-145">EventPipe de .NET Core en todas las plataformas</span><span class="sxs-lookup"><span data-stu-id="37c2f-145">.NET Core's EventPipe on all platforms</span></span>
    - [<span data-ttu-id="37c2f-146">Seguimiento de eventos para Windows (ETW)</span><span class="sxs-lookup"><span data-stu-id="37c2f-146">Event Tracing for Windows (ETW)</span></span>](/windows/win32/etw/event-tracing-portal)
    - [<span data-ttu-id="37c2f-147">Marco de seguimiento de LTTng para Linux</span><span class="sxs-lookup"><span data-stu-id="37c2f-147">LTTng tracing framework for Linux</span></span>](https://lttng.org/)

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - <span data-ttu-id="37c2f-148">Se incluye en .NET Core y como un [paquete NuGet](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) para .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="37c2f-148">Included in .NET Core and as a [NuGet package](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) for .NET Framework.</span></span>
  - <span data-ttu-id="37c2f-149">Permite el seguimiento en curso de objetos no serializables.</span><span class="sxs-lookup"><span data-stu-id="37c2f-149">Allows in-process tracing of non-serializable objects.</span></span>
  - <span data-ttu-id="37c2f-150">Incluye un puente para permitir que los campos seleccionados de objetos registrados se escriban en un elemento <xref:System.Diagnostics.Tracing.EventSource>.</span><span class="sxs-lookup"><span data-stu-id="37c2f-150">Includes a bridge to allow selected fields of logged objects to be written to an <xref:System.Diagnostics.Tracing.EventSource>.</span></span>

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - <span data-ttu-id="37c2f-151">Proporciona una manera definitiva de identificar los mensajes de registro resultantes de una actividad o transacción específica.</span><span class="sxs-lookup"><span data-stu-id="37c2f-151">Provides a definitive way to identify log messages resulting from a specific activity or transaction.</span></span> <span data-ttu-id="37c2f-152">Este objeto se puede utilizar para correlacionar los registros entre distintos servicios.</span><span class="sxs-lookup"><span data-stu-id="37c2f-152">This object can be used to correlate logs across different services.</span></span>

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - <span data-ttu-id="37c2f-153">Solo Windows.</span><span class="sxs-lookup"><span data-stu-id="37c2f-153">Windows only.</span></span>
  - <span data-ttu-id="37c2f-154">Escribe mensajes en el registro de eventos de Windows.</span><span class="sxs-lookup"><span data-stu-id="37c2f-154">Writes messages to the Windows Event Log.</span></span>
  - <span data-ttu-id="37c2f-155">Los administradores del sistema esperan que aparezcan mensajes de error grave de aplicación en el registro de eventos de Windows.</span><span class="sxs-lookup"><span data-stu-id="37c2f-155">System administrators expect fatal application error messages to appear in the Windows Event Log.</span></span>

## <a name="ilogger-and-logging-frameworks"></a><span data-ttu-id="37c2f-156">Plataformas de registro y de ILogger</span><span class="sxs-lookup"><span data-stu-id="37c2f-156">ILogger and logging frameworks</span></span>

<span data-ttu-id="37c2f-157">Es posible que las API de bajo nivel no sean la opción adecuada para sus necesidades de registro.</span><span class="sxs-lookup"><span data-stu-id="37c2f-157">The low-level APIs may not be the right choice for your logging needs.</span></span> <span data-ttu-id="37c2f-158">Puede que quiera considerar la posibilidad de usar una plataforma de registro.</span><span class="sxs-lookup"><span data-stu-id="37c2f-158">You may want to consider a logging framework.</span></span>

<span data-ttu-id="37c2f-159">La interfaz de <xref:Microsoft.Extensions.Logging.ILogger> se ha utilizado para crear una interfaz de registro común en la que se pueden insertar los registradores mediante la inserción de dependencias.</span><span class="sxs-lookup"><span data-stu-id="37c2f-159">The <xref:Microsoft.Extensions.Logging.ILogger> interface has been used to create a common logging interface where the loggers can be inserted through dependency injection.</span></span>

<span data-ttu-id="37c2f-160">Por ejemplo, para que pueda elegir la mejor opción para la aplicación, `ASP.NET` ofrece compatibilidad con una selección de marcos integrados y de terceros:</span><span class="sxs-lookup"><span data-stu-id="37c2f-160">For instance, to allow you to make the best choice for your application `ASP.NET` offers support for a selection of built-in and third-party frameworks:</span></span>

- [<span data-ttu-id="37c2f-161">Proveedores de registro integrados de ASP.NET</span><span class="sxs-lookup"><span data-stu-id="37c2f-161">ASP.NET built in logging providers</span></span>](/aspnet/core/fundamentals/logging/#built-in-logging-providers)
- [<span data-ttu-id="37c2f-162">Proveedores de registro de terceros de ASP.NET</span><span class="sxs-lookup"><span data-stu-id="37c2f-162">ASP.NET Third-party logging providers</span></span>](/aspnet/core/fundamentals/logging/#third-party-logging-providers)

## <a name="logging-related-references"></a><span data-ttu-id="37c2f-163">Referencias relacionadas de registro</span><span class="sxs-lookup"><span data-stu-id="37c2f-163">Logging related references</span></span>

- [<span data-ttu-id="37c2f-164">Cómo: Compilación condicional con Trace y Debug</span><span class="sxs-lookup"><span data-stu-id="37c2f-164">How to: Compile Conditionally with Trace and Debug</span></span>](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [<span data-ttu-id="37c2f-165">Cómo: agregar instrucciones de seguimiento al código de aplicación</span><span class="sxs-lookup"><span data-stu-id="37c2f-165">How to: Add Trace Statements to Application Code</span></span>](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- <span data-ttu-id="37c2f-166">[El registro de ASP.NET](/aspnet/core/fundamentals/logging) proporciona información general sobre las técnicas de registro que admite.</span><span class="sxs-lookup"><span data-stu-id="37c2f-166">[ASP.NET Logging](/aspnet/core/fundamentals/logging) provides an overview of the logging techniques it supports.</span></span>

- <span data-ttu-id="37c2f-167">[La interpolación de cadenas de C#](../../csharp/language-reference/tokens/interpolated.md) puede simplificar la escritura de código de registro.</span><span class="sxs-lookup"><span data-stu-id="37c2f-167">[C# String Interpolation](../../csharp/language-reference/tokens/interpolated.md) can simplify writing logging code.</span></span>

- <span data-ttu-id="37c2f-168">La propiedad <xref:System.Exception.Message?displayProperty=nameWithType> es útil para las excepciones de registro.</span><span class="sxs-lookup"><span data-stu-id="37c2f-168">The <xref:System.Exception.Message?displayProperty=nameWithType> property is useful for logging exceptions.</span></span>

- <span data-ttu-id="37c2f-169">La clase <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> puede ser útil para proporcionar información de pila en los registros.</span><span class="sxs-lookup"><span data-stu-id="37c2f-169">The <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> class can be useful to provide stack info in your logs.</span></span>

## <a name="performance-considerations"></a><span data-ttu-id="37c2f-170">Consideraciones sobre el rendimiento</span><span class="sxs-lookup"><span data-stu-id="37c2f-170">Performance considerations</span></span>

<span data-ttu-id="37c2f-171">El formato de cadena puede tomar un tiempo de procesamiento de la CPU considerable.</span><span class="sxs-lookup"><span data-stu-id="37c2f-171">String formatting can take noticeable CPU processing time.</span></span>

<span data-ttu-id="37c2f-172">En las aplicaciones críticas de rendimiento, se recomienda lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="37c2f-172">In performance critical applications, it's recommended that you:</span></span>

- <span data-ttu-id="37c2f-173">Evitar muchos registros cuando no haya nadie escuchando.</span><span class="sxs-lookup"><span data-stu-id="37c2f-173">Avoid lots of logging when no one is listening.</span></span> <span data-ttu-id="37c2f-174">Evitar la construcción de mensajes de registro costosos comprobando en primer lugar si el registro está habilitado.</span><span class="sxs-lookup"><span data-stu-id="37c2f-174">Avoid constructing costly logging messages by checking if logging is enabled first.</span></span>
- <span data-ttu-id="37c2f-175">Registrar únicamente lo que sea útil.</span><span class="sxs-lookup"><span data-stu-id="37c2f-175">Only log what's useful.</span></span>
- <span data-ttu-id="37c2f-176">Aplazar el formato sofisticado a la fase de análisis.</span><span class="sxs-lookup"><span data-stu-id="37c2f-176">Defer fancy formatting to the analysis stage.</span></span>
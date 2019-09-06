---
title: Introducción a la plataforma y las herramientas de Microsoft para aplicaciones en contenedor
description: Descubra las ofertas de Microsoft compatibles con el ciclo de vida de aplicaciones de Docker.
ms.date: 02/15/2019
ms.openlocfilehash: 6907528a5d7ff354a312e7575531b9c608cb479f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295088"
---
# <a name="introduction-to-the-microsoft-platform-andtools-for-containerized-apps"></a><span data-ttu-id="581b2-103">Introducción a la plataforma y las herramientas de Microsoft para aplicaciones en contenedor</span><span class="sxs-lookup"><span data-stu-id="581b2-103">Introduction to the Microsoft platform and tools for containerized apps</span></span>

<span data-ttu-id="581b2-104">*Visión: Creación de un ciclo de vida de aplicación en contenedor adaptable y de nivel empresarial que abarque el desarrollo, las operaciones de TI y la administración de la producción.*</span><span class="sxs-lookup"><span data-stu-id="581b2-104">*Vision: Create an adaptable, enterprise-grade, containerized application life cycle that spans your development, IT operations, and production management.*</span></span>

<span data-ttu-id="581b2-105">En la figura 3-1 se muestran los principales pilares del ciclo de vida de las aplicaciones de Docker clasificadas por el tipo de trabajo entregado por varios equipos (desarrollo de aplicaciones, procesos de infraestructuras de DevOps y operaciones y administración de TI).</span><span class="sxs-lookup"><span data-stu-id="581b2-105">Figure 3-1 shows the main pillars in the life cycle of Docker apps classified by the type of work delivered by multiple teams (app-development, DevOps infrastructure processes, and IT management and operations).</span></span> <span data-ttu-id="581b2-106">Por lo general, en la empresa, los perfiles del "rol" responsable de cada área son diferentes.</span><span class="sxs-lookup"><span data-stu-id="581b2-106">Usually, in the enterprise, the profiles of "the persona" responsible for each area are different.</span></span> <span data-ttu-id="581b2-107">Sus aptitudes también lo son.</span><span class="sxs-lookup"><span data-stu-id="581b2-107">So are their skills.</span></span>

![Herramientas de Microsoft.](./media/image1.png)

<span data-ttu-id="581b2-112">**Figura 3-1.**</span><span class="sxs-lookup"><span data-stu-id="581b2-112">**Figure 3-1.**</span></span> <span data-ttu-id="581b2-113">Pilares principales del ciclo de vida de las aplicaciones de Docker en contenedor con la plataforma y las herramientas de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="581b2-113">Main pillars in the life cycle for containerized Docker applications with Microsoft platform and tools</span></span>

<span data-ttu-id="581b2-114">Un flujo de trabajo del ciclo de vida de aplicaciones de Docker en contenedor, en principio, puede ser prescriptivo en función de "opciones de productos predeterminadas", de tal forma que los desarrolladores pueden comenzar más rápido, pero es fundamental que, como opción alternativa, haya un marco abierto para que sea un flujo de trabajo flexible capaz de adaptarse a los diferentes contextos de cada organización o empresa.</span><span class="sxs-lookup"><span data-stu-id="581b2-114">A containerized Docker life-cycle workflow can be initially prescriptive based on "by-default product choices," making it easier for developers to get started faster, but it's fundamental that under the hood there must be an open framework so that it will be a flexible workflow capable of adjusting to the different contexts from each organization or enterprise.</span></span> <span data-ttu-id="581b2-115">La infraestructura de flujo de trabajo (componentes y productos) debe ser lo suficientemente flexible para abarcar el entorno que cada empresa tendrá en el futuro, con la capacidad incluso de cambiar los productos de desarrollo o DevOps por otros.</span><span class="sxs-lookup"><span data-stu-id="581b2-115">The workflow infrastructure (components and products) must be flexible enough to cover the environment that each company will have in the future, even being capable of swapping development or DevOps products to others.</span></span> <span data-ttu-id="581b2-116">Esta flexibilidad, receptividad y amplia selección de tecnologías en la plataforma e infraestructura son precisamente las prioridades de Microsoft para aplicaciones de Docker en contenedor, como se explica en los capítulos siguientes.</span><span class="sxs-lookup"><span data-stu-id="581b2-116">This flexibility, openness, and broad choice of technologies in the platform and infrastructure are precisely the Microsoft priorities for containerized Docker applications, as explained in the chapters that follow.</span></span>

<span data-ttu-id="581b2-117">En la tabla 3-1 se muestra que la intención de las operaciones de DevOps de Microsoft para aplicaciones de Docker en contenedor es ofrecer un flujo de trabajo abierto de DevOps para poder elegir qué productos usar para cada fase (Microsoft o terceros), al mismo tiempo que se ofrece un flujo de trabajo simplificado que proporciona "productos predeterminados" ya conectados; por tanto, puede comenzar rápidamente con el flujo de trabajo de DevOps de nivel empresarial para aplicaciones de Docker.</span><span class="sxs-lookup"><span data-stu-id="581b2-117">Table 3-1 demonstrates that the intention of the Microsoft DevOps for containerized Docker applications is to provide an open DevOps workflow so that you can choose what products to use for each phase (Microsoft or third party) while providing a simplified workflow that provides "by-default-products" already connected; thus, you can quickly get started with your enterprise-level DevOps workflow for Docker apps.</span></span>

<span data-ttu-id="581b2-118">**Tabla 3-1.**</span><span class="sxs-lookup"><span data-stu-id="581b2-118">**Table 3-1.**</span></span> <span data-ttu-id="581b2-119">Flujos de trabajo de DevOps, abiertos para cualquier tecnología.</span><span class="sxs-lookup"><span data-stu-id="581b2-119">DevOps workflows, open to any technology</span></span>

| <span data-ttu-id="581b2-120">administrador de flujos de trabajo</span><span class="sxs-lookup"><span data-stu-id="581b2-120">Host</span></span> | <span data-ttu-id="581b2-121">Tecnologías de Microsoft</span><span class="sxs-lookup"><span data-stu-id="581b2-121">Microsoft technologies</span></span> | <span data-ttu-id="581b2-122">Aplicaciones de terceros: acoplables a Azure</span><span class="sxs-lookup"><span data-stu-id="581b2-122">Third-party—Azure pluggable</span></span> |
| ---------------------------| ----------------------------------------------------| --------------------------------------------------------------------------------|
| <span data-ttu-id="581b2-123">Plataforma para aplicaciones de Docker</span><span class="sxs-lookup"><span data-stu-id="581b2-123">Platform for Docker apps</span></span>   | <span data-ttu-id="581b2-124">• Microsoft Visual Studio y Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="581b2-124">• Microsoft Visual Studio and Visual Studio Code</span></span><br /> <span data-ttu-id="581b2-125">• .NET</span><span class="sxs-lookup"><span data-stu-id="581b2-125">• .NET</span></span><br /> <span data-ttu-id="581b2-126">• Microsoft Azure Kubernetes Service (AKS)</span><span class="sxs-lookup"><span data-stu-id="581b2-126">• Microsoft Azure Kubernetes Service (AKS)</span></span><br /> <span data-ttu-id="581b2-127">• Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="581b2-127">• Azure Service Fabric</span></span><br /> <span data-ttu-id="581b2-128">• Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="581b2-128">• Azure Container Registry</span></span><br /> | <span data-ttu-id="581b2-129">• Cualquier editor de código (por ejemplo, Sublime)</span><span class="sxs-lookup"><span data-stu-id="581b2-129">• Any code editor (for example, Sublime)</span></span><br /> <span data-ttu-id="581b2-130">• Cualquier lenguaje (Node.js, Java, Go, etc.)</span><span class="sxs-lookup"><span data-stu-id="581b2-130">• Any language (Node.js, Java, Go, etc.)</span></span><br /> <span data-ttu-id="581b2-131">• Cualquier orquestrator y programador</span><span class="sxs-lookup"><span data-stu-id="581b2-131">• Any orchestrator and scheduler</span></span><br /> <span data-ttu-id="581b2-132">• Cualquier registro de Docker</span><span class="sxs-lookup"><span data-stu-id="581b2-132">• Any Docker registry</span></span><br /> |
| <span data-ttu-id="581b2-133">DevOps para aplicaciones de Docker</span><span class="sxs-lookup"><span data-stu-id="581b2-133">DevOps for Docker apps</span></span>     | <span data-ttu-id="581b2-134">• Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="581b2-134">• Azure DevOps Services</span></span><br /> <span data-ttu-id="581b2-135">• Microsoft Team Foundation Server</span><span class="sxs-lookup"><span data-stu-id="581b2-135">• Microsoft Team Foundation Server</span></span><br /> <span data-ttu-id="581b2-136">• Azure Kubernetes Service (AKS)</span><span class="sxs-lookup"><span data-stu-id="581b2-136">• Azure Kubernetes Service (AKS)</span></span><br /> <span data-ttu-id="581b2-137">• Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="581b2-137">• Azure Service Fabric</span></span><br /> | <span data-ttu-id="581b2-138">• GitHub, Git, Subversion, etc.</span><span class="sxs-lookup"><span data-stu-id="581b2-138">• GitHub, Git, Subversion, etc.</span></span><br /> <span data-ttu-id="581b2-139">• Jenkins, Chef, Puppet, Velocity, CircleCI, TravisCI, etc.</span><span class="sxs-lookup"><span data-stu-id="581b2-139">• Jenkins, Chef, Puppet, Velocity, CircleCI, TravisCI, etc.</span></span><br /> <span data-ttu-id="581b2-140">• Centro de datos de Docker local, Docker Swarm, Mesos DC/OS, Kubernetes, etc.</span><span class="sxs-lookup"><span data-stu-id="581b2-140">• On-premises Docker Datacenter, Docker Swarm, Mesos DC/OS, Kubernetes, etc.</span></span><br /> |
| <span data-ttu-id="581b2-141">Administración y supervisión</span><span class="sxs-lookup"><span data-stu-id="581b2-141">Management and monitoring</span></span>  | <span data-ttu-id="581b2-142">• Azure Monitor</span><span class="sxs-lookup"><span data-stu-id="581b2-142">• Azure Monitor</span></span> | <span data-ttu-id="581b2-143">• Marathon, Chronos, etc.</span><span class="sxs-lookup"><span data-stu-id="581b2-143">• Marathon, Chronos, etc.</span></span><br />|

<span data-ttu-id="581b2-144">La plataforma y las herramientas de Microsoft para aplicaciones de Docker en contenedor, como se define en la tabla 3-1, constan de los siguientes componentes:</span><span class="sxs-lookup"><span data-stu-id="581b2-144">The Microsoft platform and tools for containerized Docker apps, as defined in Table 3-1, comprise the following components:</span></span>

- <span data-ttu-id="581b2-145">**Plataforma de desarrollo de aplicaciones de Docker**. El desarrollo de un servicio una colección de servicios que componen una "aplicación".</span><span class="sxs-lookup"><span data-stu-id="581b2-145">**Platform for Docker Apps development** The development of a service, or collection of services that make up an "app."</span></span> <span data-ttu-id="581b2-146">La plataforma de desarrollo ofrece todo el trabajo que los desarrolladores necesitan antes de insertar el código en un repositorio de código compartido.</span><span class="sxs-lookup"><span data-stu-id="581b2-146">The development platform provides all the work developers requires prior to pushing their code to a shared code repository.</span></span> <span data-ttu-id="581b2-147">El desarrollo de servicios, implementados como contenedores, es similar al desarrollo de las mismas aplicaciones o servicios sin Docker.</span><span class="sxs-lookup"><span data-stu-id="581b2-147">Developing services, deployed as containers, are similar to the development of the same apps or services without Docker.</span></span> <span data-ttu-id="581b2-148">Puede seguir usando su lenguaje favorito (.NET, Node.js, Go, etc.) y su editor o IDE preferidos, como Visual Studio o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="581b2-148">You continue to use your preferred language (.NET, Node.js, Go, etc.) and preferred editor or IDE like Visual Studio or Visual Studio Code.</span></span> <span data-ttu-id="581b2-149">Sin embargo, en lugar de considerar Docker como un destino de implementación, los servicios se desarrollan en el entorno de Docker.</span><span class="sxs-lookup"><span data-stu-id="581b2-149">However, rather than consider Docker a deployment destination, you develop your services in the Docker environment.</span></span> <span data-ttu-id="581b2-150">El código se compila, ejecuta, prueba y depura en contenedores a nivel local, proporcionando el entorno de destino en la fase de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="581b2-150">You build, run, test, and debug your code in containers locally, providing the destination environment at development time.</span></span> <span data-ttu-id="581b2-151">Al proporcionar el entorno de destino local, los contenedores de Docker configuran lo que ayudará significativamente a mejorar el ciclo de vida de DevOps.</span><span class="sxs-lookup"><span data-stu-id="581b2-151">By providing the destination environment locally, Docker containers set up what will drastically help you improve your DevOps life cycle.</span></span> <span data-ttu-id="581b2-152">Visual Studio y Visual Studio Code disponen de extensiones para integrar los contenedores de Docker en el proceso de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="581b2-152">Visual Studio and Visual Studio Code have extensions to integrate Docker containers within your development process.</span></span>

- <span data-ttu-id="581b2-153">**DevOps para las aplicaciones de Docker**. Los desarrolladores que crean aplicaciones de Docker pueden usar [Azure DevOps Services](https://azure.microsoft.com/services/devops/) o cualquier otro producto de terceros, como Jenkins, para crear una administración integral y automatizada del ciclo de vida de las aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="581b2-153">**DevOps for Docker Apps** Developers creating Docker applications can use [Azure DevOps Services](https://azure.microsoft.com/services/devops/) or any other third-party product, like Jenkins, to build out a comprehensive automated application life-cycle management (ALM).</span></span>

  <span data-ttu-id="581b2-154">Con Azure DevOps Services, los desarrolladores pueden crear DevOps centradas en contenedores para un proceso rápido e iterativo que abarque el control del código fuente desde cualquier plataforma (Azure DevOps Services-Git, GitHub, cualquier repositorio Git remoto o Subversion), integración continua (CI), pruebas unitarias internas, pruebas de integración entre contenedores y servicios, entrega continua (CD) y administración de versiones.</span><span class="sxs-lookup"><span data-stu-id="581b2-154">With Azure DevOps Services, developers can create container-focused DevOps for a fast, iterative process that covers source-code control from anywhere (Azure DevOps Services-Git, GitHub, any remote Git repository, or Subversion), Continuous Integration (CI), internal unit tests, inter-container/service integration tests, Continuous Delivery (CD), and release management (RM).</span></span> <span data-ttu-id="581b2-155">Los desarrolladores también pueden automatizar las versiones de las aplicaciones de Docker en Azure Kubernetes Service (AKS), desde entornos de desarrollo a almacenamiento provisional y producción.</span><span class="sxs-lookup"><span data-stu-id="581b2-155">Developers also can automate their Docker application releases into Azure Kubernetes Service (AKS), from development to staging and production environments.</span></span>

- <span data-ttu-id="581b2-156">**Administración y supervisión**. Los equipos de TI pueden administrar y supervisar aplicaciones y servicios de producción de varias maneras, mediante la integración de ambas perspectivas en una experiencia consolidada.</span><span class="sxs-lookup"><span data-stu-id="581b2-156">**Management and Monitoring** IT can manage and monitor production applications and services in several ways, integrating both perspectives in a consolidated experience.</span></span>

  - <span data-ttu-id="581b2-157">**Azure Portal** Si usa orquestadores de código abierto, Azure Kubernetes Service (AKS), Service Fabric y otros orquestadores le ayudarán a configurar y mantener los entornos de Docker.</span><span class="sxs-lookup"><span data-stu-id="581b2-157">**Azure portal** If you're using open-source orchestrators, Azure Kubernetes Service (AKS), Service Fabric and other orchestrators help you to set up and maintain your Docker environments.</span></span> <span data-ttu-id="581b2-158">Si usa Azure Service Fabric, la herramienta Service Fabric Explorer permite visualizar y configurar el clúster.</span><span class="sxs-lookup"><span data-stu-id="581b2-158">If you're using Azure Service Fabric, the Service Fabric Explorer tool makes it possible for you to visualize and configure your cluster.</span></span>

  - <span data-ttu-id="581b2-159">**Herramientas de Docker** Puede administrar las aplicaciones de contenedor con herramientas conocidas.</span><span class="sxs-lookup"><span data-stu-id="581b2-159">**Docker tools** You can manage your container applications using familiar tools.</span></span> <span data-ttu-id="581b2-160">No es necesario cambiar sus prácticas de administración de Docker existentes para mover cargas de trabajo de contenedor a la nube.</span><span class="sxs-lookup"><span data-stu-id="581b2-160">There's no need to change your existing Docker management practices to move container workloads to the cloud.</span></span> <span data-ttu-id="581b2-161">Use las herramientas de administración de aplicaciones con las que ya está familiarizado y conéctelas a través de los puntos de conexión de API para el orquestador de su elección.</span><span class="sxs-lookup"><span data-stu-id="581b2-161">Use the application management tools you're already familiar with and connect via the standard API endpoints for the orchestrator of your choice.</span></span> <span data-ttu-id="581b2-162">También puede usar otras herramientas de terceros para administrar las aplicaciones de Docker, como Docker Datacenter o las herramientas de Docker para la CLI.</span><span class="sxs-lookup"><span data-stu-id="581b2-162">You also can use other third-party tools to manage your Docker applications, such as Docker Datacenter or even CLI Docker tools.</span></span> 

    <span data-ttu-id="581b2-163">Incluso si está familiarizado con los comandos de Linux, puede administrar las aplicaciones de contenedor mediante Microsoft Windows y PowerShell con una línea de comandos del subsistema de Linux y los productos (Docker, Kubernetes, etc.) que los clientes ejecutan en esta funcionalidad del subsistema de Linux.</span><span class="sxs-lookup"><span data-stu-id="581b2-163">Even if you're familiar with Linux commands, you can manage your container applications using Microsoft Windows and PowerShell with a Linux Subsystem command line and the products (Docker, Kubernetes…) clients running on this Linux Subsystem capability.</span></span> <span data-ttu-id="581b2-164">Más adelante en este libro obtendrá más información sobre el uso de estas herramientas en el subsistema de Linux con su sistema operativo favorito de Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="581b2-164">You'll learn more about using these tools under Linux Subsystem using your favorite Microsoft Windows OS later in this book.</span></span>

  - <span data-ttu-id="581b2-165">**Herramientas de código abierto** Como AKS expone los puntos de conexión de API estándar para el motor de orquestación, las herramientas más populares son compatibles con AKS y, en la mayoría de los casos, son fáciles de usar, incluidos los visualizadores, las herramientas de supervisión, las herramientas de línea de comandos e incluso futuras herramientas a medida que estén disponibles.</span><span class="sxs-lookup"><span data-stu-id="581b2-165">**Open-source tools** Because AKS exposes the standard API endpoints for the orchestration engine, the most popular tools are compatible with AKS and, in most cases, will work out of the box—including visualizers, monitoring, command-line tools, and even future tools as they become available.</span></span>

  - <span data-ttu-id="581b2-166">**Azure Monitor** Se trata de una solución de Azure para supervisar todos los aspectos del entorno de producción.</span><span class="sxs-lookup"><span data-stu-id="581b2-166">**Azure Monitor** Is Azure's solution to monitor every angle of your production environment.</span></span> <span data-ttu-id="581b2-167">Puede supervisar las aplicaciones de Docker en producción con solo configurar su SDK en los servicios, a fin de obtener datos de registro generados por el sistema a partir de las aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="581b2-167">You can monitor production Docker applications by just setting up its SDK into your services so that you can get system-generated log data from the applications.</span></span>

<span data-ttu-id="581b2-168">Por tanto, Microsoft ofrece una base completa para un ciclo de vida de aplicaciones de Docker en contenedor de un extremo a otro.</span><span class="sxs-lookup"><span data-stu-id="581b2-168">Thus, Microsoft offers a complete foundation for an end-to-end containerized Docker application life cycle.</span></span> <span data-ttu-id="581b2-169">Se trata de *una colección de productos y tecnologías que le permiten seleccionar, como opción, las herramientas y procesos existentes, así como realizar la integración con ellos*.</span><span class="sxs-lookup"><span data-stu-id="581b2-169">However, it's *a collection of products and technologies that allow you to optionally select and integrate with existing tools and processes*.</span></span> <span data-ttu-id="581b2-170">La flexibilidad de un amplio enfoque y la eficacia de las funcionalidades posicionan a Microsoft como una solución eficaz para el desarrollo de aplicaciones de Docker en contenedor.</span><span class="sxs-lookup"><span data-stu-id="581b2-170">The flexibility in a broad approach along with the strength in the depth of capabilities place Microsoft in a strong position for containerized Docker application development.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="581b2-171">[Anterior](../Docker-application-lifecycle/containers-foundation-for-devops-collaboration.md)
>[Siguiente](../design-develop-containerized-apps/index.md)</span><span class="sxs-lookup"><span data-stu-id="581b2-171">[Previous](../Docker-application-lifecycle/containers-foundation-for-devops-collaboration.md)
[Next](../design-develop-containerized-apps/index.md)</span></span>
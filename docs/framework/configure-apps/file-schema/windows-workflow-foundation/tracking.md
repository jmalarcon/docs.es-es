---
title: <tracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: fd9b50ed-98a1-4518-836d-e4e02c670822
ms.openlocfilehash: 28d73bb74c4a49052589040adc26194b1300668c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397602"
---
# <a name="tracking"></a>\<> de seguimiento
Representa una sección de configuración para definir los valores de seguimiento de un servicio de flujo de trabajo.  
  
 Para obtener más información sobre el seguimiento del flujo de trabajo y su configuración, consulte [seguimiento y](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) seguimiento del flujo de trabajo y [configuración del seguimiento para un flujo de trabajo](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<integrado. > De ServiceModel**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<> de seguimiento**  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <participants>
        <add name="String" 
             profileName="String" 
             type="String" />
      </participants>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String" 
                                    childActivityName="String"/>
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String" />
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String"  />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQueries>
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestQueries>
            <cancelRequestQuery activityName="String" 
                                childActivityName="String"/>
          </cancelRequestQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String" 
                                 name="String"/>
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery activityName="String" 
                                   faultHandlerActivityName="String" />
          </faultPropagationQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String" />
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
 Ninguno.  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|DESCRIPCIÓN|  
|-------------|-----------------|  
|[\<participantes >](participants.md)|Colección de elementos de configuración que definen los participantes que se suscriben a los registros de seguimiento. Los participantes de seguimiento contienen la lógica para procesar la carga de los registros de seguimiento (por ejemplo, podrían escribir en un archivo).|  
|[\<trackingProfile>](trackingprofile.md)|Un perfil de seguimiento para filtrar registros de seguimiento emitidos desde una instancia de flujo de trabajo.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|DESCRIPCIÓN|  
|-------------|-----------------|  
|system.ServiceModel|El elemento raíz de todos los elementos de configuración de flujo de trabajo.|  
  
## <a name="remarks"></a>Comentarios  
 El seguimiento ofrece la posibilidad de examinar la ejecución de un flujo de trabajo. La infraestructura de seguimiento del flujo de trabajo instrumenta un flujo de trabajo para emitir registros que reflejan los eventos clave durante la ejecución. Por ejemplo, cuando una instancia de flujo de trabajo se inicia o completa, se emiten los registros de seguimiento. El seguimiento también puede extraer datos comerciales relevantes asociados a las variables de flujo de trabajo. Por ejemplo, si el flujo de trabajo representa un sistema de procesamiento de pedidos, el Id. del pedido se puede extraer junto con el registro de seguimiento. En general, la habilitación del seguimiento de WF facilita el diagnóstico o los análisis comerciales durante la ejecución de un flujo de trabajo.  
  
## <a name="see-also"></a>Vea también

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [Seguimiento y traza de flujos de trabajo](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)

---
title: <workflow>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560aa9b6-9cf3-460e-b798-f87d14b1d2de
ms.openlocfilehash: 5205f9ab89297c0e55c3e5e0c03b9e3fef36963a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397579"
---
# <a name="workflow"></a>\<> de flujo de trabajo
Un elemento de configuración que contiene todas las consultas para un flujo de trabajo concreto identificado por la propiedad <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType>.  
  
 Para obtener más información sobre el seguimiento del flujo de trabajo y su configuración, consulte [seguimiento y](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) seguimiento de flujos de trabajo y [perfiles de seguimiento](../../../windows-workflow-foundation/tracking-profiles.md).  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<integrado. > De ServiceModel**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de seguimiento**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> trackingProfile**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de flujo de trabajo**  
  
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
  
|Atributo|DESCRIPCIÓN|  
|---------------|-----------------|  
|activityDefinitionId|Una cadena que especifica el Id. de definición de actividad del flujo de trabajo del que se está realizando el seguimiento.|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|DESCRIPCIÓN|  
|-------------|-----------------|  
|[\<activityScheduledQueries>](activityscheduledqueries.md)|Representa una colección de consultas que se utilizan para realizar el seguimiento de una actividad programada para su ejecución por parte de una actividad primaria. La consulta es necesaria para que un participante de seguimiento se suscriba a los registros programados de la actividad.|  
|[\<activityStateQueries>](activitystatequeries.md)|Representa una colección de consultas que se usan para realizar el seguimiento de los cambios del ciclo de vida de las actividades que constituyen una instancia de flujo de trabajo. Por ejemplo, puede que desee realizar un seguimiento de cada vez que se complete la actividad "enviar correo electrónico" dentro de una instancia de flujo de trabajo. Esta consulta es necesaria para que un participante de seguimiento se suscriba a los objetos de registro de estado de actividad. Los estados de suscripción disponibles se especifican en ActivityStates.|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries.md)|Representa una colección de consultas que se usan para realizar el seguimiento de la reanudación de un marcador dentro de una instancia de flujo de trabajo. La consulta es necesaria para que un participante del seguimiento se suscriba a los registros de reanudación del marcador.|  
|[\<cancelRequestedQueries>](cancelrequestedqueries.md)|Representa una colección de consultas que se usan para realizar el seguimiento de las solicitudes para cancelar una actividad secundaria por parte de la actividad primaria. La consulta es necesaria para que un participante del seguimiento se suscriba con el fin de cancelar los objetos de registro de solicitud.|  
|[\<customTrackingQueries>](customtrackingqueries.md)|Representa una colección de consultas que se utilizan para realizar el seguimiento de los eventos que defina en sus actividades de código. La consulta es necesaria para que un participante de seguimiento se suscriba a los registros del seguimiento personalizados.|  
|[\<faultPropagationQueries>](faultpropagationqueries.md)|Representa una colección de consultas que se utilizan para realizar el seguimiento del control de errores que se producen dentro de una actividad.  Este evento se produce cada vez que un FaultHandler procesa un error. Debería usar tal consulta para realizar el seguimiento del control de errores que se producen dentro de una actividad. La consulta es necesaria que un participante del seguimiento se suscriba a los registros de propagación de errores.|  
|[\<workflowInstanceQueries>](workflowinstancequeries.md)|Representa una colección de elementos de configuración que realizan el seguimiento de los cambios del ciclo de vida de la instancia del flujo de trabajo, como un evento iniciado o completado.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|DESCRIPCIÓN|  
|-------------|-----------------|  
|[\<trackingProfile>](trackingprofile.md)|Representa una sección de configuración para crear una suscripción a los registros de seguimiento de flujo de trabajo en un participante de seguimiento. Los perfiles de seguimiento contienen consultas de seguimiento que permiten a un participante de seguimiento suscribirse a los eventos del flujo de trabajo que se emiten cuando el estado de una instancia de flujo de trabajo cambia en el tiempo de ejecución. Las consultas definidas dentro de la sección de perfil de seguimiento definen los tipos de eventos que devuelve la suscripción.|  
  
## <a name="remarks"></a>Comentarios  
 Los perfiles de seguimiento contienen consultas de seguimiento que permiten a un participante de seguimiento suscribirse a los eventos del flujo de trabajo que se emiten cuando el estado de una determinada instancia de flujo de trabajo cambia en el tiempo de ejecución. Este elemento de configuración identifica la instancia de flujo de trabajo de la que se está realizando el seguimiento.  
  
 Dependiendo de sus requisitos de supervisión, puede escribir un perfil muy general que se suscribe a un conjunto pequeño de cambios de estado de alto nivel en un flujo de trabajo. A la inversa, puede crear un perfil específico cuyos eventos resultantes estén lo suficientemente enriquecidos para reconstruir un flujo de ejecución detallado posteriormente.  
  
 Los perfiles de seguimiento se estructuran como suscripciones declarativas para los registros de seguimiento que le permiten consultar el tiempo de ejecución de flujo de trabajo para registros de seguimiento específicos. Hay una serie de tipos de consultas que le permiten suscribirse a distintas clases de registros de seguimiento. Para obtener una lista completa de consultas, vea la lista de elementos secundarios de este tema y [perfiles de seguimiento](../../../windows-workflow-foundation/tracking-profiles.md).  
  
 En el ejemplo siguiente se muestra un perfil de seguimiento en un archivo de configuración que permite a un participante `Started` de `Completed` seguimiento suscribirse a los eventos de flujo de trabajo y.  
  
```xml  
<system.serviceModel>  
  <tracking>    
    <trackingProfile name="Sample Tracking Profile">  
      <workflow activityDefinitionId="*">  
         <workflowInstanceQueries>  
            <workflowInstanceQuery>  
            <states>  
              <state name="Started"/>  
              <state name="Completed"/>  
            </states>  
          </workflowInstanceQuery>  
        </workflowInstanceQueries>  
      </workflow>  
    </trackingProfile>          
   </profiles>  
  </tracking>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a>Vea también

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [Seguimiento y traza de flujos de trabajo](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Perfiles de seguimiento](../../../windows-workflow-foundation/tracking-profiles.md)

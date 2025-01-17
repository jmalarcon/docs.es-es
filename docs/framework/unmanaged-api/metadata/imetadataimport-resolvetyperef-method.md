---
title: IMetaDataImport::ResolveTypeRef (Método)
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResolveTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f323e91e60c9735a51e955eaab6673ca167f294d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951876"
---
# <a name="imetadataimportresolvetyperef-method"></a>IMetaDataImport::ResolveTypeRef (Método)
Resuelve una <xref:System.Type> referencia representada por el token TypeRef especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
## <a name="parameters"></a>Parámetros  
 `tr`  
 de Token de metadatos de TypeRef para el que se va a devolver la información de tipos a la que se hace referencia.  
  
 `riid`  
 de IID de la interfaz que se va a `ppIScope`devolver en. Normalmente, esto sería IID_IMetaDataImport.  
  
 `ppIScope`  
 enuncia Interfaz al ámbito del módulo en el que se define el tipo al que se hace referencia.  
  
 `ptd`  
 enuncia Un puntero a un token de TypeDef que representa el tipo al que se hace referencia.  
  
## <a name="remarks"></a>Comentarios  
  
> [!IMPORTANT]
> No use este método si se cargan varios dominios de aplicación. El método no respeta los límites del dominio de aplicación. Si se cargan varias versiones de un ensamblado y contienen el mismo tipo con el mismo espacio de nombres, el método devuelve el ámbito del módulo del primer tipo que encuentra.  
  
 El `ResolveTypeRef` método busca la definición de tipo en otros módulos. Si se encuentra la definición de tipo `ResolveTypeRef` , devuelve una interfaz a ese ámbito de módulo, así como el token de TypeDef para el tipo.  
  
 Si la referencia de tipo que se va a resolver tiene un ámbito de resolución `ResolveTypeRef` de AssemblyRef, el método busca una coincidencia solo en los ámbitos de metadatos que ya se han abierto con llamadas al método [IMetaDataDispenser:: OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) o a la [ IMetaDataDispenser:: Openscopeonmemory (](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) (método). Esto se debe `ResolveTypeRef` a que no puede determinar solo el ámbito de AssemblyRef en el que se almacena en el disco o en la caché global de ensamblados el ensamblado.  
  
## <a name="requirements"></a>Requisitos  
 **Select** Consulte [Requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado**: Cor. h  
  
 **Biblioteca** Se incluye como recurso en MsCorEE. dll  
  
 **Versiones de .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vea también

- [IMetaDataImport (interfaz)](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 (interfaz)](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

---
title: ICLRStrongName::StrongNameTokenFromPublicKey (Método)
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey method [.NET Framework hosting]
- StrongNameTokenFromPublicKey method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 7962ce88-7e86-4a6f-8298-621b01ffc3c2
topic_type:
- apiref
ms.openlocfilehash: f37cd6ef85985784303aeb976776b03fbc74dec3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092532"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a>ICLRStrongName::StrongNameTokenFromPublicKey (Método)
Obtiene un token que representa una clave pública. Un token de nombre seguro es la forma abreviada de una clave pública.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT StrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a>Parámetros  
 `pbPublicKeyBlob`  
 de Estructura de tipo [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) que contiene la parte pública del par de claves utilizado para generar la firma de nombre seguro.  
  
 `cbPublicKeyBlob`  
 de Tamaño, en bytes, de `pbPublicKeyBlob`.  
  
 `ppbStrongNameToken`  
 enuncia El token de nombre seguro correspondiente a la clave pasada `pbPublicKeyBlob`. El Common Language Runtime asigna la memoria en la que se va a devolver el token. El llamador debe liberar esta memoria mediante el método [ICLRStrongName:: StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) .  
  
 `pcbStrongNameToken`  
 enuncia Tamaño, en bytes, del token de nombre seguro devuelto.  
  
## <a name="return-value"></a>Valor devuelto  
 `S_OK` si el método se completó correctamente; de lo contrario, un valor HRESULT que indica un error (vea [Valores HRESULT comunes](https://go.microsoft.com/fwlink/?LinkId=213878) para una lista).  
  
## <a name="remarks"></a>Comentarios  
 Un token de nombre seguro es la forma abreviada de una clave pública que se usa para ahorrar espacio al almacenar información de clave en los metadatos. En concreto, se usan tokens de nombre seguro en las referencias de ensamblado para hacer referencia al ensamblado dependiente.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Vea [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** Metahost. h  
  
 **Biblioteca:** Se incluye como recurso en Mscoree. dll  
  
 **Versiones de .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Vea también

- [StrongNameGetPublicKey (método)](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [PublicKeyBlob (estructura)](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [ICLRStrongName (interfaz)](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

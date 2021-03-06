---
title: Método IMetaDataEmit::DefineField
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b54ceb099df15855b6b30b8c28d7d8917a9c71eb
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50184943"
---
# <a name="imetadataemitdefinefield-method"></a>Método IMetaDataEmit::DefineField
Cria uma definição para um campo com a assinatura de metadados especificado e obtém um token para essa definição de campo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT DefineField (   
    [in]  mdTypeDef   td,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwFieldFlags,   
    [in]  PCCOR_SIGNATURE pvSigBlob,   
    [in]  ULONG       cbSigBlob,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue,   
    [out] mdFieldDef  *pmd   
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `td`  
 [in] O `mdTypeDef` token para a classe ou interface delimitador.  
  
 `szName`  
 [in] O nome do campo em Unicode.  
  
 `dwFieldFlags`  
 [in] Os atributos de campo. Esse é um bitmask de `CorFieldAttr` valores.  
  
 `pvSigBlob`  
 [in] A assinatura de campo como um BLOB.  
  
 `cbSigBlob`  
 [in] A contagem de bytes em `pvSigBlob`.  
  
 `dwCPlusTypeFlag`  
 [in] O `ELEMENT_TYPE_` *\** para o valor da constante. Esse é um `CorElementType` valor. Se não definir um valor constante para o campo, use `ELEMENT_TYPE_END`.  
  
 `pValue`  
 [in] O valor da constante para o campo.  
  
 `cchValue`  
 [in] O tamanho em caracteres (Unicode) do `pValue`.  
  
 `pmd`  
 [out] O `mdFieldDef` token atribuído.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

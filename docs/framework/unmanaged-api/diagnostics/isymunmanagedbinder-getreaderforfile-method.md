---
title: Método ISymUnmanagedBinder::GetReaderForFile
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderForFile
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderForFile
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderForFile method [.NET Framework debugging]
- GetReaderForFile method [.NET Framework debugging]
ms.assetid: 46c06258-831e-47c8-a50a-8650af6b637e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: df6a35dcaebc681aa5463a014d3283c81efea617
ms.sourcegitcommit: 296183dbe35077b5c5e5e74d5fbe7f399bc507ee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/05/2018
ms.locfileid: "50982809"
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a>Método ISymUnmanagedBinder::GetReaderForFile
Dado uma interface de metadados e um nome de arquivo, retorna a correta [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface que lê os símbolos de depuração associados com o módulo.  
  
 Esse método abrirá o arquivo de programa (PDB) do banco de dados somente se ele está ao lado do arquivo executável. Essa alteração foi feita para fins de segurança. Se você precisar de uma pesquisa mais abrangente para o arquivo PDB, use o [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `importer`  
 [in] Um ponteiro para a interface de importação de metadados.  
  
 `fileName`  
 [in] Um ponteiro para o nome do arquivo.  
  
 `searchPath`  
 [in] Um ponteiro para o caminho de pesquisa.  
  
 `pRetVal`  
 [out] Um ponteiro que é definido para retornado [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** Corsym, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [Método GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)

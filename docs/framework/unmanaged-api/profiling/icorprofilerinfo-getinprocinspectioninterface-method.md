---
title: "Método ICorProfilerInfo::GetInprocInspectionInterface"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetInprocInspectionInterface
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetInprocInspectionInterface
helpviewer_keywords:
- GetInprocInspectionInterface method [.NET Framework profiling]
- ICorProfilerInfo::GetInprocInspectionInterface method [.NET Framework profiling]
ms.assetid: 22a92d1d-8849-4af6-8304-ecc53dd1d289
topic_type: apiref
caps.latest.revision: "19"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: be114784b0003e5f1540520fdbbef751b369f1da
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a><span data-ttu-id="cbc2f-102">Método ICorProfilerInfo::GetInprocInspectionInterface</span><span class="sxs-lookup"><span data-stu-id="cbc2f-102">ICorProfilerInfo::GetInprocInspectionInterface Method</span></span>
<span data-ttu-id="cbc2f-103">Obtém um objeto que pode ser consultado para uma interface de "ICorDebugProcess".</span><span class="sxs-lookup"><span data-stu-id="cbc2f-103">Gets an object that can be queried for an "ICorDebugProcess" interface.</span></span> <span data-ttu-id="cbc2f-104">Este método está obsoleto no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="cbc2f-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbc2f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cbc2f-105">Syntax</span></span>  
  
```  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cbc2f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cbc2f-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="cbc2f-107">[out](/cpp/atl/iunknown) objeto que pode ser consultado por um `ICorDebugProcess` interface.</span><span class="sxs-lookup"><span data-stu-id="cbc2f-107">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbc2f-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="cbc2f-108">Remarks</span></span>  
 <span data-ttu-id="cbc2f-109">O common language runtime (CLR) depuração da API com suporte limitado em processo depuração do .NET Framework versão 1.0.</span><span class="sxs-lookup"><span data-stu-id="cbc2f-109">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="cbc2f-110">No processo de depuração habilitado um criador de perfil usar as partes de inspeção da API de depuração.</span><span class="sxs-lookup"><span data-stu-id="cbc2f-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="cbc2f-111">Como resultado de comentários do cliente, no processo de depuração foi removido do .NET Framework versão 2.0 e substituído por um conjunto de funcionalidades mais alinhados com a API de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="cbc2f-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbc2f-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cbc2f-112">Requirements</span></span>  
 <span data-ttu-id="cbc2f-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbc2f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbc2f-114">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cbc2f-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cbc2f-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cbc2f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cbc2f-116">**Versão do .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="cbc2f-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbc2f-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cbc2f-117">See Also</span></span>  
 [<span data-ttu-id="cbc2f-118">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="cbc2f-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
---
title: "Duração de chamada"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4973ec3-3c66-4c0b-b5d0-294b62c83f7d
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9bf221115b7919a1ca7facdfe80af2af899b3326
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="call-duration"></a>Duração de chamada
Nome do contador: Duração da chamada  
  
## <a name="description"></a>Descrição  
 A duração média das chamadas para esta operação. A duração média é calculada com base na equação: (N1-N0)/(D1-D0).  
  
> [!WARNING]
>  Quando usado em um serviço WCF assíncrono o contador de duração de chamadas sempre retornará -1.  
  
## <a name="see-also"></a>Consulte também  
 [PERF_AVERAGE_TIMER](http://go.microsoft.com/fwlink/?LinkId=95015)
---
title: 'Ponto de extremidade: chamadas com falha'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 271e6284-9c4b-465f-b619-069e1555a5e4
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d62eb1ad10c7112696d8fa2a358db4c88ee86cb3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-calls-faulted"></a>Ponto de extremidade: chamadas com falha
Nome do contador: Chamadas com falha.  
  
## <a name="description"></a>Descrição  
 Número de chamadas para este ponto de extremidade que retornaram falhas. Em [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] aplicativos, métodos de serviço se comunicam usando mensagens de falha SOAP de informações de erro de processamento. Falhas de SOAP são tipos de mensagem que estão incluídos nos metadados para uma operação de serviço e, portanto, crie um contrato de falha que os clientes podem usar para tornar a execução mais robusta ou interativo. Como falhas de SOAP são demonstradas para clientes em formato XML, eles são altamente interoperáveis.  
  
## <a name="see-also"></a>Consulte também  
 [Specifying and Handling Faults in Contracts and Services](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) (Especificando e lidando com falhas em contratos e serviços)
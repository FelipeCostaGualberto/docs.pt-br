---
title: Cláusula Distinct (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: 18d09d8018303aab6a69801c84c7ec9c6ea19ca9
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44083826"
---
# <a name="distinct-clause-visual-basic"></a>Cláusula Distinct (Visual Basic)
Restringe os valores da variável de intervalo para eliminar valores duplicados nas cláusulas de consulta subsequentes.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Distinct  
```  
  
## <a name="remarks"></a>Comentários  
 Você pode usar o `Distinct` cláusula para retornar uma lista de itens exclusivos. O `Distinct` cláusula faz com que a consulta a ignorar os resultados da consulta duplicados. O `Distinct` cláusula se aplica a valores duplicados para todos os campos especificados de retorno de `Select` cláusula. Se nenhum `Select` cláusula for especificada, o `Distinct` cláusula é aplicada à variável de intervalo para a consulta identificada no `From` cláusula. Se a variável de intervalo não é um tipo imutável, a consulta irá ignorar apenas um resultado de consulta se correspondem a todos os membros do tipo de um resultado de consulta existente.  
  
## <a name="example"></a>Exemplo  
 A expressão de consulta a seguir une uma lista de clientes e uma lista de pedidos do cliente. O `Distinct` cláusula é incluída para retornar uma lista de nomes exclusivos de clientes e datas de pedido.  
  
 [!code-vb[VbSimpleQuerySamples#20](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/distinct-clause_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Consultas](../../../visual-basic/language-reference/queries/index.md)  
 [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)

---
title: -refonly (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
ms.openlocfilehash: b22fb9ae24a04d9fe530811bf764352199c31813
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50200804"
---
# <a name="-refonly-visual-basic"></a>-refonly (Visual Basic)

O **- refonly** opção indica que a saída primária da compilação deve ser um assembly de referência em vez de um assembly de implementação. O parâmetro `-refonly` silenciosamente desabilita a geração de PDBs, uma vez que assemblies de referência não podem ser executados.

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>Sintaxe

```console
-refonly
```

## <a name="remarks"></a>Comentários

Visual Basic oferece suporte a `-refout` alternar a partir da versão 15.3.

Assemblies de referência são assemblies somente de metadados que contêm metadados, mas nenhum código de implementação. Eles incluem informações de tipo e membro para tudo, exceto tipos anônimos. O motivo para usar corpos `throw null` (em vez de nenhum corpo) é que PEVerify poderia ser executado e passado (validando, assim, a integridade dos metadados).

Assemblies de referência incluem um nível de conjunto [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) atributo. Esse atributo pode ser especificado na origem (assim, o compilador não precisará sintetizá-lo). Devido a esse atributo, tempos de execução se recusarão a carregar assemblies de referência para a execução (mas ainda podem ser carregados em um contexto de somente reflexão). As ferramentas que refletem nos assemblies precisam garantir que elas carreguem assemblies de referência como somente reflexão; Caso contrário, o tempo de execução gera uma <xref:System.BadImageFormatException>.

As opções `-refonly` e [`-refout`](refout-compiler-option.md) são mutualmente exclusivas.

## <a name="see-also"></a>Consulte também
[-refout](refout-compiler-option.md)   
[Compilador de linha de comando do Visual Basic](index.md)  
[Linhas de Comando de Compilação de Exemplo](sample-compilation-command-lines.md)   

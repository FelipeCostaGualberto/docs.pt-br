---
title: Abreviações de tipo (F#)
description: Saiba mais sobre as abreviações de tipo F# para dar um nome mais significativo de um tipo para facilitar a leitura do código.
ms.date: 05/16/2016
ms.openlocfilehash: 259cd6c84e22fc7c98e08255d3e0ded5b87af352
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2018
ms.locfileid: "48842418"
---
# <a name="type-abbreviations"></a>Abreviações de tipo

Um *abreviação de tipo* é um alias ou nome alternativo para um tipo.

## <a name="syntax"></a>Sintaxe

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a>Comentários

Você pode usar as abreviações de tipo para fornecer um tipo de um nome mais significativo, para facilitar a leitura do código. Você também pode usá-los para criar um nome fácil de usar para um tipo que de outra forma inconveniente para gravar. Além disso, você pode usar as abreviações de tipo para torná-lo mais fácil de alterar um tipo subjacente, sem alterar o código que usa o tipo. A seguir é uma abreviação de tipo simples.

Acessibilidade de abreviações de tipo padrão é `public`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

Abreviações de tipo podem incluir parâmetros genéricos, como no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

No código anterior, `Transform` é uma abreviação de tipo que representa uma função que aceita um único argumento de qualquer tipo e que retorna um único valor desse mesmo tipo.

Abreviações de tipo não são preservadas no código MSIL do .NET Framework. Portanto, quando você usa um assembly F# de outra linguagem do .NET Framework, você deve usar o nome do tipo subjacente para uma abreviação de tipo.

Abreviações de tipo também podem ser usadas em unidades de medida. Para obter mais informações, consulte [unidades de medida](units-of-measure.md).

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)

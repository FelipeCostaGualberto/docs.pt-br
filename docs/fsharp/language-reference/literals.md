---
title: Literais (F#)
description: Saiba mais sobre os tipos de literais no F# linguagem de programação.
ms.date: 05/16/2016
ms.openlocfilehash: 7a531cd63c5a4dc1123834d481fc998216b0d82d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131333"
---
# <a name="literals"></a>Literais

> [!NOTE]
> Os links de referência de API neste artigo você será levado ao MSDN (por enquanto).

Este tópico fornece uma tabela que mostra como especificar o tipo de um literal em F#.

## <a name="literal-types"></a>Tipos literais

A tabela a seguir mostra os tipos de literais no F#. Caracteres que representam dígitos em notação hexadecimal não diferenciam maiusculas de minúsculas; caracteres que identifica o tipo diferenciam maiusculas de minúsculas.

|Tipo|Descrição|Prefixo ou sufixo|Exemplos|
|----|-----------|----------------|--------|
|sbyte|inteiro com sinal de 8 bits|y|`86y`<br /><br />`0b00000101y`|
|byte|número de natural de 8 bits sem sinal|uy|`86uy`<br /><br />`0b00000101uy`|
|int16|inteiro com sinal de 16 bits|s|`86s`|
|uint16|número de natural de 16 bits sem sinal|us|`86us`|
|int<br /><br />int32|inteiro com sinal de 32 bits|l ou none|`86`<br /><br />`86l`|
|uint<br /><br />uint32|número de natural de 32 bits sem sinal|u ou ul|`86u`<br /><br />`86ul`|
|unativeint|ponteiro nativo como um número natural sem sinal|Cancelar|`0x00002D3Fun`|
|int64|inteiro com sinal de 64 bits|L|`86L`|
|uint64|número de natural de 64 bits sem sinal|UL|`86UL`|
|simples, float32|número de ponto flutuante de 32 bits|F ou f|`4.14F` ou `4.14f`|
|||LF|`0x00000000lf`|
|float; Double|número de ponto flutuante de 64 bits|nenhum|`4.14` ou `2.3E+32` ou `2.3e+32`|
|||LF|`0x0000000000000000LF`|
|bigint|inteiro não limitado a representação de 64 bits|I|`9999999999999999999999999999I`|
|decimal|número fracionário representado como um ponto fixo ou um número racional|M ou m|`0.7833M` ou `0.7833m`|
|Char|caractere Unicode|nenhum|`'a'`|
|Cadeia de Caracteres|Cadeia de caracteres Unicode|nenhum|`"text\n"`<br /><br />ou<br /><br />`@"c:\filename"`<br /><br />ou<br /><br />`"""<book title="Paradise Lost">"""`<br /><br />ou<br /><br />`"string1" + "string2"`<br /><br />Consulte também [cadeias de caracteres](Strings.md).|
|byte|Caractere ASCII|B|`'a'B`|
|byte[]|Cadeia de caracteres ASCII|B|`"text"B`|
|Cadeia de caracteres ou byte]|cadeia de caracteres textual|prefixo @|`@"\\server\share"` (Unicode)<br /><br />`@"\\server\share"B` (ASCII)|

## <a name="remarks"></a>Comentários

Cadeias de caracteres Unicode podem conter as codificações explícitas que você pode especificar usando `\u` seguido por um código hexadecimal de 16 bits ou codificações UTF-32 que você pode especificar usando `\U` seguido por um código hexadecimal de 32 bits que representa a Unicode par substituto.

Como de F# 3.1, você pode usar o `+` entrar para combinar literais de cadeia de caracteres. Você também pode usar o bit a bit ou (`|||`) operador para combinar sinalizadores de enum. Por exemplo, o código a seguir é legal no F# 3.1:

```fsharp
[<Literal>]
let literal1 = "a" + "b"

[<Literal>]
let fileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let literal2 = 1 ||| 64

[<Literal>]
let literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

Não é permitido o uso de outros operadores bit a bit.

## <a name="named-literals"></a>Literais nomeados

Os valores que devem ser constantes podem ser marcados com o [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) atributo. Este atributo tem o efeito de causar um valor a ser compilado como uma constante.

Em expressões de correspondência, identificadores que começam com caracteres minúsculos sempre são tratados como variáveis a serem associadas, em vez de como literais, portanto, você deve geralmente usar iniciais maiusculas ao definir literais.

## <a name="integers-in-other-bases"></a>Números inteiros em outras Bases

Inteiros com sinal de 32 bits também podem ser especificados em octal, hexadecimal ou binário usando um `0x`, `0o` ou `0b` do prefixo, respectivamente.

```fsharp
let Numbers = (0x9F, 0o77, 0b1010)
// Result: Numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a>Sublinhados em literais numéricos

Começando com F# 4.1, você pode separar dígitos com o caractere de sublinhado (`_`).

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a>Consulte também

- [Classe Core. literalattribute](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)

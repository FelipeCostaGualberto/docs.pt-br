---
title: "Globalização"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- globalization [.NET Framework], about globalization
- global applications, globalization
- international applications [.NET Framework], globalization
- world-ready applications, globalization
- application development [.NET Framework], globalization
- culture, globalization
ms.assetid: 4e919934-6b19-42f2-b770-275a4fae87c9
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a60284bf2db8f47dd17c04fad5cbd6db4970a8a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="globalization"></a>Globalização
A globalização envolve projetar e desenvolver um aplicativo preparado para o mundo que dá suporte a interfaces localizadas e dados regionais para usuários em várias culturas. Antes de iniciar a fase de design, você deve determinar a quais culturas seu aplicativo dará suporte. Embora um aplicativo seja direcionado para uma única cultura ou região por padrão, você pode projetá-lo e gravá-lo para que ele possa ser facilmente estendido para usuários em outras culturas ou regiões.  
  
 Como desenvolvedores, todos nós temos suposições sobre as interfaces do usuário e dados que são formados pelas nossas culturas. Por exemplo, para um desenvolvedor falante de inglês nos Estados Unidos, a serialização de dados de data e hora como uma cadeia de caracteres no formato `MM/dd/yyyy hh:mm:ss` parece perfeitamente razoável. No entanto, a desserialização essa cadeia de caracteres em um sistema em uma cultura diferente é provavelmente lançará um <xref:System.FormatException> exceção ou produzir dados imprecisos. A globalização nos permite identificar essas suposições específicas de culturas e nos certificarmos de que elas não afetem o design ou código de nosso aplicativo.  
  
 As seções a seguir discutem os principais problemas que você deve considerar e as práticas recomendadas que você pode seguir ao manipular cadeias de caracteres, valores de data/hora e valores numéricos em um aplicativo globalizado.  
  
-   [Tratando cadeias de caracteres](../../../docs/standard/globalization-localization/globalization.md#HandlingStrings)  
  
    -   [Usar Unicode internamente](../../../docs/standard/globalization-localization/globalization.md#Strings_Unicode)  
  
    -   [Usar arquivos de recurso](../../../docs/standard/globalization-localization/globalization.md#Strings_Resources)  
  
    -   [Procurando e comparando cadeias de caracteres](../../../docs/standard/globalization-localization/globalization.md#Strings_Searching)  
  
    -   [Testando igualdade das cadeias de caracteres](../../../docs/standard/globalization-localization/globalization.md#Strings_Equality)  
  
    -   [Ordenando e classificando cadeias de caracteres](../../../docs/standard/globalization-localization/globalization.md#Strings_Ordering)  
  
    -   [Evitar concatenação da cadeia de caracteres](../../../docs/standard/globalization-localization/globalization.md#Strings_Concat)  
  
-   [Tratando datas e horas](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes)  
  
    -   [Mantendo datas e horas](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes_Persist)  
  
    -   [Exibindo datas e horas](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes_Display)  
  
    -   [Reconhecimento de serialização e fuso horário](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes_TimeZones)  
  
    -   [Realizando aritmética de data e hora](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes_Arithmetic)  
  
-   [Tratando valores numéricos](../../../docs/standard/globalization-localization/globalization.md#Numbers)  
  
    -   [Exibindo valores numéricos](../../../docs/standard/globalization-localization/globalization.md#Numbers_Display)  
  
    -   [Mantendo valores numéricos](../../../docs/standard/globalization-localization/globalization.md#Numbers_Persist)  
  
-   [Trabalhando com configurações específicas da cultura](../../../docs/standard/globalization-localization/globalization.md#Cultures)  
  
<a name="HandlingStrings"></a>   
## <a name="handling-strings"></a>Tratando Cadeias de Caracteres  
 A manipulação de caracteres e cadeias de caracteres é um foco central da globalização, porque cada cultura ou região pode usar caracteres e conjuntos de caracteres diferentes e classificá-los de maneira diferente. Esta seção fornece recomendações para usar cadeias de caracteres em aplicativos globalizados.  
  
<a name="Strings_Unicode"></a>   
### <a name="use-unicode-internally"></a>Usar Unicode Internamente  
 Por padrão, o .NET Framework usa cadeias de caracteres Unicode. Uma cadeia de caracteres Unicode consiste em zero, um ou mais <xref:System.Char> objetos, cada um deles representa uma unidade de código UTF-16. Há uma representação Unicode para quase todos os caracteres em cada conjunto de caracteres no uso em todo o mundo.  
  
 Muitos aplicativos e sistemas operacionais, incluindo o sistema operacional Windows, também podem usar as páginas de código para representar conjuntos de caracteres. Páginas de código geralmente contêm valores ASCII padrão de 0x00 a 0x7F e mapeiam outros caracteres para os valores restantes de 0x80 a 0xFF. A interpretação dos valores de 0x80 a 0xFF depende da página de código específica. Por isso, se possível, evite usar as páginas de código em um aplicativo globalizado.  
  
 O exemplo a seguir ilustra os perigos da interpretação de dados de página de código quando a página de código padrão em um sistema é diferente da página de código no qual os dados foram salvos. (Para simular esse cenário, o exemplo especifica explicitamente páginas de código diferentes.) Primeiro, o exemplo define uma matriz que consiste dos caracteres em maiúsculas do alfabeto grego. Ele os codifica em uma matriz de bytes usando a página de código 737 (também conhecida como MS-DOS grego) e salva a matriz de bytes em um arquivo. Se o arquivo é recuperado e sua matriz de bytes é decodificada usando a página de código 737, os caracteres originais são restaurados. No entanto, se o arquivo é recuperado e sua matriz de bytes é decodificada usando a página de código 1252 (ou Windows-1252, que representa os caracteres do alfabeto latino), os caracteres originais são perdidos.  
  
 [!code-csharp[Conceptual.Globalization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/codepages1.cs#1)]
 [!code-vb[Conceptual.Globalization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/codepages1.vb#1)]  
  
 O uso do Unicode garante que as mesmas unidades de código sempre sejam mapeadas para os mesmos caracteres e que os mesmos caracteres sempre sejam mapeados para as mesmas matrizes de bytes.  
  
<a name="Strings_Resources"></a>   
### <a name="use-resource-files"></a>Usar Arquivos de Recurso  
 Mesmo se você estiver desenvolvendo um aplicativo que tenha como alvo uma única cultura ou a região, use arquivos de recurso para armazenar cadeias de caracteres e outros recursos que sejam exibidos na interface do usuário. Você nunca deve adicioná-los diretamente em seu código. Usar arquivos de recurso tem uma série de vantagens:  
  
-   Todas as cadeias de caracteres estão em um único local. Você não precisa pesquisar todo o seu código-fonte para identificar cadeias de caracteres para modificá-las para um determinado idioma ou cultura.  
  
-   Não há nenhuma necessidade de duplicar cadeias de caracteres. Os desenvolvedores que não usam arquivos de recursos frequentemente definem a mesma cadeia de caracteres em vários arquivos de código-fonte. Essa duplicação aumenta a probabilidade de que uma ou mais instâncias sejam esquecidas quando uma cadeia de caracteres é modificada.  
  
-   Você pode incluir recursos que não sejam cadeia de caracteres tais como imagens ou dados binários no arquivo de recurso, em vez de armazená-los em um arquivo autônomo separado, para que eles possam ser recuperados facilmente.  
  
 Usar arquivos de recurso tem vantagens específicas se você está criando um aplicativo localizado. Quando você implanta recursos em assemblies de satélite, o common language runtime seleciona automaticamente um recurso apropriado com base na cultura da interface do usuário atual, conforme definido pelo <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> propriedade. Desde que você fornece um recurso de específicos de cultura apropriado e instanciar corretamente um <xref:System.Resources.ResourceManager> de objeto ou usar uma classe de recursos fortemente tipados, o tempo de execução trata os detalhes de recuperar os recursos apropriados.  
  
 Para obter mais informações sobre como criar arquivos de recursos, consulte [Criar arquivos de recurso](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md). Para obter informações sobre como criar e implantar assemblies satélite, consulte [Criar assemblies satélite](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md) e [Empacotar e implantar recursos](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).  
  
<a name="Strings_Searching"></a>   
### <a name="searching-and-comparing-strings"></a>Procurando e Comparando Cadeias de Caracteres  
 Sempre que possível, você deve tratar cadeias de caracteres como cadeias de caracteres inteiras em vez de tratá-las como uma série de caracteres individuais. Isso é especialmente importante quando você classifica ou pesquisa subcadeias de caracteres, para evitar problemas associados à análise de caracteres combinados.  
  
> [!TIP]
>  Você pode usar o <xref:System.Globalization.StringInfo> classe para trabalhar com os elementos de texto, em vez de caracteres individuais em uma cadeia de caracteres.  
  
 Em comparações e pesquisas de cadeia de caracteres, um erro comum é tratar a cadeia de caracteres como um conjunto de caracteres, cada um dos quais é representada por um <xref:System.Char> objeto. Na verdade, um único caractere pode ser formado por uma, duas ou mais <xref:System.Char> objetos. Esses caracteres são encontrados com mais frequência em cadeias de caracteres de culturas cujos alfabetos consistem em caracteres fora do intervalo de caracteres do Latim Básico Unicode (U+0021 até U+007E). O exemplo a seguir tenta localizar o índice do caractere LETRA A MAIÚSCULA COM ACENTO GRAVE LATINA (U+00C0) em uma cadeia de caracteres. No entanto, esse caractere pode ser representado de duas maneiras diferentes: como uma única unidade de código (U+00C0) ou como um caractere composto (duas unidades de código: U+0021 e U+007E). Nesse caso, o caractere é representado na instância de cadeia de caracteres por dois <xref:System.Char> objetos, U + 0021 e U + 007E. O código de exemplo chama o <xref:System.String.IndexOf%28System.Char%29?displayProperty=nameWithType> e <xref:System.String.IndexOf%28System.String%29?displayProperty=nameWithType> sobrecargas para localizar a posição desse caractere na instância de cadeia de caracteres, mas elas retornam resultados diferentes. A primeira chamada do método tem um <xref:System.Char> argumento; ele executa uma comparação ordinal e, portanto, não é possível encontrar uma correspondência. A segunda chamada tem um <xref:System.String> argumento; ele executa uma comparação sensíveis à cultura e, portanto, localiza uma correspondência.  
  
 [!code-csharp[Conceptual.Globalization#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/search1.cs#18)]
 [!code-vb[Conceptual.Globalization#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/search1.vb#18)]  
  
 Você pode evitar alguns ambiguidade deste exemplo (chamadas de duas sobrecargas semelhantes de um método que retornar resultados diferentes), chamando uma sobrecarga que inclui um <xref:System.StringComparison> parâmetro, como o <xref:System.String.IndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> ou <xref:System.String.LastIndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> método.  
  
 No entanto, pesquisas nem sempre são com diferenciação entre culturas. Se a finalidade da pesquisa é tomar uma decisão de segurança ou permitir ou não o acesso a alguns recursos, a comparação deve ser ordinal, conforme discutido na próxima seção.  
  
<a name="Strings_Equality"></a>   
### <a name="testing-strings-for-equality"></a>Testando Igualdade das Cadeias de Caracteres  
 Se você quiser testar duas cadeias de caracteres de igualdade em vez de determinar como eles se comparam na ordem de classificação, use o <xref:System.String.Equals%2A?displayProperty=nameWithType> método em vez de um método de comparação de cadeia de caracteres como <xref:System.String.Compare%2A?displayProperty=nameWithType> ou <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType>.  
  
 Comparações de igualdade normalmente são executadas para acessar algum recurso de modo condicional. Por exemplo, você pode executar uma comparação de igualdade para verificar uma senha ou confirmar a existência de um arquivo. Essas comparações não linguísticas devem sempre ser de tipo ordinal, em vez de com diferenciação entre culturas. Em geral, você deve chamar a instância <xref:System.String.Equals%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> estático ou método <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> método com um valor de <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> para cadeias de caracteres, como senhas e um valor de <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> para cadeias de caracteres, como nomes de arquivo ou URIs.  
  
 Algumas vezes, as comparações de igualdade envolvem pesquisas ou comparações de subcadeia de caracteres em vez de chamadas para o <xref:System.String.Equals%2A?displayProperty=nameWithType> método. Em alguns casos, você pode usar uma subsequência de pesquisa para determinar se aquela subcadeia de caracteres é igual a uma outra cadeia de caracteres. Se a finalidade desta comparação é não linguística, a pesquisa também deve ser ordinal em vez de com diferenciação entre culturas.  
  
 O exemplo a seguir ilustra o perigo de uma pesquisa com diferenciação entre culturas em dados não linguísticos. O método `AccessesFileSystem` é projetado para proibir o acesso de URIs que começam com a subcadeia de caracteres "FILE" ao sistema de arquivos. Para fazer isso, ele executa uma comparação com diferenciação entre culturas mas sem diferenciação de maiúsculas e minúsculas do início da URI com a cadeia de caracteres "FILE". Já que um URI que acessa o sistema de arquivos pode começar com "FILE:" ou "file:", a suposição implícita é que esse "i" (U+0069) é sempre o equivalente em minúsculas de "I" (U+0049). No entanto, em turco e azerbaidjano, a versão maiúscula de "i" é "İ" (U+0130). Devido a essa discrepância, a comparação com diferenciação entre culturas permite o acesso ao sistema de arquivos quando ele deve ser proibido.  
  
 [!code-csharp[Conceptual.Globalization#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals1.cs#12)]
 [!code-vb[Conceptual.Globalization#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals1.vb#12)]  
  
 Você pode evitar esse problema ao executar uma comparação ordinal que diferencia maiúsculas de minúsculas, conforme mostra o exemplo a seguir.  
  
 [!code-csharp[Conceptual.Globalization#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals2.cs#13)]
 [!code-vb[Conceptual.Globalization#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals2.vb#13)]  
  
<a name="Strings_Ordering"></a>   
### <a name="ordering-and-sorting-strings"></a>Ordenando e Classificando Cadeias de Caracteres  
 Normalmente, cadeias de caracteres ordenadas que devem ser exibidas na interface do usuário devem ser classificadas com base na cultura. A maior parte do tempo, essas comparações de cadeia de caracteres são tratadas implicitamente pelo .NET Framework ao chamar um método que classifica as cadeias de caracteres, como <xref:System.Array.Sort%2A?displayProperty=nameWithType> ou <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType>. Por padrão, as cadeias de caracteres são classificadas pelo uso das convenções de classificação da cultura atual. O exemplo a seguir ilustra a diferença entre quando uma matriz de cadeias de caracteres é classificada usando as convenções das culturas Inglês (Estados Unidos) e Sueco (Suécia).  
  
 [!code-csharp[Conceptual.Globalization#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sort1.cs#14)]
 [!code-vb[Conceptual.Globalization#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sort1.vb#14)]  
  
 Comparação de cadeia de caracteres sensíveis à cultura é definida pelo <xref:System.Globalization.CompareInfo> objeto, que é retornado por cada cultura <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> propriedade. Comparações de cadeia de caracteres sensíveis à cultura que usam o <xref:System.String.Compare%2A?displayProperty=nameWithType> sobrecargas do método também use o <xref:System.Globalization.CompareInfo> objeto.  
  
 O .NET Framework usa tabelas para realizar classificações com diferenciação de cultura em dados de cadeia de caracteres. O conteúdo dessas tabelas, que contêm dados sobre os pesos de classificação e normalização de cadeias de caracteres, é determinado pela versão do padrão Unicode implementada por uma versão específica do .NET Framework. A tabela a seguir lista as versões do Unicode implementadas pelas versões especificadas do .NET Framework. Observe que essa lista de versões com suporte do Unicode aplica-se somente à comparação e classificação de caracteres. ela não se aplica à classificação de caracteres Unicode por categoria. Para obter mais informações, consulte a seção "Cadeias de caracteres e o Unicode padrão" o <xref:System.String> artigo.  
  
|Versão do .NET Framework|Sistema operacional|Versão Unicode|  
|----------------------------|----------------------|---------------------|  
|.NET Framework 2.0|Todos os sistemas operacionais|Unicode 4.1|  
|.NET Framework 3.0|Todos os sistemas operacionais|Unicode 4.1|  
|.NET Framework 3,5|Todos os sistemas operacionais|Unicode 4.1|  
|.NET Framework 4|Todos os sistemas operacionais|Unicode 5.0|  
|.NET Framework 4.5|[!INCLUDE[win7](../../../includes/win7-md.md)]|Unicode 5.0|  
|.NET Framework 4.5|[!INCLUDE[win8](../../../includes/win8-md.md)]|Unicode 6.0|  
  
 No [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], a comparação e classificação de cadeias de caracteres depende do sistema operacional. O [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] em execução no [!INCLUDE[win7](../../../includes/win7-md.md)] recupera dados de suas próprias tabelas, que implementam o Unicode 5.0. O [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] em execução no [!INCLUDE[win8](../../../includes/win8-md.md)] recupera dados de tabelas do sistema operacional, que implementam o Unicode 6.0. Se você serializar dados classificados sensíveis à cultura, você pode usar o <xref:System.Globalization.SortVersion> classe para determinar quando os dados serializados precisam ser classificada para que seja consistente com o .NET Framework e ordem de classificação do sistema operacional. Para obter um exemplo, consulte o <xref:System.Globalization.SortVersion> tópico sobre a classe.  
  
 Se seu aplicativo executa amplos tipos específicos de cultura de dados de cadeia de caracteres, você pode trabalhar com o <xref:System.Globalization.SortKey> classe para comparar cadeias de caracteres. Uma chave de classificação reflete os pesos de classificação específicos de uma determinada cultura, incluindo os pesos alfabético, de maiúsculas e minúsculas e de diacríticos de uma determinada cadeia de caracteres. Como comparações usando chaves de classificação são binárias, eles são mais rápidos do que comparações que usam um <xref:System.Globalization.CompareInfo> de objeto implicitamente ou explicitamente. Criar uma chave de classificação específicas de cultura para uma determinada cadeia de caracteres, passando a cadeia de caracteres para o <xref:System.Globalization.CompareInfo.GetSortKey%2A?displayProperty=nameWithType> método.  
  
 O exemplo a seguir é semelhante ao exemplo anterior. No entanto, em vez de chamar o <xref:System.Array.Sort%28System.Array%29?displayProperty=nameWithType> método, que chama implicitamente o <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType> método, ele define um <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementação que compara as chaves de classificação, que ele cria e passa para o <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Collections.Generic.IComparer%7B%60%600%7D%29?displayProperty=nameWithType> método.  
  
 [!code-csharp[Conceptual.Globalization#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sortkey1.cs#15)]
 [!code-vb[Conceptual.Globalization#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sortkey1.vb#15)]  
  
<a name="Strings_Concat"></a>   
### <a name="avoid-string-concatenation"></a>Evitar Concatenação da Cadeia de Caracteres  
 Se possível, evite usar cadeias de caracteres compostas compiladas em tempo de execução de frases concatenadas. Cadeias de caracteres compostas são difíceis de localizar, porque elas muitas vezes pressupõem uma ordem gramatical no idioma original do aplicativo que não se aplica a outros idiomas localizados.  
  
<a name="DatesAndTimes"></a>   
## <a name="handling-dates-and-times"></a>Tratando Datas e Horas  
 Como você lida com valores de data/hora depende de como estão esses valores: persistentes ou exibidos na interface do usuário. Esta seção examina os dois usos. Ela também aborda como você pode manipular diferenças de fuso horário e operações aritméticas ao trabalhar com datas e horas.  
  
<a name="DatesAndTimes_Display"></a>   
### <a name="displaying-dates-and-times"></a>Exibindo Datas e Horas  
 Normalmente, quando as datas e horas são exibidas na interface do usuário, você deve usar as convenções de formatação da cultura do usuário, que é definido pelo <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> propriedade e o <xref:System.Globalization.DateTimeFormatInfo> objeto retornado pelo `CultureInfo.CurrentCulture.DateTimeFormat` propriedade. As convenções de formatação da cultura atual são usadas automaticamente quando você formata uma data usando qualquer um dos seguintes métodos:  
  
-   Sem o parâmetro <xref:System.DateTime.ToString?displayProperty=nameWithType> método  
  
-   O <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> método, que inclui uma cadeia de caracteres de formato  
  
-   Sem o parâmetro <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType> método  
  
-   O <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType>, que inclui uma cadeia de caracteres de formato  
  
-   O recurso de [formatação de composição](../../../docs/standard/base-types/composite-formatting.md), quando ele é usado com datas  
  
 O exemplo a seguir exibe dados do pôr-do-sol e nascer do sol duas vezes para 11 de outubro de 2012. Primeiro, ele define a cultura atual para Croata (Croácia) e, em seguida, para Inglês (Grã-Bretanha). Em cada caso, as datas e horas são exibidas no formato apropriado para aquela cultura.  
  
 [!code-csharp[Conceptual.Globalization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates1.cs#2)]
 [!code-vb[Conceptual.Globalization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates1.vb#2)]  
  
<a name="DatesAndTimes_Persist"></a>   
### <a name="persisting-dates-and-times"></a>Mantendo Datas e Horas  
 Você nunca deve persistir dados de data e hora em um formato que possa variar de acordo com a cultura. Esse é um erro de programação comum, que resulta em dados corrompidos ou em uma exceção de tempo de execução. O exemplo a seguir serializa duas datas, 9 de janeiro de 2013 e 18 de agosto de 2013, como cadeias de caracteres usando as convenções de formatação da cultura Inglês (Estados Unidos). Quando os dados são recuperados e analisados usando as convenções da cultura Inglês (Estados Unidos), eles são restaurado com êxito. No entanto, quando eles são recuperados e analisados usando as convenções da cultura Inglês (Reino Unido), a primeira data é interpretada incorretamente como 1º de setembro e a segunda falha ao ser analisada porque o calendário gregoriano não tem um décimo oitavo mês.  
  
 [!code-csharp[Conceptual.Globalization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates2.cs#3)]
 [!code-vb[Conceptual.Globalization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates2.vb#3)]  
  
 Você pode evitar esse problema de qualquer uma de três maneiras:  
  
-   Serialize a data e hora no formato binário em vez de uma cadeia de caracteres.  
  
-   Salve e analise a representação da data e hora usando uma cadeia de caracteres de formato personalizado, que é a mesma independentemente da cultura do usuário.  
  
-   Salve a cadeia de caracteres usando as convenções de formatação da cultura invariável.  
  
 O exemplo a seguir ilustra a última abordagem. Ele usa as convenções de formatação da cultura invariável retornada por estático <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> propriedade.  
  
 [!code-csharp[Conceptual.Globalization#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates3.cs#4)]
 [!code-vb[Conceptual.Globalization#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates3.vb#4)]  
  
<a name="DatesAndTimes_TimeZones"></a>   
### <a name="serialization-and-time-zone-awareness"></a>Reconhecimento de Serialização e Fuso Horário  
 Um valor de data/hora pode ter várias interpretações, variando de uma hora geral ("As lojas abrem em 2 de janeiro de 2013, às 9h") para um ponto específico no tempo ("Data de nascimento: 2 de janeiro de 2013, 6h32"). Quando um valor temporal representa um ponto específico no tempo e você o restaura de um valor serializado, você deve certificar-se de que ele representa o mesmo ponto no tempo, independentemente da localização geográfica ou do fuso horário do usuário.  
  
 O exemplo a seguir ilustra esse problema. Ele salva um único valor de data/hora local como uma cadeia de caracteres em três [formatos padrão](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) ("G" para data geral com tempo em formato longo, "s" para data/hora classificável e "o" para data/hora de ida e volta), bem como no formato binário.  
  
 [!code-csharp[Conceptual.Globalization#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates4.cs#10)]
 [!code-vb[Conceptual.Globalization#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates4.vb#10)]  
  
 Quando os dados são restaurados em um sistema no mesmo fuso horário do sistema no qual eles foram serializados, os valores de data/hora desserializados refletem com precisão o valor original, como se pode ver na saída:  
  
```  
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified  
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified  
'2013-03-30T18:00:00.0000000-07:00' --> 3/30/2013 6:00:00 PM Local  
  
3/30/2013 6:00:00 PM Local  
```  
  
 No entanto, se você restaurar os dados em um sistema em um fuso horário diferente, apenas o valor de data/hora que tiver sido formatado com a cadeia de caracteres de formato padrão "o" (ida e volta) preservará informações de fuso horário e, por isso, representará o mesmo instante no tempo. Aqui está a saída quando os dados de data e hora são restaurados em um sistema no fuso horário padrão românico:  
  
```  
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified  
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified  
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local  
  
3/30/2013 6:00:00 PM Local  
```  
  
 Para refletir com precisão um valor de data/hora que representa um único ponto de tempo, independentemente do fuso horário do sistema no qual os dados são desserializados, você pode realizar qualquer uma das seguintes ações:  
  
-   Salvar o valor como uma cadeia de caracteres usando a cadeia de caracteres de formato padrão "o" (ida e volta). Em seguida, desserializá-lo no sistema de destino.  
  
-   Convertê-lo para UTC e salvá-lo como uma cadeia de caracteres usando a cadeia de caracteres de formato padrão "r" (RFC1123). Em seguida, desserializá-lo no sistema de destino e convertê-lo para o horário local.  
  
-   Convertê-lo em UTC e salvá-lo como uma cadeia de caracteres usando a cadeia de caracteres de formato padrão "u" (classificável universal). Em seguida, desserializá-lo no sistema de destino e convertê-lo para o horário local.  
  
-   Convertê-lo em UTC e salvá-lo no formato binário. Em seguida, desserializá-lo no sistema de destino e convertê-lo para o horário local.  
  
 O exemplo a seguir ilustra cada uma das técnicas.  
  
 [!code-csharp[Conceptual.Globalization#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates8.cs#11)]
 [!code-vb[Conceptual.Globalization#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates8.vb#11)]  
  
 Quando os dados são serializados em um sistema no fuso horário padrão do Pacífico e desserializados em um sistema no fuso horário padrão românico, o exemplo exibe a seguinte saída:  
  
```  
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local  
'Sun, 31 Mar 2013 01:00:00 GMT' --> 3/31/2013 3:00:00 AM Local  
'2013-03-31 01:00:00Z' --> 3/31/2013 3:00:00 AM Local  
  
3/31/2013 3:00:00 AM Local  
```  
  
 Para obter mais informações, consulte [Convertendo horários entre fusos horários](../../../docs/standard/datetime/converting-between-time-zones.md).  
  
<a name="DatesAndTimes_Arithmetic"></a>   
### <a name="performing-date-and-time-arithmetic"></a>Realizando Aritmética de Data e Hora  
 Tanto o <xref:System.DateTime> e <xref:System.DateTimeOffset> tipos dão suporte a operações aritméticas. Você pode calcular a diferença entre dois valores de data ou então você pode adicionar ou subtrair intervalos de tempo específicos para ou de um valor de data. No entanto, operações aritméticas em valores de data/hora não levam em consideração fusos horários e regras de ajuste de fuso horário. Por isso, data e hora em valores que representam pontos no tempo podem retornar resultados imprecisos.  
  
 Por exemplo, ocorre a transição da hora padrão do Pacífico para o horário de verão do Pacífico no segundo domingo de março, que é de 10 de março do ano de 2013. Conforme demonstrado pelo exemplo a seguir, se você calcular a data e hora, o resultado será 48 horas após 9 de março de 2013 às 10:30 da manhã. Em um sistema no fuso horário padrão do Pacífico, o resultado, 11 de março de 2013 às 10:30 da manhã, não leva em consideração o ajuste de horário que ocorre nesse intermédio.  
  
 [!code-csharp[Conceptual.Globalization#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates5.cs#8)]
 [!code-vb[Conceptual.Globalization#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates5.vb#8)]  
  
 Para garantir que uma operação aritmética em valores de data/hora produza resultados precisos, siga estas etapas:  
  
1.  Converta o horário no fuso horário de origem em UTC.  
  
2.  Execute a operação aritmética.  
  
3.  Se o resultado for um valor de data/hora, converta-o de UTC para a hora no fuso horário de origem.  
  
 O exemplo a seguir é semelhante ao exemplo anterior, exceto pelo fato de que ele segue essas três etapas para adicionar corretamente 48 horas a 9 de março de 2013, às 10:30 da manhã.  
  
 [!code-csharp[Conceptual.Globalization#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates6.cs#9)]
 [!code-vb[Conceptual.Globalization#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates6.vb#9)]  
  
 Para obter mais informações, consulte [Executando operações aritméticas com datas e horas](../../../docs/standard/datetime/performing-arithmetic-operations.md).  
  
### <a name="using-culture-sensitive-names-for-date-elements"></a>Usando Nomes Sensíveis à Cultura para Elementos de Data  
 Seu aplicativo pode precisar exibir o nome do mês ou dia da semana. Para fazer isso, código como o mostrado a seguir é comum.  
  
 [!code-csharp[Conceptual.Globalization#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname1.cs#19)]
 [!code-vb[Conceptual.Globalization#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname1.vb#19)]  
  
 No entanto, esse código sempre retorna os nomes dos dias da semana em inglês. O código que extrai o nome do mês é muitas vezes ainda mais inflexível. Com frequência, ele assume um calendário de doze meses com nomes dos meses em um idioma específico.  
  
 Usando [cadeias de caracteres de formato de data e hora personalizado](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) ou as propriedades da <xref:System.Globalization.DateTimeFormatInfo> do objeto, é fácil extrair as cadeias de caracteres que refletem os nomes dos dias da semana ou meses na cultura do usuário, como mostra o exemplo a seguir. Altera a cultura atual para o francês (França) e exibe o nome do dia da semana e o nome do mês para 1º de julho de 2013.  
  
 [!code-csharp[Conceptual.Globalization#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname2.cs#20)]
 [!code-vb[Conceptual.Globalization#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname2.vb#20)]  
  
<a name="Numbers"></a>   
## <a name="handling-numeric-values"></a>Tratando Valores Numéricos  
 Como você lida com números depende de como estão esses valores: persistentes ou exibidos na interface do usuário. Esta seção examina os dois usos.  
  
> [!NOTE]
>  Na análise e operações de formatação, o .NET Framework reconhece somente os caracteres latinos básicos de 0 a 9 (U+0030 a U+0039) como dígitos numéricos.  
  
<a name="Numbers_Display"></a>   
### <a name="displaying-numeric-values"></a>Exibindo Valores Numéricos  
 Normalmente, quando os números são exibidos na interface do usuário, você deve usar as convenções de formatação da cultura do usuário, que é definido pelo <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> propriedade e o <xref:System.Globalization.NumberFormatInfo> objeto retornado pelo `CultureInfo.CurrentCulture.NumberFormat` propriedade. As convenções de formatação da cultura atual são usadas automaticamente quando você formata uma data usando qualquer um dos seguintes métodos:  
  
-   O método sem parâmetro `ToString` de qualquer tipo numérico  
  
-   O método `ToString(String)` de qualquer tipo numérico, que inclui uma cadeia de caracteres de formato como um argumento  
  
-   O recurso de [formatação de composição](../../../docs/standard/base-types/composite-formatting.md), quando ele é usado com valores numéricos  
  
 O exemplo a seguir exibe a temperatura média por mês em Paris, na França. Ele primeiro define a cultura atual para Francês (França) antes de exibir os dados e, em seguida, define-a como Inglês (Estados Unidos). Em cada caso, as temperaturas e os nomes dos meses são exibidos no formato apropriado para aquela cultura. Observe que as duas culturas usam separadores decimais diferentes no valor da temperatura. Observe também que o exemplo usa "MMMM" data e hora de cadeia de caracteres de formato personalizado para exibir o nome completo do mês, e que aloca a quantidade apropriada de espaço para o nome do mês na cadeia de caracteres de resultado, determinando o comprimento do nome do mês mais longo de <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A?displayProperty=nameWithType></C0>matriz.  
  
 [!code-csharp[Conceptual.Globalization#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers1.cs#5)]
 [!code-vb[Conceptual.Globalization#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers1.vb#5)]  
  
<a name="Numbers_Persist"></a>   
### <a name="persisting-numeric-values"></a>Mantendo Valores Numéricos  
 Você nunca deve persistir dados numéricos em um formato específico de cultura. Esse é um erro de programação comum, que resulta em dados corrompidos ou em uma exceção de tempo de execução. O exemplo a seguir gera dez números de ponto flutuante aleatórios e, em seguida, serializa-os como cadeias de caracteres usando as convenções de formatação da cultura Inglês (Estados Unidos). Quando os dados são recuperados e analisados usando as convenções da cultura Inglês (Estados Unidos), eles são restaurado com êxito. No entanto, quando eles são recuperados e analisados usando as convenções da cultura Francês (França), nenhum dos números pode ser analisado porque as culturas usam separadores decimais diferentes.  
  
 [!code-csharp[Conceptual.Globalization#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers2.cs#6)]
 [!code-vb[Conceptual.Globalization#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers2.vb#6)]  
  
 Para evitar esse problema, você pode usar uma destas técnicas:  
  
-   Salve e analise a representação do número usando uma cadeia de caracteres de formato personalizado, que é a mesma independentemente da cultura do usuário.  
  
-   Salve o número como uma cadeia de caracteres usando as convenções de formatação da cultura invariável, que é retornado pelo <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> propriedade.  
  
-   Serialize o número em formato binário em vez do formato de cadeia de caracteres.  
  
 O exemplo a seguir ilustra a última abordagem. Ele serializa a matriz de <xref:System.Double> valores e, em seguida, desserializa e exibe-los usando as convenções de formatação do inglês (Estados Unidos) e culturas francês (França).  
  
 [!code-csharp[Conceptual.Globalization#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers3.cs#7)]
 [!code-vb[Conceptual.Globalization#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers3.vb#7)]  
  
 A serialização de valores de moeda é um caso especial. Já que um valor de moeda depende da unidade monetária na qual ele é expresso, faz pouco sentido para tratá-lo como um valor numérico independente. No entanto, se você salvar um valor de moeda como uma cadeia de caracteres formatada que inclui um símbolo de moeda, ele não poderá ser desserializado em um sistema cuja cultura padrão use um símbolo de moeda diferente, assim como mostra o exemplo a seguir.  
  
 [!code-csharp[Conceptual.Globalization#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency1.cs#16)]
 [!code-vb[Conceptual.Globalization#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency1.vb#16)]  
  
 Em vez disso, você deve serializar o valor numérico juntamente com algumas informações culturais como o nome da cultura, para que o valor e o símbolo de moeda possam ser desserializados independentemente da cultura atual. O exemplo a seguir faz isso definindo uma `CurrencyValue` estrutura com dois membros: o <xref:System.Decimal> valor e o nome da cultura à qual pertence o valor.  
  
 [!code-csharp[Conceptual.Globalization#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency2.cs#17)]
 [!code-vb[Conceptual.Globalization#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency2.vb#17)]  
  
<a name="Cultures"></a>   
## <a name="working-with-culture-specific-settings"></a>Trabalhando com Configurações Específicas da Cultura  
 No .NET Framework, o <xref:System.Globalization.CultureInfo> classe representa uma cultura específica ou região. Algumas de suas propriedades retornam objetos que fornecem informações específicas sobre alguns aspectos de uma cultura:  
  
-   O <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> propriedade retorna um <xref:System.Globalization.CompareInfo> objeto que contém informações sobre como a cultura compara e ordena as cadeias de caracteres.  
  
-   O <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> propriedade retorna um <xref:System.Globalization.DateTimeFormatInfo> objeto que fornece informações específicas da cultura usadas na formatação de data e hora.  
  
-   O <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> propriedade retorna um <xref:System.Globalization.NumberFormatInfo> objeto que fornece informações específicas da cultura usadas na formatação de dados numéricos.  
  
-   O <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType> propriedade retorna um <xref:System.Globalization.TextInfo> objeto que fornece informações sobre a cultura de gravação do sistema.  
  
 Em geral, não faça suposições sobre os valores de específicos <xref:System.Globalization.CultureInfo> propriedades e seus objetos relacionados. Em vez disso, você deve exibir os dados específicos da cultura como sujeitos a alterações, por estes motivos:  
  
-   Valores de propriedade individuais estão sujeitos a alteração e revisão ao longo do tempo; conforme os dados são corrigidos, dados melhores ficam disponíveis, ou então as convenções específicas da cultura são alteradas.  
  
-   Valores de propriedade individuais podem variar entre as versões das versões do sistema operacional ou do .NET Framework.  
  
-   O .NET Framework dá suporte a culturas de substituição. Isso torna possível definir uma nova cultura personalizada que complementa as culturas padrão existentes ou substitui completamente uma cultura padrão existente.  
  
-   O usuário pode personalizar configurações específicas da cultura usando o aplicativo **Região e Idioma** no Painel de Controle. Quando você instancia um <xref:System.Globalization.CultureInfo> do objeto, você pode determinar se ele reflete essas personalizações do usuário chamando o <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> construtor. Normalmente, para aplicativos de usuário final, você deve respeitar as preferências do usuário para que sejam apresentados ao usuário dados em um formato que ele espera.  
  
## <a name="see-also"></a>Consulte também  
 [Globalização e localização](../../../docs/standard/globalization-localization/index.md)  
 [Melhores práticas para o uso de cadeias de caracteres](../../../docs/standard/base-types/best-practices-strings.md)
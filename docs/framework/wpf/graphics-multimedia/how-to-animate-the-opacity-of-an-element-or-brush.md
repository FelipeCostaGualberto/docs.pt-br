---
title: Como animar a opacidade de um elemento ou pincel
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- opacity [WPF], animating
- animation [WPF], Opacity property
ms.assetid: 572af23b-39dd-48d1-9db5-4bca56a4b3d3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 808d29292e176af8d3af1fc0f4a02c48ee05ea35
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-animate-the-opacity-of-an-element-or-brush"></a>Como animar a opacidade de um elemento ou pincel
Para um elemento de framework esmaecimento e sair do modo de exibição, é possível animar seu <xref:System.Windows.UIElement.Opacity%2A> pode animar a propriedade ou o <xref:System.Windows.Media.Brush.Opacity%2A> propriedade do <xref:System.Windows.Media.Brush> (ou pincéis) usado para pintar a ele. Animar a opacidade do elemento facilita e seus filhos esmaecem e aparecem na exibição, mas animar o pincel usado para pintar o elemento permite a ser mais seletivo sobre qual parte do elemento desaparece. Por exemplo, você poderia animar a opacidade de um pincel usado para pintar a tela de fundo de um botão. Isso faria com que a tela de fundo do botão esmaecesse e aparecesse na exibição, deixando o texto completamente opaco.  
  
> [!NOTE]
>  Animação de <xref:System.Windows.Media.Brush.Opacity%2A> de um <xref:System.Windows.Media.Brush> fornece benefícios de desempenho sobre animação a <xref:System.Windows.UIElement.Opacity%2A> propriedade de um elemento.  
  
 No exemplo a seguir, dois botões são animados de modo que desaparecem e saem do modo de exibição. A opacidade do primeiro <xref:System.Windows.Controls.Button> é animado de `1.0` para `0.0` em um <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de cinco segundos. O segundo botão também é animado, mas a opacidade de SolidColorBrush usado para pintar o <xref:System.Windows.Controls.Control.Background%2A> é animada em vez da opacidade do botão inteiro. Quando o exemplo é executado, o primeiro botão esmaece e desaparece completamente da exibição, enquanto apenas a tela de fundo do segundo botão esmaece e desaparece da exibição. Seu texto e borda permanecem totalmente opacos.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[timingbehaviors_snip#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/OpacityAnimationExample.xaml#10)]  
  
 O código foi omitido neste exemplo. O exemplo completo também mostra como animar a opacidade de um <xref:System.Windows.Media.Color> dentro de um <xref:System.Windows.Media.LinearGradientBrush>.  Para ver o exemplo completo, consulte [Animando a opacidade de um exemplo de elemento](http://go.microsoft.com/fwlink/?LinkID=159968).
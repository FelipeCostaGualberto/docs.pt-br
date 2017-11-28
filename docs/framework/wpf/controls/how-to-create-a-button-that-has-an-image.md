---
title: "Como criar um botão que tenha uma imagem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Button controls [WPF], creating
ms.assetid: 607a193c-4098-4dd8-8dc0-51256cec2020
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fa3aa5454629d53fd8864df6a4f204e22028208f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-button-that-has-an-image"></a><span data-ttu-id="4128d-102">Como criar um botão que tenha uma imagem</span><span class="sxs-lookup"><span data-stu-id="4128d-102">How to: Create a Button That Has an Image</span></span>
<span data-ttu-id="4128d-103">Este exemplo mostra como incluir uma imagem em um <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="4128d-103">This example shows how to include an image on a <xref:System.Windows.Controls.Button>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4128d-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4128d-104">Example</span></span>  
 <span data-ttu-id="4128d-105">O exemplo a seguir cria dois <xref:System.Windows.Controls.Button> controles.</span><span class="sxs-lookup"><span data-stu-id="4128d-105">The following example creates two <xref:System.Windows.Controls.Button> controls.</span></span> <span data-ttu-id="4128d-106">Um <xref:System.Windows.Controls.Button> contém texto e o outro contém uma imagem.</span><span class="sxs-lookup"><span data-stu-id="4128d-106">One <xref:System.Windows.Controls.Button> contains text and the other contains an image.</span></span> <span data-ttu-id="4128d-107">A imagem está em uma pasta chamada dados, que é uma subpasta da pasta de projeto de exemplo.</span><span class="sxs-lookup"><span data-stu-id="4128d-107">The image is in a folder called data, which is a subfolder of the example’s project folder.</span></span> <span data-ttu-id="4128d-108">Quando um usuário clica o <xref:System.Windows.Controls.Button> que tem a imagem, o plano de fundo e o texto do outro <xref:System.Windows.Controls.Button> alterar.</span><span class="sxs-lookup"><span data-stu-id="4128d-108">When a user clicks the <xref:System.Windows.Controls.Button> that has the image, the background and the text of the other <xref:System.Windows.Controls.Button> change.</span></span>  
  
 <span data-ttu-id="4128d-109">Este exemplo cria <xref:System.Windows.Controls.Button> controla usando marcação, mas usa o código para escrever o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="4128d-109">This example creates <xref:System.Windows.Controls.Button> controls by using markup but uses code to write the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handlers.</span></span>  
  
 [!code-xaml[BtnColor#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml#4)]  
  
 [!code-csharp[BtnColor#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml.cs#6)]
 [!code-vb[BtnColor#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BtnColor/VisualBasic/Pane1.xaml.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="4128d-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4128d-110">See Also</span></span>  
 [<span data-ttu-id="4128d-111">Controles</span><span class="sxs-lookup"><span data-stu-id="4128d-111">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)  
 [<span data-ttu-id="4128d-112">Biblioteca de controles</span><span class="sxs-lookup"><span data-stu-id="4128d-112">Control Library</span></span>](../../../../docs/framework/wpf/controls/control-library.md)
---
title: Como detectar quando o texto em um TextBox foi alterado
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
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 92fc8995ab75cc25bac3bb21b1646052822c3721
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a><span data-ttu-id="41dd3-102">Como detectar quando o texto em um TextBox foi alterado</span><span class="sxs-lookup"><span data-stu-id="41dd3-102">How to: Detect When Text in a TextBox Has Changed</span></span>
<span data-ttu-id="41dd3-103">Este exemplo mostra uma maneira de usar o <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> evento para executar um método sempre que o texto em uma <xref:System.Windows.Controls.TextBox> controle foi alterado.</span><span class="sxs-lookup"><span data-stu-id="41dd3-103">This example shows one way to use the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event to execute a method whenever the text in a <xref:System.Windows.Controls.TextBox> control has changed.</span></span>  
  
 <span data-ttu-id="41dd3-104">Na classe por trás do código para o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que contém o <xref:System.Windows.Controls.TextBox> controle que você deseja monitorar as alterações, insira um método a ser chamado sempre que o <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> evento ser acionado.</span><span class="sxs-lookup"><span data-stu-id="41dd3-104">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="41dd3-105">Esse método deve ter uma assinatura que corresponde a esperada pelo <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span><span class="sxs-lookup"><span data-stu-id="41dd3-105">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>  
  
 <span data-ttu-id="41dd3-106">O manipulador de eventos é chamado sempre que o conteúdo do <xref:System.Windows.Controls.TextBox> controle for alterado, por um usuário ou programaticamente.</span><span class="sxs-lookup"><span data-stu-id="41dd3-106">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>  
  
 <span data-ttu-id="41dd3-107">**Observação:** esse evento é acionado quando o <xref:System.Windows.Controls.TextBox> controle é criado e preenchido inicialmente com o texto.</span><span class="sxs-lookup"><span data-stu-id="41dd3-107">**Note:** This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41dd3-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41dd3-108">Example</span></span>  
 <span data-ttu-id="41dd3-109">No [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] que define seu <xref:System.Windows.Controls.TextBox> controlar, especifique o <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> atributo com um valor que corresponda ao nome de método do manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="41dd3-109">In the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that defines your <xref:System.Windows.Controls.TextBox> control, specify the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> attribute with a value that matches the event handler method name.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextChangedXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]  
  
## <a name="example"></a><span data-ttu-id="41dd3-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41dd3-110">Example</span></span>  
 <span data-ttu-id="41dd3-111">Na classe por trás do código para o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que contém o <xref:System.Windows.Controls.TextBox> controle que você deseja monitorar as alterações, insira um método a ser chamado sempre que o <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> evento ser acionado.</span><span class="sxs-lookup"><span data-stu-id="41dd3-111">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="41dd3-112">Esse método deve ter uma assinatura que corresponde a esperada pelo <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span><span class="sxs-lookup"><span data-stu-id="41dd3-112">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
 [!code-vb[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]  
  
 <span data-ttu-id="41dd3-113">O manipulador de eventos é chamado sempre que o conteúdo do <xref:System.Windows.Controls.TextBox> controle for alterado, por um usuário ou programaticamente.</span><span class="sxs-lookup"><span data-stu-id="41dd3-113">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>  
  
 <span data-ttu-id="41dd3-114">**Observação:** esse evento é acionado quando o <xref:System.Windows.Controls.TextBox> controle é criado e preenchido inicialmente com o texto.</span><span class="sxs-lookup"><span data-stu-id="41dd3-114">**Note:** This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>  
  
 <span data-ttu-id="41dd3-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="41dd3-115">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41dd3-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41dd3-116">See Also</span></span>  
 <xref:System.Windows.Controls.TextChangedEventArgs>  
 [<span data-ttu-id="41dd3-117">Visão geral de TextBox</span><span class="sxs-lookup"><span data-stu-id="41dd3-117">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="41dd3-118">Visão geral de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="41dd3-118">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
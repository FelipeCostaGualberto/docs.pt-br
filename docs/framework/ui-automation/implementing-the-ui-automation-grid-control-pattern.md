---
title: "Implementando o Padrão de Controle Grid de Automação de Interface de Usuário"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, grid
- grid control pattern
- UI Automation, grid control pattern
ms.assetid: 234d11a0-7ce7-4309-8989-2f4720e02f78
caps.latest.revision: "27"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 123bc1454a58391bc6503fd3f60d477fd5498306
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a><span data-ttu-id="73824-102">Implementando o Padrão de Controle Grid de Automação de Interface de Usuário</span><span class="sxs-lookup"><span data-stu-id="73824-102">Implementing the UI Automation Grid Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="73824-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="73824-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="73824-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="73824-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="73824-105">Este tópico apresenta diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.IGridProvider>, incluindo informações sobre propriedades, métodos e eventos.</span><span class="sxs-lookup"><span data-stu-id="73824-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="73824-106">Links para referências adicionais são listadas no final da visão geral.</span><span class="sxs-lookup"><span data-stu-id="73824-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="73824-107">O <xref:System.Windows.Automation.GridPattern> padrão de controle é usado para oferecer suporte aos controles que atuam como contêineres para uma coleção de elementos filho.</span><span class="sxs-lookup"><span data-stu-id="73824-107">The <xref:System.Windows.Automation.GridPattern> control pattern is used to support controls that act as containers for a collection of child elements.</span></span> <span data-ttu-id="73824-108">Os filhos deste elemento devem implementar <xref:System.Windows.Automation.Provider.IGridItemProvider> e ser organizados em um sistema de coordenadas lógico bidimensional que pode ser percorrido por linha e coluna.</span><span class="sxs-lookup"><span data-stu-id="73824-108">The children of this element must implement <xref:System.Windows.Automation.Provider.IGridItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column.</span></span> <span data-ttu-id="73824-109">Para obter exemplos de controles que implementam este padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="73824-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="73824-110">Convenções e diretrizes de implementação</span><span class="sxs-lookup"><span data-stu-id="73824-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="73824-111">Ao implementar o padrão de controle de grade, observe as seguintes diretrizes e convenções:</span><span class="sxs-lookup"><span data-stu-id="73824-111">When implementing the Grid control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="73824-112">Coordenadas da grade são baseadas em zero com o superior esquerda (ou célula superior direita dependendo da localidade) tendo as coordenadas (0, 0).</span><span class="sxs-lookup"><span data-stu-id="73824-112">Grid coordinates are zero-based with the upper left (or upper right cell depending on locale) having coordinates (0, 0).</span></span>  
  
-   <span data-ttu-id="73824-113">Se uma célula estiver vazia, um elemento de automação de interface do usuário ainda deve ser retornado para oferecer suporte a <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> propriedade daquela célula.</span><span class="sxs-lookup"><span data-stu-id="73824-113">If a cell is empty, a UI Automation element must still be returned in order to support the <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> property for that cell.</span></span> <span data-ttu-id="73824-114">Isso é possível quando o layout dos elementos filho na grade é semelhante a uma matriz irregular (veja exemplo abaixo).</span><span class="sxs-lookup"><span data-stu-id="73824-114">This is possible when the layout of child elements in the grid is similar to a ragged array (see example below).</span></span>  
  
 <span data-ttu-id="73824-115">![Windows Explorer exibir mostrando desbalanceada layout. ] (../../../docs/framework/ui-automation/media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")</span><span class="sxs-lookup"><span data-stu-id="73824-115">![Windows Explorer view showing ragged layout.](../../../docs/framework/ui-automation/media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")</span></span>  
<span data-ttu-id="73824-116">Exemplo de um controle de grade com coordenadas vazios</span><span class="sxs-lookup"><span data-stu-id="73824-116">Example of a Grid Control with Empty Coordinates</span></span>  
  
-   <span data-ttu-id="73824-117">Uma grade com um único item ainda é necessária para implementar <xref:System.Windows.Automation.Provider.IGridProvider> se ela for considerada logicamente uma grade.</span><span class="sxs-lookup"><span data-stu-id="73824-117">A grid with a single item is still required to implement <xref:System.Windows.Automation.Provider.IGridProvider> if it is logically considered to be a grid.</span></span> <span data-ttu-id="73824-118">O número de itens filhos na grade é irrelevante.</span><span class="sxs-lookup"><span data-stu-id="73824-118">The number of child items in the grid is immaterial.</span></span>  
  
-   <span data-ttu-id="73824-119">Linhas e colunas, dependendo da implementação de provedor, podem ser carregadas no [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de árvore e, portanto, serão refletidas no <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> e <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="73824-119">Hidden rows and columns, depending on the provider implementation, may be loaded in the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree and therefore will be reflected in the <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> and <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> properties.</span></span> <span data-ttu-id="73824-120">Se as linhas e colunas ocultas ainda não tiverem sido carregadas, eles não devem ser contados.</span><span class="sxs-lookup"><span data-stu-id="73824-120">If the hidden rows and columns have not yet been loaded, they should not be counted.</span></span>  
  
-   <span data-ttu-id="73824-121"><xref:System.Windows.Automation.Provider.IGridProvider>não habilitam manipulação ativa de uma grade; <xref:System.Windows.Automation.Provider.ITransformProvider> deve ser implementado para habilitar essa funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="73824-121"><xref:System.Windows.Automation.Provider.IGridProvider> does not enable active manipulation of a grid; <xref:System.Windows.Automation.Provider.ITransformProvider> must be implemented to enable this functionality.</span></span>  
  
-   <span data-ttu-id="73824-122">Use um <xref:System.Windows.Automation.StructureChangedEventHandler> para escutar alterações estruturais ou de layout na grade como células que foram adicionados, removidos ou mesclados.</span><span class="sxs-lookup"><span data-stu-id="73824-122">Use a <xref:System.Windows.Automation.StructureChangedEventHandler> to listen for structural or layout changes to the grid such as cells that have been added, removed, or merged.</span></span>  
  
-   <span data-ttu-id="73824-123">Use um <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> para controlar a travessia pelos itens ou células de uma grade.</span><span class="sxs-lookup"><span data-stu-id="73824-123">Use a <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> to track traversal through the items or cells of a grid.</span></span>  
  
<a name="Required_Members_for_IGridProvider"></a>   
## <a name="required-members-for-igridprovider"></a><span data-ttu-id="73824-124">Membros necessários para IGridProvider</span><span class="sxs-lookup"><span data-stu-id="73824-124">Required Members for IGridProvider</span></span>  
 <span data-ttu-id="73824-125">As propriedades e métodos a seguir são necessários para implementar a interface IGridProvider.</span><span class="sxs-lookup"><span data-stu-id="73824-125">The following properties and methods are required for implementing the IGridProvider interface.</span></span>  
  
|<span data-ttu-id="73824-126">Membros necessários</span><span class="sxs-lookup"><span data-stu-id="73824-126">Required members</span></span>|<span data-ttu-id="73824-127">Tipo</span><span class="sxs-lookup"><span data-stu-id="73824-127">Type</span></span>|<span data-ttu-id="73824-128">Observações</span><span class="sxs-lookup"><span data-stu-id="73824-128">Notes</span></span>|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>|<span data-ttu-id="73824-129">Propriedade</span><span class="sxs-lookup"><span data-stu-id="73824-129">Property</span></span>|<span data-ttu-id="73824-130">Nenhum</span><span class="sxs-lookup"><span data-stu-id="73824-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>|<span data-ttu-id="73824-131">Propriedade</span><span class="sxs-lookup"><span data-stu-id="73824-131">Property</span></span>|<span data-ttu-id="73824-132">Nenhum</span><span class="sxs-lookup"><span data-stu-id="73824-132">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A>|<span data-ttu-id="73824-133">Método</span><span class="sxs-lookup"><span data-stu-id="73824-133">Method</span></span>|<span data-ttu-id="73824-134">Nenhum</span><span class="sxs-lookup"><span data-stu-id="73824-134">None</span></span>|  
  
 <span data-ttu-id="73824-135">Esse padrão de controle não possui eventos associados.</span><span class="sxs-lookup"><span data-stu-id="73824-135">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="73824-136">Exceções</span><span class="sxs-lookup"><span data-stu-id="73824-136">Exceptions</span></span>  
 <span data-ttu-id="73824-137">Provedores devem lançar as exceções a seguir.</span><span class="sxs-lookup"><span data-stu-id="73824-137">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="73824-138">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="73824-138">Exception type</span></span>|<span data-ttu-id="73824-139">Condição</span><span class="sxs-lookup"><span data-stu-id="73824-139">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> <span data-ttu-id="73824-140">-Se a coordenada da linha solicitada é maior do que o <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> ou a coordenada da coluna é maior que o <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>.</span><span class="sxs-lookup"><span data-stu-id="73824-140">-   If the requested row coordinate is larger than the <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> or the column coordinate is larger than the <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>.</span></span>|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> <span data-ttu-id="73824-141">-Se a coluna ou linha solicitada coordenadas é menor que zero.</span><span class="sxs-lookup"><span data-stu-id="73824-141">-   If either of the requested row or column coordinates is less than zero.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="73824-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73824-142">See Also</span></span>  
 [<span data-ttu-id="73824-143">Visão geral de padrões de controle de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="73824-143">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="73824-144">Suporte a padrões de controle em um provedor de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="73824-144">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="73824-145">Padrões de controle de automação de interface do usuário para clientes</span><span class="sxs-lookup"><span data-stu-id="73824-145">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="73824-146">Implementando o padrão de controle GridItem de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="73824-146">Implementing the UI Automation GridItem Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)  
 [<span data-ttu-id="73824-147">Visão geral de árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="73824-147">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="73824-148">Usar o cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="73824-148">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
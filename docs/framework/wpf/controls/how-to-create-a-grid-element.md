---
title: Como criar um elemento de grade
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], creating [WPF], grid instance
ms.assetid: b2f07626-9df8-43b8-8d36-492f3cb42837
ms.openlocfilehash: b93bb859c4a0df50da2fa00587a28fda3776fd09
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185778"
---
# <a name="how-to-create-a-grid-element"></a>Como criar um elemento de grade
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como criar e usar uma instância do <xref:System.Windows.Controls.Grid> usando o [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ou código. Este exemplo usa três <xref:System.Windows.Controls.ColumnDefinition> objetos e três <xref:System.Windows.Controls.RowDefinition> objetos criar uma grade que tem nove células, como em uma planilha. Cada célula contém um <xref:System.Windows.Controls.TextBlock> elemento que representa a data e a linha superior contém uma <xref:System.Windows.Controls.TextBlock> com o <xref:System.Windows.Controls.Grid.ColumnSpan%2A> propriedade aplicado. Para mostrar os limites de cada célula, o <xref:System.Windows.Controls.Grid.ShowGridLines%2A> propriedade está habilitada.  
  
 [!code-csharp[Grid#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Grid/CSharp/Grid_Code.cs#3)]
 [!code-vb[Grid#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Grid/VisualBasic/grid_vb.vb#3)]
 [!code-xaml[Grid#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Grid/XAML/default.xaml#3)]  
  
  Qualquer uma das abordagens irá gerar uma interface do usuário que se parece muito os mesmos, como a mostrada abaixo.

  ![uma captura de tela mostra uma interface de usuário do WPF que contém uma grade, dividida em três colunas.  Ele tem o título '2018 produtos fornecidos' abrangendo todas as colunas da linha superior e tem três colunas cada com dados de vendas para um determinado trimestre.  A linha inferior tem abrangendo duas colunas com a mensagem de texto ' Total de unidades: 300.000'](./media/how-to-create-a-grid-element/how-to-create-a-grid-element.png)
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.Grid>  
 [Visão geral de painéis](../../../../docs/framework/wpf/controls/panels-overview.md)

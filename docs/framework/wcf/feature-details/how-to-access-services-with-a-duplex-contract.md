---
title: 'Como: acessar serviços com um contrato duplex'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
ms.openlocfilehash: 6675da079b343b1b80477c65260ee8a1f44df72a
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027896"
---
# <a name="how-to-access-services-with-a-duplex-contract"></a>Como: acessar serviços com um contrato duplex

Um recurso do Windows Communication Foundation (WCF) é a capacidade de criar um serviço que usa um padrão de mensagens duplex. Esse padrão permite que um serviço para se comunicar com o cliente por meio de um retorno de chamada. Este tópico mostra as etapas para criar um cliente do WCF em uma classe de cliente que implementa a interface de retorno de chamada.

Uma associação dupla expõe o endereço IP do cliente para o serviço. O cliente deve usar a segurança para garantir que ele se conecta apenas para serviços relações de confiança.

Para obter um tutorial sobre como criar um serviço WCF básico e um cliente, consulte [Tutorial de Introdução](../../../../docs/framework/wcf/getting-started-tutorial.md).

## <a name="to-access-a-duplex-service"></a>Para acessar um serviço duplex

1. Crie um serviço que contém duas interfaces. É a primeira interface para o serviço, o segundo é para o retorno de chamada. Para obter mais informações sobre como criar um serviço duplex, consulte [como: criar um contrato Duplex](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).

2. Execute o serviço.

3. Use o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar contratos (interfaces) para o cliente. Para obter informações sobre como fazer isso, consulte [como: criar um cliente](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).

4. Implemente a interface de retorno de chamada na classe do cliente, conforme mostrado no exemplo a seguir.

    ```csharp
    public class CallbackHandler : ICalculatorDuplexCallback
    {
        public void Result(double result)
        {
            Console.WriteLine("Result ({0})", result);
        }
        public void Equation(string equation)
        {
            Console.WriteLine("Equation({0})", equation);
        }
    }
    ```

    ```vb
    Public Class CallbackHandler
    Implements ICalculatorDuplexCallback
       Public Sub Result (ByVal result As Double)
          Console.WriteLine("Result ({0})", result)
       End Sub
        Public Sub Equation(ByVal equation As String)
            Console.Writeline("Equation({0})", equation)
        End Sub
    End Class
    ```

5. Crie uma instância da classe <xref:System.ServiceModel.InstanceContext>. O construtor requer uma instância da classe do cliente.

    ```csharp
    InstanceContext site = new InstanceContext(new CallbackHandler());
    ```

    ```vb
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())
    ```

6. Criar uma instância do cliente WCF usando o construtor que requer um <xref:System.ServiceModel.InstanceContext> objeto. O segundo parâmetro do construtor é o nome de um ponto de extremidade encontrado no arquivo de configuração.

    ```csharp
    CalculatorDuplexClient wcfClient = new CalculatorDuplexClient(site, "default");
    ```

    ```vb
    Dim wcfClient As New CalculatorDuplexClient(site, "default")
    ```

7. Chame os métodos do cliente WCF conforme necessário.

## <a name="example"></a>Exemplo

O exemplo de código a seguir demonstra como criar uma classe de cliente que acessa um contrato duplex.

[!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
[!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]

## <a name="see-also"></a>Consulte também

[Tutorial de Introdução](../../../../docs/framework/wcf/getting-started-tutorial.md)  
[Como criar um contrato duplex](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
[Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
[Como criar um cliente](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
[Como usar o ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)

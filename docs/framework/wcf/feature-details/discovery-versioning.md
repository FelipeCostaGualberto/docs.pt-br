---
title: Controle de versão de descoberta
ms.date: 03/30/2017
ms.assetid: f91c6d0a-3af2-45c5-9a5c-e75390619836
ms.openlocfilehash: 18c160e5e08ed9b6733bed9d5e40a4dde00dfd1c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489174"
---
# <a name="discovery-versioning"></a>Controle de versão de descoberta
Este tópico fornece uma visão geral da implementação de alguns novos recursos de descoberta. Ele também fornece uma visão geral sobre como selecionar a versão de descoberta para usar.  
  
## <a name="discovery-versioning"></a>Controle de versão de descoberta  
 O recurso de descoberta inclui suporte para três versões do protocolo WS_Discovery. A descoberta de APIs permitem que você selecione qual versão do protocolo que você deseja usar. Este documento descreve brevemente as configurações relacionadas ao controle de versão.  
  
 As classes de descoberta a seguir agora têm um <xref:System.ServiceModel.Discovery.DiscoveryVersion> propriedade e execute um <xref:System.ServiceModel.Discovery.DiscoveryVersion> argumento em seus construtores:  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
  
### <a name="discoveryversionwsdiscoveryapril2005"></a>DiscoveryVersion.WSDiscoveryApril2005  
 Fornecendo <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryApril2005> como um construtor parâmetro faz com que a implementação de usar a versão April2005 do protocolo WS-Discovery. Esta versão corresponde à versão publicada da especificação do protocolo WS-Discovery. Esta versão deve ser usada para interoperar com o aplicativo herdado utilizando a versão April2005 do WS-Discovery.  
  
### <a name="discoveryversionwsdiscovery11"></a>DiscoveryVersion.WSDiscovery11  
 É a versão de descoberta padrão usada pelas APIs <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscovery11>. Essa é a versão atual padronizado do protocolo WS-Discovery.  
  
## <a name="discoveryversionwsdiscoverycd1"></a>DiscoveryVersion.WSDiscoveryCD1  
 Fornecendo <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryCD1> como um parâmetro de construtor utiliza a implementação do Comitê de rascunho 1 versão do protocolo WS-Discovery. Esta versão do protocolo deve ser usado para interoperar com implementações executando a versão do CD 1 do protocolo WS-Discovery.  
  
## <a name="supporting-multiple-udp-discovery-endpoints-for-different-discovery-versions-on-a-single-service-host"></a>O suporte a vários pontos de extremidade de descoberta UDP para versões diferentes de descoberta em um Host de serviço único  
 Você talvez queira expor vários descoberta de pontos de extremidade UDP para versões diferentes de descoberta em um host de serviço único. Para fazer isso, você deve especificar um endereço exclusivo para cada ponto de extremidade de descoberta UDP. O exemplo a seguir mostra como fazer isso.  
  
```  
UdpDiscoveryEndpoint newVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscovery11);  
UdpDiscoveryEndpoint oldVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
  
newVersionUdpEndpoint.Address = new EndpointAddress(newVersionUdpEndpoint.Address.Uri.ToString() + "/version11");  
oldVersionUdpEndpoint.Address = new EndpointAddress(oldVersionUdpEndpoint.Address.Uri.ToString() + "/versionAril2005");  
  
serviceHost.AddServiceEndpoint(newVersionUdpEndpoint);  
serviceHost.AddServiceEndpoint(oldVersionUdpEndpoint);  
```

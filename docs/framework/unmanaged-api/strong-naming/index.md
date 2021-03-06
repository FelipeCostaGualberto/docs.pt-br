---
title: Nomenclatura forte (referência de API não gerenciada)
ms.date: 03/30/2017
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5eb67e9b9f8f972075a98415de63d50585974823
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50193949"
---
# <a name="strong-naming-unmanaged-api-reference"></a>Nomenclatura forte (referência de API não gerenciada)
A API de nomenclatura forte permite que um cliente administre a assinatura de nome forte para assemblies.  
  
 Assinar um assembly com um nome forte adiciona uma criptografia de chave pública ao arquivo que contém o manifesto do assembly. Assinatura de nome forte ajuda a verificar a exclusividade do nome, a evitar falsificação de nome e a fornecer chamadores com uma identidade exclusiva quando uma referência é resolvida. No entanto, nenhum nível de confiança está associado a um nome forte.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Funções Estáticas Globais de Nomenclatura Forte](https://msdn.microsoft.com/library/efa715df-e8cc-48f2-9ec4-26586f0dc8d0)  
 Descreve as funções estáticas globais não gerenciadas que a API de nomenclatura forte usa.  
  
> [!NOTE]
>  Todas essas funções foram preteridas a partir do [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Para alternativas sugeridas, consulte a interface [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md).  
  
 [Função GetHashFromAssemblyFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfile-function.md)  
 Obtém um hash do arquivo do assembly especificado, usando o algoritmo de hash especificado. Preterida a partir do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função GetHashFromAssemblyFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfilew-function.md)  
 Obtém um hash do arquivo do assembly especificado como uma cadeia de caracteres Unicode, usando o algoritmo de hash especificado. Preterida a partir do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função GetHashFromBlob](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromblob-function.md)  
 Obtém um hash do assembly no endereço de memória especificado, usando o algoritmo de hash especificado. Preterida a partir do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função GetHashFromFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md)  
 Gera um hash sobre o conteúdo do arquivo especificado.  Preterida a partir do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md)  
 Gera um hash sobre o conteúdo do arquivo especificado por uma cadeia de caracteres Unicode. Preterida a partir do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função GetHashFromHandle](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromhandle-function.md)  
 Gera um hash sobre o conteúdo do arquivo com o identificador de arquivo especificado, usando o algoritmo de hash especificado.  Preterida a partir do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameCompareAssemblies](../../../../docs/framework/unmanaged-api/strong-naming/strongnamecompareassemblies-function.md)  
 Determina se dois assemblies diferem somente por suas assinaturas de nome forte. Preterida a partir do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)  
 Obtém o último código de erro que foi gerado por uma das funções de nome forte.  
  
 [Função StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)  
 Libera a memória que foi alocada com uma chamada anterior a uma função de nome forte, como [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), ou [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).   Preterida a partir do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameGetBlob](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblob-function.md)  
 Preenche o buffer especificado com a representação binária do arquivo executável no endereço especificado. Preterida a partir do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameGetBlobFromImage](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblobfromimage-function.md)  
 Obtém uma representação binária da imagem do assembly no endereço de memória especificado. Preterida a partir do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)  
 Obtém a chave pública de um par de chaves pública/privada. Preterida a partir do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameHashSize](../../../../docs/framework/unmanaged-api/strong-naming/strongnamehashsize-function.md)  
 Obtém o tamanho do buffer necessário para um hash, usando o algoritmo de hash especificado.  Preterida a partir do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md)  
 Exclui o contêiner de chave especificado. Preterida a partir do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameKeyGen](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygen-function.md)  
 Cria um novo par de chaves públicas/privadas para uso de nome forte.  Preterida a partir do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameKeyGenEx](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygenex-function.md)  
 Gera um novo par de chaves públicas/privadas com o tamanho da chave especificado para o uso de nome forte. Preterida a partir do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md)  
 Importa um par de chaves públicas/privadas em um contêiner.  Preterida a partir do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)  
 Gera uma assinatura de nome forte para o assembly especificado.   Preterida a partir do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameSignatureGenerationEx](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegenerationex-function.md)  
 Gera uma assinatura de nome forte para o assembly especificado, com base nos sinalizadores especificados.    Preterida a partir do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameSignatureSize](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md)  
 Retorna o tamanho da assinatura de nome forte. Preterida a partir do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md)  
 Obtém um valor que indica se o manifesto do assembly no caminho fornecido contém uma assinatura de nome forte, que é verificada de acordo com os sinalizadores especificados. Preterida a partir do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationex-function.md)  
 Obtém um valor que indica se o manifesto do assembly no caminho fornecido contém uma assinatura de nome forte.  Preterida a partir do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameSignatureVerificationFromImage](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationfromimage-function.md)  
 Verifica se um assembly, que já foi mapeado para a memória, é válido para a chave pública associada. Preterida a partir do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md)  
 Cria um token de nome forte do arquivo do assembly especificado.  Preterida a partir do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameTokenFromAssemblyEx](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassemblyex-function.md)  
 Cria um token de nome forte por meio do arquivo do assembly especificado e retorna a chave pública. Preterida a partir do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md)  
 Obtém um token que representa uma chave pública. Preterida a partir do [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Estruturas de nomenclatura forte](https://msdn.microsoft.com/library/4b041a2f-fd12-4b91-aacd-bc3b34a5124d)  
 Descreve a estrutura não gerenciada que uma API de nomenclatura forte usa para administrar a assinatura de nome forte para os assemblies.  
  
 [Estrutura PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 Representa a chave pública de um par de chaves públicas/privadas em formato binário.  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 [Referência de API não gerenciada](../../../../docs/framework/unmanaged-api/index.md)

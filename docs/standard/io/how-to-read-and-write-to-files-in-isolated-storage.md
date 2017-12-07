---
title: Como ler e gravar em arquivos no armazenamento isolado
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
- files, isolated storage
- reading data
- storing data using isolated storage, reading and writing to files
- writing to files within store
- data storage using isolated storage, reading and writing to files
- reading files within store
- isolated storage, reading and writing to files
- data stores, reading and writing to files
- stores, reading and writing to files
ms.assetid: f977ebdc-1b55-475a-bc3d-3376470b08ae
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8d733efc3d70070dd12f55c651033e97d1792c38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-and-write-to-files-in-isolated-storage"></a>Como ler e gravar em arquivos no armazenamento isolado
Para ler ou gravar um arquivo em um armazenamento isolado, use um <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> objeto com um leitor de fluxo (<xref:System.IO.StreamReader> objeto) ou o gravador do fluxo (<xref:System.IO.StreamWriter> objeto).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir obtém um armazenamento isolado e verifica se existe um arquivo chamado TestStore no repositório. Se não existir, ele cria o arquivo e grava "Hello isolado Storage" no arquivo. Se TestStore já existir, o código de exemplo lê a partir do arquivo.  
  
 [!code-csharp[Conceptual.IsolatedStorage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source5.cs#5)]
 [!code-vb[Conceptual.IsolatedStorage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source5.vb#5)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>  
 <xref:System.IO.FileMode?displayProperty=nameWithType>  
 <xref:System.IO.FileAccess?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader?displayProperty=nameWithType>  
 <xref:System.IO.StreamWriter?displayProperty=nameWithType>  
 [E/S de arquivo e de fluxo](../../../docs/standard/io/index.md)  
 [Armazenamentos isolado](../../../docs/standard/io/isolated-storage.md)
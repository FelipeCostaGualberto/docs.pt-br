---
title: Como descriptografar elementos XML com chaves simétricas
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.RijndaelManaged class
- XML encryption
- Rijndael
- decryption
ms.assetid: 6038aff0-f92c-4e29-a618-d793410410d8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 38bb22de14ecef618d45f54cced32af57542d3df
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43866839"
---
# <a name="how-to-decrypt-xml-elements-with-symmetric-keys"></a>Como descriptografar elementos XML com chaves simétricas
Você pode usar as classes de <xref:System.Security.Cryptography.Xml> namespace para criptografar um elemento em um documento XML.  Criptografia XML permite armazenar ou transportar XML confidencial, sem se preocupar com os dados que está sendo lidos com facilidade.  Este exemplo de código descriptografa um elemento XML usando o algoritmo de criptografia AES (padrão avançado), também conhecido como Rijndael.  
  
 Para obter informações sobre como criptografar um elemento XML usando esse procedimento, consulte [como: criptografar a elementos XML com chaves simétricas](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).  
  
 Quando você usa um algoritmo simétrico, como AES para criptografar os dados XML, você deve usar a mesma chave para criptografar e descriptografar os dados XML.  O exemplo neste procedimento supõe que o XML criptografado foi criptografado usando a mesma chave e criptografando e descriptografando partes concordar com o algoritmo e chave a ser usada.  Este exemplo não armazena nem criptografar a chave AES no XML criptografado.  
  
 Este exemplo é apropriado para situações em que um único aplicativo precisa para criptografar dados com base em uma chave de sessão armazenados na memória, ou com base em uma chave criptograficamente forte derivada de uma senha.  Para situações em que dois ou mais aplicativos precisam compartilhar dados XML criptografados, considere usar um esquema de criptografia com base em um algoritmo assimétrico ou um certificado X.509.  
  
### <a name="to-decrypt-an-xml-element-with-a-symmetric-key"></a>Para descriptografar um elemento XML com uma chave simétrica  
  
1.  Criptografar um elemento XML com a chave gerada anteriormente usando as técnicas descritas [como: criptografar a elementos XML com chaves simétricas](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).  
  
2.  Localizar o <`EncryptedData`> elemento (definido pelo padrão de criptografia XML) em um <xref:System.Xml.XmlDocument> do objeto que contém o XML criptografado e crie um novo <xref:System.Xml.XmlElement> objeto para representar esse elemento.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3.  Criar uma <xref:System.Security.Cryptography.Xml.EncryptedData> objeto ao carregar os dados XML brutos de criado anteriormente <xref:System.Xml.XmlElement> objeto.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4.  Criar um novo <xref:System.Security.Cryptography.Xml.EncryptedXml> de objeto e usá-lo para descriptografar os dados XML usando a mesma chave que foi usada para criptografia.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5.  Substitua o elemento criptografado com o elemento recentemente descriptografados em texto sem formatação no documento XML.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo supõe que um arquivo chamado `"test.xml"` existe no mesmo diretório que o programa compilado.  Ele também pressupõe que `"test.xml"` contém um `"creditcard"` elemento.  Você pode colocar o XML a seguir em um arquivo chamado `test.xml` e usá-lo com este exemplo.  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Para compilar este exemplo, você precisa incluir uma referência ao `System.Security.dll`.  
  
-   Inclua os seguintes namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, e <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Nunca armazenar uma chave de criptografia em texto não criptografado ou transferir uma chave entre as máquinas em texto não criptografado.  
  
 Quando você terminar usando uma chave de criptografia simétrica, desmarcá-la da memória, definindo cada byte como zero ou chamando o <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> método da classe de criptografia gerenciada.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Security.Cryptography.Xml>  
- [Como criptografar elementos XML com chaves simétricas](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md)

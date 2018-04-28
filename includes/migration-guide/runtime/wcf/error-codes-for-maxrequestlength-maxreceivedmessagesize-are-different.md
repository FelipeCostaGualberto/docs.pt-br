### <a name="error-codes-for-maxrequestlength-or-maxreceivedmessagesize-are-different"></a><span data-ttu-id="f8330-101">Códigos de erro de maxRequestLength ou maxReceivedMessageSize são diferentes</span><span class="sxs-lookup"><span data-stu-id="f8330-101">Error codes for maxRequestLength or maxReceivedMessageSize are different</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f8330-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="f8330-102">Details</span></span>|<span data-ttu-id="f8330-103">Mensagens nos serviços Web WCF hospedadas no IIS (Serviços de Informações da Internet) ou no ASP.NET Development Server que excedam maxRequestLength (no ASP.NET) ou maxReceivedMessageSize (no WCF) têm códigos de erro diferentes. O código de status HTTP foi alterado de 400 (Solicitação Incorreta) para 413 (Entidade de Solicitação Muito Longa), e as mensagens que excederam as configurações de maxRequestLength ou maxReceivedMessageSize lançarão uma exceção <xref:System.ServiceModel.ProtocolException?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="f8330-103">Messages in WCF web services hosted in Internet Information Services (IIS) or ASP.NET Development Server that exceed maxRequestLength (in ASP.NET) or maxReceivedMessageSize (in WCF) have different error codeThe HTTP status code has changed from 400 (Bad Request) to 413 (Request Entity Too Large), and messages that exceed either the maxRequestLength or the maxReceivedMessageSize setting throw a <xref:System.ServiceModel.ProtocolException?displayProperty=name> exception.</span></span> <span data-ttu-id="f8330-104">Isso inclui os casos em que o modo de transferência é Streamed.</span><span class="sxs-lookup"><span data-stu-id="f8330-104">This includes cases in which the transfer mode is Streamed.</span></span>|
|<span data-ttu-id="f8330-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="f8330-105">Suggestion</span></span>|<span data-ttu-id="f8330-106">Essa alteração facilita a depuração nos casos em que o comprimento da mensagem excede os limites permitidos pelo ASP.NET ou WCF. É necessário modificar os códigos que executam o processamento baseado em um código de status HTTP 400.</span><span class="sxs-lookup"><span data-stu-id="f8330-106">This change facilitates debugging in cases where the message length exceeds the limits allowed by ASP.NET or WCF.You must modify any code that performs processing based on an HTTP 400 status code.</span></span>|
|<span data-ttu-id="f8330-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="f8330-107">Scope</span></span>|<span data-ttu-id="f8330-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="f8330-108">Edge</span></span>|
|<span data-ttu-id="f8330-109">Versão</span><span class="sxs-lookup"><span data-stu-id="f8330-109">Version</span></span>|<span data-ttu-id="f8330-110">4.5</span><span class="sxs-lookup"><span data-stu-id="f8330-110">4.5</span></span>|
|<span data-ttu-id="f8330-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="f8330-111">Type</span></span>|<span data-ttu-id="f8330-112">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="f8330-112">Runtime</span></span>|

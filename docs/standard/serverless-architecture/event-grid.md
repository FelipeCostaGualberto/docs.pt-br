---
title: Grade de eventos do Azure - aplicativos sem servidor
description: A grade de eventos do Azure é uma solução sem servidor para entrega de eventos confiável e o roteamento em grande escala em um modelo de pagamento por evento.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: b2507da61cbea3b4bdc51c6eecfe4d784737e924
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/03/2018
ms.locfileid: "49369601"
---
# <a name="event-grid"></a><span data-ttu-id="68197-103">Grade de eventos</span><span class="sxs-lookup"><span data-stu-id="68197-103">Event Grid</span></span>

<span data-ttu-id="68197-104">[A grade de eventos do Azure](/azure-event-grid/overview) fornece infraestrutura sem servidor para aplicativos baseados em eventos.</span><span class="sxs-lookup"><span data-stu-id="68197-104">[Azure Event Grid](/azure-event-grid/overview) provides serverless infrastructure for event-based applications.</span></span> <span data-ttu-id="68197-105">Você pode publicar na grade de eventos de qualquer origem e consumir mensagens de qualquer plataforma.</span><span class="sxs-lookup"><span data-stu-id="68197-105">You can publish to Event Grid from any source and consume messages from any platform.</span></span> <span data-ttu-id="68197-106">Grade de eventos também tem suporte interno para eventos de recursos do Azure para simplificar a integração com seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="68197-106">Event Grid also has built-in support for events from Azure resources to streamline integration with your applications.</span></span> <span data-ttu-id="68197-107">Por exemplo, você pode assinar eventos de armazenamento de blob para notificar seu aplicativo quando um arquivo for carregado.</span><span class="sxs-lookup"><span data-stu-id="68197-107">For example, you can subscribe to blob storage events to notify your app when a file is uploaded.</span></span> <span data-ttu-id="68197-108">Seu aplicativo, em seguida, pode publicar uma mensagem de grade de evento personalizado que é consumida por outra nuvem ou aplicativos locais.</span><span class="sxs-lookup"><span data-stu-id="68197-108">Your application can then publish a custom event grid message that is consumed by other cloud or on-premises applications.</span></span> <span data-ttu-id="68197-109">Grade de eventos foi criada para lidar com confiança de grande escala.</span><span class="sxs-lookup"><span data-stu-id="68197-109">Event Grid was built to reliably handle massive scale.</span></span> <span data-ttu-id="68197-110">Você obtém os benefícios da publicação e assinar mensagens sem a sobrecarga de configurar a infraestrutura necessária.</span><span class="sxs-lookup"><span data-stu-id="68197-110">You get the benefits of publishing and subscribing to messages without the overhead of setting up the necessary infrastructure.</span></span>

![Logotipo da grade de eventos](./media/event-grid-logo.png)

<span data-ttu-id="68197-112">Os principais recursos da grade de eventos incluem:</span><span class="sxs-lookup"><span data-stu-id="68197-112">The major features of event grid include:</span></span>

* <span data-ttu-id="68197-113">Roteamento de eventos totalmente gerenciado.</span><span class="sxs-lookup"><span data-stu-id="68197-113">Fully managed event routing.</span></span>
* <span data-ttu-id="68197-114">Perto de entrega de eventos em tempo real em escala.</span><span class="sxs-lookup"><span data-stu-id="68197-114">Near real-time event delivery at scale.</span></span>
* <span data-ttu-id="68197-115">Cobertura mais ampla dentro e fora do Azure.</span><span class="sxs-lookup"><span data-stu-id="68197-115">Broad coverage both inside and outside of Azure.</span></span>

## <a name="scenarios"></a><span data-ttu-id="68197-116">Cenários</span><span class="sxs-lookup"><span data-stu-id="68197-116">Scenarios</span></span>

<span data-ttu-id="68197-117">Grade de eventos aborda vários cenários diferentes.</span><span class="sxs-lookup"><span data-stu-id="68197-117">Event Grid addresses several different scenarios.</span></span> <span data-ttu-id="68197-118">Esta seção aborda três dos mais comuns.</span><span class="sxs-lookup"><span data-stu-id="68197-118">This section covers three of the most common ones.</span></span>

### <a name="ops-automation"></a><span data-ttu-id="68197-119">Automação de operações</span><span class="sxs-lookup"><span data-stu-id="68197-119">Ops automation</span></span>

![Automação de operações](./media/ops-automation.png)

<span data-ttu-id="68197-121">Grade de eventos pode ajudar a automação de velocidade e simplificar a aplicação de políticas, notificando [automação do Azure](https://docs.microsoft.com/azure/automation) quando a infraestrutura é provisionada.</span><span class="sxs-lookup"><span data-stu-id="68197-121">Event Grid can help speed automation and simplify policy enforcement by notifying [Azure Automation](https://docs.microsoft.com/azure/automation) when infrastructure is provisioned.</span></span>

### <a name="application-integration"></a><span data-ttu-id="68197-122">Integração de aplicativos</span><span class="sxs-lookup"><span data-stu-id="68197-122">Application integration</span></span>

![Integração de aplicativos](./media/app-integration.png)

<span data-ttu-id="68197-124">Você pode usar a grade de eventos para conectar seu aplicativo a outros serviços.</span><span class="sxs-lookup"><span data-stu-id="68197-124">You can use Event Grid to connect your app to other services.</span></span> <span data-ttu-id="68197-125">Usando protocolos HTTP padrão, aplicativos herdados ainda podem ser facilmente modificados para publicar mensagens da grade de eventos.</span><span class="sxs-lookup"><span data-stu-id="68197-125">Using standard HTTP protocols, even legacy apps can be easily modified to publish Event Grid messages.</span></span> <span data-ttu-id="68197-126">Ganchos da Web estão disponíveis para outros serviços e plataformas para consumir mensagens da grade de eventos.</span><span class="sxs-lookup"><span data-stu-id="68197-126">Web hooks are available for other services and platforms to consume Event Grid messages.</span></span>

### <a name="serverless-apps"></a><span data-ttu-id="68197-127">Aplicativos sem servidor</span><span class="sxs-lookup"><span data-stu-id="68197-127">Serverless apps</span></span>

![Aplicativos sem servidor](./media/serverless-apps.png)

<span data-ttu-id="68197-129">Grade de eventos pode disparar o Azure Functions, aplicativos lógicos ou seu próprio código personalizado.</span><span class="sxs-lookup"><span data-stu-id="68197-129">Event Grid can trigger Azure Functions, Logic Apps, or your own custom code.</span></span> <span data-ttu-id="68197-130">Uma grande vantagem de usar a grade de eventos é que ele usa um *push* mecanismo para enviar mensagens quando ocorrerem eventos.</span><span class="sxs-lookup"><span data-stu-id="68197-130">A major benefit of using Event Grid is that it uses a *push* mechanism to send messages when events occur.</span></span> <span data-ttu-id="68197-131">A arquitetura de push consome menos recursos e dimensiona melhor do que *sondagem* mecanismos.</span><span class="sxs-lookup"><span data-stu-id="68197-131">The push architecture consumes fewer resources and scales better than *polling* mechanisms.</span></span> <span data-ttu-id="68197-132">Sondagem deve verificar se há atualizações em intervalos regulares.</span><span class="sxs-lookup"><span data-stu-id="68197-132">Polling must check for updates on a regular interval.</span></span>

## <a name="event-grid-vs-other-azure-messaging-services"></a><span data-ttu-id="68197-133">Grade de eventos versus outros serviços de mensagens do Azure</span><span class="sxs-lookup"><span data-stu-id="68197-133">Event Grid vs. other Azure messaging services</span></span>

<span data-ttu-id="68197-134">O Azure fornece vários serviços de sistema de mensagens, incluindo [dos Hubs de eventos](https://docs.microsoft.com/azure/event-hubs) e [do barramento de serviço](https://docs.microsoft.com/azure/service-bus-messaging).</span><span class="sxs-lookup"><span data-stu-id="68197-134">Azure provides several messaging services, including [Event Hubs](https://docs.microsoft.com/azure/event-hubs) and [Service Bus](https://docs.microsoft.com/azure/service-bus-messaging).</span></span> <span data-ttu-id="68197-135">Cada foi projetado para tratar de um conjunto específico de casos de uso.</span><span class="sxs-lookup"><span data-stu-id="68197-135">Each is designed to address a specific set of use cases.</span></span> <span data-ttu-id="68197-136">O diagrama a seguir fornece uma visão geral das diferenças entre os serviços.</span><span class="sxs-lookup"><span data-stu-id="68197-136">The following diagram provides a high-level overview of the differences between the services.</span></span>

![Comparação de mensagens do Azure](./media/azure-messaging-services.png)

<span data-ttu-id="68197-138">Para obter uma comparação mais detalhada, consulte [comparam os serviços de mensagens](https://docs.microsoft.com/azure/event-grid/compare-messaging-services).</span><span class="sxs-lookup"><span data-stu-id="68197-138">For a more in-depth comparison, see [Compare messaging services](https://docs.microsoft.com/azure/event-grid/compare-messaging-services).</span></span>

## <a name="performance-targets"></a><span data-ttu-id="68197-139">Metas de desempenho</span><span class="sxs-lookup"><span data-stu-id="68197-139">Performance targets</span></span>

<span data-ttu-id="68197-140">Usando a grade de eventos, você pode tirar proveito do desempenho seguinte garantias:</span><span class="sxs-lookup"><span data-stu-id="68197-140">Using Event Grid you can take advantage of the following performance guarantees:</span></span>

* <span data-ttu-id="68197-141">Subsecond latência de ponta a ponta no 99 º percentil.</span><span class="sxs-lookup"><span data-stu-id="68197-141">Subsecond end-to-end latency in the 99th percentile.</span></span>
* <span data-ttu-id="68197-142">disponibilidade de 99,99%.</span><span class="sxs-lookup"><span data-stu-id="68197-142">99.99% availability.</span></span>
* <span data-ttu-id="68197-143">10 milhões de eventos por segundo por região.</span><span class="sxs-lookup"><span data-stu-id="68197-143">10 million events per second per region.</span></span>
* <span data-ttu-id="68197-144">assinaturas de 100 milhões por região.</span><span class="sxs-lookup"><span data-stu-id="68197-144">100 million subscriptions per region.</span></span>
* <span data-ttu-id="68197-145">latência do publicador de 50 ms.</span><span class="sxs-lookup"><span data-stu-id="68197-145">50-ms publisher latency.</span></span>
* <span data-ttu-id="68197-146">repetição de 24 horas com retirada exponencial para entrega garantida na janela de 1 dia.</span><span class="sxs-lookup"><span data-stu-id="68197-146">24-hour retry with exponential back-off for guaranteed delivery in the 1-day window.</span></span>
* <span data-ttu-id="68197-147">Failover regional transparente.</span><span class="sxs-lookup"><span data-stu-id="68197-147">Transparent regional failover.</span></span>

## <a name="event-grid-schema"></a><span data-ttu-id="68197-148">Esquema de grade de eventos</span><span class="sxs-lookup"><span data-stu-id="68197-148">Event Grid schema</span></span>

<span data-ttu-id="68197-149">Grade de eventos usa um esquema padrão para encapsular eventos personalizados.</span><span class="sxs-lookup"><span data-stu-id="68197-149">Event Grid uses a standard schema to wrap custom events.</span></span> <span data-ttu-id="68197-150">O esquema é como um envelope que encapsula o elemento de dados personalizados.</span><span class="sxs-lookup"><span data-stu-id="68197-150">The schema is like an envelope that wraps your custom data element.</span></span> <span data-ttu-id="68197-151">Aqui está um exemplo de mensagem de grade de eventos:</span><span class="sxs-lookup"><span data-stu-id="68197-151">Here is an example Event Grid message:</span></span>

```json
[{
    "id": "03e24f21-a955-43cc-8921-1f61a6081ce0",
    "eventType": "myCustomEvent",
    "subject": "foo/bar/12",
    "eventTime": "2018-09-22T10:36:01+00:00",
    "data": {
        "favoriteColor": "blue",
        "favoriteAnimal": "panther",
        "favoritePlanet": "Jupiter"
    },
    "dataVersion": "1.0"
}]
```

<span data-ttu-id="68197-152">Tudo sobre a mensagem é o padrão, exceto o `data` propriedade.</span><span class="sxs-lookup"><span data-stu-id="68197-152">Everything about the message is standard except the `data` property.</span></span> <span data-ttu-id="68197-153">Você pode inspecionar a mensagem e usar o `eventType` e `dataVersion` desserializar a parte personalizada de carga.</span><span class="sxs-lookup"><span data-stu-id="68197-153">You can inspect the message and use the `eventType` and `dataVersion` to de-serialize the custom portion of the payload.</span></span>

## <a name="azure-resources"></a><span data-ttu-id="68197-154">Recursos do Azure</span><span class="sxs-lookup"><span data-stu-id="68197-154">Azure resources</span></span>

<span data-ttu-id="68197-155">Uma grande vantagem de usar a grade de eventos é que as mensagens automática produzidas pelo Azure.</span><span class="sxs-lookup"><span data-stu-id="68197-155">A major benefit of using Event Grid is the automatic messages produced by Azure.</span></span> <span data-ttu-id="68197-156">No Azure, recursos de publicar automaticamente um *tópico* que permite que você assine para vários eventos.</span><span class="sxs-lookup"><span data-stu-id="68197-156">In Azure, resources automatically publish to a *topic* that allows you to subscribe for various events.</span></span> <span data-ttu-id="68197-157">A tabela a seguir lista os tipos de recursos, tipos de mensagens e eventos que estão disponíveis automaticamente.</span><span class="sxs-lookup"><span data-stu-id="68197-157">The following table lists the resource types, message types, and events that are available automatically.</span></span>

| <span data-ttu-id="68197-158">Recursos do Azure</span><span class="sxs-lookup"><span data-stu-id="68197-158">Azure resource</span></span> | <span data-ttu-id="68197-159">Tipo de evento</span><span class="sxs-lookup"><span data-stu-id="68197-159">Event type</span></span> | <span data-ttu-id="68197-160">Descrição</span><span class="sxs-lookup"><span data-stu-id="68197-160">Description</span></span> |
| -------------- | ---------- | ----------- |
| <span data-ttu-id="68197-161">Assinatura do Azure</span><span class="sxs-lookup"><span data-stu-id="68197-161">Azure subscription</span></span> | <span data-ttu-id="68197-162">Microsoft.Resources.ResourceWriteSuccess</span><span class="sxs-lookup"><span data-stu-id="68197-162">Microsoft.Resources.ResourceWriteSuccess</span></span> | <span data-ttu-id="68197-163">Gerado quando um recurso cria ou operação de atualização é bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="68197-163">Raised when a resource create or update operation succeeds.</span></span> |
| | <span data-ttu-id="68197-164">Microsoft.Resources.ResourceWriteFailure</span><span class="sxs-lookup"><span data-stu-id="68197-164">Microsoft.Resources.ResourceWriteFailure</span></span> | <span data-ttu-id="68197-165">Gerado quando um recurso cria ou operação de atualização falhará.</span><span class="sxs-lookup"><span data-stu-id="68197-165">Raised when a resource create or update operation fails.</span></span> |
| | <span data-ttu-id="68197-166">Microsoft.Resources.ResourceWriteCancel</span><span class="sxs-lookup"><span data-stu-id="68197-166">Microsoft.Resources.ResourceWriteCancel</span></span> | <span data-ttu-id="68197-167">Gerado quando um recurso cria ou operação de atualização é cancelada.</span><span class="sxs-lookup"><span data-stu-id="68197-167">Raised when a resource create or update operation is canceled.</span></span> |
|  | <span data-ttu-id="68197-168">Microsoft.Resources.ResourceDeleteSuccess</span><span class="sxs-lookup"><span data-stu-id="68197-168">Microsoft.Resources.ResourceDeleteSuccess</span></span> | <span data-ttu-id="68197-169">Gerado quando uma operação de exclusão do recurso é bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="68197-169">Raised when a resource delete operation succeeds.</span></span> |
|  | <span data-ttu-id="68197-170">Microsoft.Resources.ResourceDeleteFailure</span><span class="sxs-lookup"><span data-stu-id="68197-170">Microsoft.Resources.ResourceDeleteFailure</span></span> | <span data-ttu-id="68197-171">Gerado quando uma operação de exclusão de recurso falha.</span><span class="sxs-lookup"><span data-stu-id="68197-171">Raised when a resource delete operation fails.</span></span> |
| | <span data-ttu-id="68197-172">Microsoft.Resources.ResourceDeleteCancel</span><span class="sxs-lookup"><span data-stu-id="68197-172">Microsoft.Resources.ResourceDeleteCancel</span></span> | <span data-ttu-id="68197-173">Gerado quando uma operação de exclusão do recurso é cancelada.</span><span class="sxs-lookup"><span data-stu-id="68197-173">Raised when a resource delete operation is canceled.</span></span> <span data-ttu-id="68197-174">Esse evento ocorre quando uma implantação de modelo é cancelada.</span><span class="sxs-lookup"><span data-stu-id="68197-174">This event happens when a template deployment is canceled.</span></span> |
| <span data-ttu-id="68197-175">Armazenamento de BLOBs</span><span class="sxs-lookup"><span data-stu-id="68197-175">Blob storage</span></span> | <span data-ttu-id="68197-176">Microsoft.Storage.BlobCreated</span><span class="sxs-lookup"><span data-stu-id="68197-176">Microsoft.Storage.BlobCreated</span></span> | <span data-ttu-id="68197-177">Gerado quando um blob é criado.</span><span class="sxs-lookup"><span data-stu-id="68197-177">Raised when a blob is created.</span></span> |
| | <span data-ttu-id="68197-178">Microsoft.Storage.BlobDeleted</span><span class="sxs-lookup"><span data-stu-id="68197-178">Microsoft.Storage.BlobDeleted</span></span> | <span data-ttu-id="68197-179">Gerado quando um blob é excluído.</span><span class="sxs-lookup"><span data-stu-id="68197-179">Raised when a blob is deleted.</span></span> |
| <span data-ttu-id="68197-180">Hubs de eventos</span><span class="sxs-lookup"><span data-stu-id="68197-180">Event hubs</span></span> | <span data-ttu-id="68197-181">Microsoft.EventHub.CaptureFileCreated</span><span class="sxs-lookup"><span data-stu-id="68197-181">Microsoft.EventHub.CaptureFileCreated</span></span> | <span data-ttu-id="68197-182">Gerado quando um arquivo de captura é criado.</span><span class="sxs-lookup"><span data-stu-id="68197-182">Raised when a capture file is created.</span></span>
| <span data-ttu-id="68197-183">Hub IoT</span><span class="sxs-lookup"><span data-stu-id="68197-183">IoT Hub</span></span> | <span data-ttu-id="68197-184">Microsoft.Devices.DeviceCreated</span><span class="sxs-lookup"><span data-stu-id="68197-184">Microsoft.Devices.DeviceCreated</span></span> | <span data-ttu-id="68197-185">Publicado quando um dispositivo é registrado para um hub IoT.</span><span class="sxs-lookup"><span data-stu-id="68197-185">Published when a device is registered to an IoT hub.</span></span> |
| | <span data-ttu-id="68197-186">Microsoft.Devices.DeviceDeleted</span><span class="sxs-lookup"><span data-stu-id="68197-186">Microsoft.Devices.DeviceDeleted</span></span> | <span data-ttu-id="68197-187">Publicado quando um dispositivo é excluído de um hub IoT.</span><span class="sxs-lookup"><span data-stu-id="68197-187">Published when a device is deleted from an IoT hub.</span></span> |
| <span data-ttu-id="68197-188">Grupos de recursos</span><span class="sxs-lookup"><span data-stu-id="68197-188">Resource groups</span></span> | <span data-ttu-id="68197-189">Microsoft.Resources.ResourceWriteSuccess</span><span class="sxs-lookup"><span data-stu-id="68197-189">Microsoft.Resources.ResourceWriteSuccess</span></span> | <span data-ttu-id="68197-190">Gerado quando um recurso cria ou operação de atualização é bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="68197-190">Raised when a resource create or update operation succeeds.</span></span> |
| | <span data-ttu-id="68197-191">Microsoft.Resources.ResourceWriteFailure</span><span class="sxs-lookup"><span data-stu-id="68197-191">Microsoft.Resources.ResourceWriteFailure</span></span> | <span data-ttu-id="68197-192">Gerado quando um recurso cria ou operação de atualização falhará.</span><span class="sxs-lookup"><span data-stu-id="68197-192">Raised when a resource create or update operation fails.</span></span> |
| | <span data-ttu-id="68197-193">Microsoft.Resources.ResourceWriteCancel</span><span class="sxs-lookup"><span data-stu-id="68197-193">Microsoft.Resources.ResourceWriteCancel</span></span> | <span data-ttu-id="68197-194">Gerado quando um recurso cria ou operação de atualização é cancelada.</span><span class="sxs-lookup"><span data-stu-id="68197-194">Raised when a resource create or update operation is canceled.</span></span> |
| | <span data-ttu-id="68197-195">Microsoft.Resources.ResourceDeleteSuccess</span><span class="sxs-lookup"><span data-stu-id="68197-195">Microsoft.Resources.ResourceDeleteSuccess</span></span> | <span data-ttu-id="68197-196">Gerado quando uma operação de exclusão do recurso é bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="68197-196">Raised when a resource delete operation succeeds.</span></span> |
| | <span data-ttu-id="68197-197">Microsoft.Resources.ResourceDeleteFailure</span><span class="sxs-lookup"><span data-stu-id="68197-197">Microsoft.Resources.ResourceDeleteFailure</span></span> | <span data-ttu-id="68197-198">Gerado quando uma operação de exclusão de recurso falha.</span><span class="sxs-lookup"><span data-stu-id="68197-198">Raised when a resource delete operation fails.</span></span> |
| | <span data-ttu-id="68197-199">Microsoft.Resources.ResourceDeleteCancel</span><span class="sxs-lookup"><span data-stu-id="68197-199">Microsoft.Resources.ResourceDeleteCancel</span></span> | <span data-ttu-id="68197-200">Gerado quando uma operação de exclusão do recurso é cancelada.</span><span class="sxs-lookup"><span data-stu-id="68197-200">Raised when a resource delete operation is canceled.</span></span> <span data-ttu-id="68197-201">Esse evento ocorre quando uma implantação de modelo é cancelada.</span><span class="sxs-lookup"><span data-stu-id="68197-201">This event happens when a template deployment is canceled.</span></span> |

<span data-ttu-id="68197-202">Para obter mais informações, consulte [esquema de evento de grade de eventos do Azure](https://docs.microsoft.com/azure/event-grid/event-schema).</span><span class="sxs-lookup"><span data-stu-id="68197-202">For more information, see [Azure Event Grid event schema](https://docs.microsoft.com/azure/event-grid/event-schema).</span></span>

<span data-ttu-id="68197-203">Você pode acessar a grade de eventos de qualquer tipo de aplicativo, até mesmo um que é executado localmente.</span><span class="sxs-lookup"><span data-stu-id="68197-203">You can access Event Grid from any type of application, even one that runs on-premises.</span></span>

## <a name="conclusion"></a><span data-ttu-id="68197-204">Conclusão</span><span class="sxs-lookup"><span data-stu-id="68197-204">Conclusion</span></span>

<span data-ttu-id="68197-205">Neste capítulo, você aprendeu sobre a plataforma do Azure sem servidor que é composta de funções do Azure, aplicativos lógicos e a grade de eventos.</span><span class="sxs-lookup"><span data-stu-id="68197-205">In this chapter you learned about the Azure serverless platform that is composed of Azure Functions, Logic Apps, and Event Grid.</span></span> <span data-ttu-id="68197-206">Você pode usar esses recursos para criar uma arquitetura de aplicativo totalmente sem servidor, ou criar uma solução híbrida que interage com outros recursos de nuvem e em servidores locais.</span><span class="sxs-lookup"><span data-stu-id="68197-206">You can use these resources to build an entirely serverless app architecture, or create a hybrid solution that interacts with other cloud resources and on-premises servers.</span></span> <span data-ttu-id="68197-207">Combinado com uma plataforma de dados sem servidor como [SQL do Azure](https://docs.microsoft.com/azure/sql-database) ou [CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction), você pode criar aplicativos nativos de nuvem totalmente gerenciada.</span><span class="sxs-lookup"><span data-stu-id="68197-207">Combined with a serverless data platform such as [Azure SQL](https://docs.microsoft.com/azure/sql-database) or [CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction), you can build fully managed cloud native applications.</span></span>

## <a name="recommended-resources"></a><span data-ttu-id="68197-208">Recursos recomendados</span><span class="sxs-lookup"><span data-stu-id="68197-208">Recommended resources</span></span>

* [<span data-ttu-id="68197-209">Planos de serviço de aplicativo</span><span class="sxs-lookup"><span data-stu-id="68197-209">App service plans</span></span>](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)
* [<span data-ttu-id="68197-210">Application Insights</span><span class="sxs-lookup"><span data-stu-id="68197-210">Application Insights</span></span>](https://docs.microsoft.com/azure/application-insights)
* [<span data-ttu-id="68197-211">Análise do Application Insights</span><span class="sxs-lookup"><span data-stu-id="68197-211">Application Insights Analytics</span></span>](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)
* [<span data-ttu-id="68197-212">Azure: Traga seu aplicativo para a nuvem com o Azure Functions sem servidor</span><span class="sxs-lookup"><span data-stu-id="68197-212">Azure: Bring your app to the cloud with serverless Azure Functions</span></span>](https://channel9.msdn.com/events/Connect/2017/E102)
* [<span data-ttu-id="68197-213">Grade de Eventos do Azure</span><span class="sxs-lookup"><span data-stu-id="68197-213">Azure Event Grid</span></span>](https://docs.microsoft.com/azure/azure-event-grid/overview)
* [<span data-ttu-id="68197-214">Esquema de evento de grade de eventos do Azure</span><span class="sxs-lookup"><span data-stu-id="68197-214">Azure Event Grid event schema</span></span>](https://docs.microsoft.com/azure/event-grid/event-schema)
* [<span data-ttu-id="68197-215">Hubs de eventos do Azure</span><span class="sxs-lookup"><span data-stu-id="68197-215">Azure Event Hubs</span></span>](https://docs.microsoft.com/azure/event-hubs)
* [<span data-ttu-id="68197-216">Documentação de funções do Azure</span><span class="sxs-lookup"><span data-stu-id="68197-216">Azure Functions documentation</span></span>](https://docs.microsoft.com/azure/azure-functions)
* [<span data-ttu-id="68197-217">Conceitos de associações e gatilhos do Azure Functions</span><span class="sxs-lookup"><span data-stu-id="68197-217">Azure Functions triggers and bindings concepts</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)
* [<span data-ttu-id="68197-218">Aplicativos Lógicos do Azure</span><span class="sxs-lookup"><span data-stu-id="68197-218">Azure Logic Apps</span></span>](https://docs.microsoft.com/azure/logic-apps)
* [<span data-ttu-id="68197-219">Barramento de Serviço do Azure</span><span class="sxs-lookup"><span data-stu-id="68197-219">Azure Service Bus</span></span>](https://docs.microsoft.com/azure/service-bus-messaging)
* [<span data-ttu-id="68197-220">Armazenamento de tabelas do Azure</span><span class="sxs-lookup"><span data-stu-id="68197-220">Azure Table Storage</span></span>](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)
* [<span data-ttu-id="68197-221">Comparar functions 1.x e 2.x</span><span class="sxs-lookup"><span data-stu-id="68197-221">Compare functions 1.x and 2.x</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-versions)
* [<span data-ttu-id="68197-222">Conectar-se a fontes de dados local com o Gateway de dados local do Azure</span><span class="sxs-lookup"><span data-stu-id="68197-222">Connecting to on-premises data sources with Azure On-premises Data Gateway</span></span>](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)
* [<span data-ttu-id="68197-223">Criar sua primeira função no portal do Azure</span><span class="sxs-lookup"><span data-stu-id="68197-223">Create your first function in the Azure portal</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)
* [<span data-ttu-id="68197-224">Criar sua primeira função usando a CLI do Azure</span><span class="sxs-lookup"><span data-stu-id="68197-224">Create your first function using the Azure CLI</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)
* [<span data-ttu-id="68197-225">Criar sua primeira função usando o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="68197-225">Create your first function using Visual Studio</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)
* [<span data-ttu-id="68197-226">Funções de idiomas com suporte</span><span class="sxs-lookup"><span data-stu-id="68197-226">Functions supported languages</span></span>](https://docs.microsoft.com/azure/azure-functions/supported-languages)
* [<span data-ttu-id="68197-227">Monitorar Azure Functions</span><span class="sxs-lookup"><span data-stu-id="68197-227">Monitor Azure Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)
* [<span data-ttu-id="68197-228">Trabalhar com Proxies do Azure Functions</span><span class="sxs-lookup"><span data-stu-id="68197-228">Work with Azure Functions Proxies</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-proxies)

>[!div class="step-by-step"]
<span data-ttu-id="68197-229">[Anterior](logic-apps.md)
[Próximo](durable-azure-functions.md)</span><span class="sxs-lookup"><span data-stu-id="68197-229">[Previous](logic-apps.md)
[Next](durable-azure-functions.md)</span></span>
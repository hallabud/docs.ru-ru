---
title: Сетка событий Azure — Бессерверных приложений
description: Сетка событий Azure — это бессерверное решение для доставки событий надежных и маршрутизации в большом масштабе на модель оплаты за событие.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: b2507da61cbea3b4bdc51c6eecfe4d784737e924
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "49370208"
---
# <a name="event-grid"></a><span data-ttu-id="d5c49-103">"Сетка событий"</span><span class="sxs-lookup"><span data-stu-id="d5c49-103">Event Grid</span></span>

<span data-ttu-id="d5c49-104">[Сетка событий Azure](/azure-event-grid/overview) предоставляет независимой от сервера инфраструктурой приложений на основе событий.</span><span class="sxs-lookup"><span data-stu-id="d5c49-104">[Azure Event Grid](/azure-event-grid/overview) provides serverless infrastructure for event-based applications.</span></span> <span data-ttu-id="d5c49-105">Можно опубликовать в сетке событий из любого источника и получать сообщения с любой платформы.</span><span class="sxs-lookup"><span data-stu-id="d5c49-105">You can publish to Event Grid from any source and consume messages from any platform.</span></span> <span data-ttu-id="d5c49-106">"Сетка событий" также имеет встроенную поддержку событий из ресурсов Azure для упрощения интеграции с приложениями.</span><span class="sxs-lookup"><span data-stu-id="d5c49-106">Event Grid also has built-in support for events from Azure resources to streamline integration with your applications.</span></span> <span data-ttu-id="d5c49-107">Например можно подписаться на события хранилища BLOB-объектов для уведомления приложения при отправке файла.</span><span class="sxs-lookup"><span data-stu-id="d5c49-107">For example, you can subscribe to blob storage events to notify your app when a file is uploaded.</span></span> <span data-ttu-id="d5c49-108">Приложение затем можно опубликовать сообщение сетки пользовательское событие, используется в другом облаке или локальных приложений.</span><span class="sxs-lookup"><span data-stu-id="d5c49-108">Your application can then publish a custom event grid message that is consumed by other cloud or on-premises applications.</span></span> <span data-ttu-id="d5c49-109">"Сетка событий" был разработан для надежно обрабатывающих массивного масштабирования.</span><span class="sxs-lookup"><span data-stu-id="d5c49-109">Event Grid was built to reliably handle massive scale.</span></span> <span data-ttu-id="d5c49-110">Вы получаете преимущества публикации и подписки на сообщения без издержек по настройке необходимую инфраструктуру.</span><span class="sxs-lookup"><span data-stu-id="d5c49-110">You get the benefits of publishing and subscribing to messages without the overhead of setting up the necessary infrastructure.</span></span>

![Логотип сетки событий](./media/event-grid-logo.png)

<span data-ttu-id="d5c49-112">Основные возможности "Сетка событий":</span><span class="sxs-lookup"><span data-stu-id="d5c49-112">The major features of event grid include:</span></span>

* <span data-ttu-id="d5c49-113">Полностью управляемой маршрутизацией событий.</span><span class="sxs-lookup"><span data-stu-id="d5c49-113">Fully managed event routing.</span></span>
* <span data-ttu-id="d5c49-114">Рядом с доставки событий в реальном времени в нужном масштабе.</span><span class="sxs-lookup"><span data-stu-id="d5c49-114">Near real-time event delivery at scale.</span></span>
* <span data-ttu-id="d5c49-115">Широкий покрытие внутри и вне Azure.</span><span class="sxs-lookup"><span data-stu-id="d5c49-115">Broad coverage both inside and outside of Azure.</span></span>

## <a name="scenarios"></a><span data-ttu-id="d5c49-116">Сценарии</span><span class="sxs-lookup"><span data-stu-id="d5c49-116">Scenarios</span></span>

<span data-ttu-id="d5c49-117">"Сетка событий" адреса нескольких различных сценариях.</span><span class="sxs-lookup"><span data-stu-id="d5c49-117">Event Grid addresses several different scenarios.</span></span> <span data-ttu-id="d5c49-118">В этом разделе рассматриваются три наиболее распространенные из них.</span><span class="sxs-lookup"><span data-stu-id="d5c49-118">This section covers three of the most common ones.</span></span>

### <a name="ops-automation"></a><span data-ttu-id="d5c49-119">Автоматизация операций</span><span class="sxs-lookup"><span data-stu-id="d5c49-119">Ops automation</span></span>

![Автоматизация операций](./media/ops-automation.png)

<span data-ttu-id="d5c49-121">"Сетка событий" может помочь скорость автоматизации и упрощает применение политик, уведомляя о [службы автоматизации Azure](https://docs.microsoft.com/azure/automation) после подготовки инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="d5c49-121">Event Grid can help speed automation and simplify policy enforcement by notifying [Azure Automation](https://docs.microsoft.com/azure/automation) when infrastructure is provisioned.</span></span>

### <a name="application-integration"></a><span data-ttu-id="d5c49-122">Интеграция приложений</span><span class="sxs-lookup"><span data-stu-id="d5c49-122">Application integration</span></span>

![Интеграция приложений](./media/app-integration.png)

<span data-ttu-id="d5c49-124">"Сетка событий" можно использовать для подключения приложения к другим службам.</span><span class="sxs-lookup"><span data-stu-id="d5c49-124">You can use Event Grid to connect your app to other services.</span></span> <span data-ttu-id="d5c49-125">С помощью стандартных протоколов HTTP, даже для устаревших приложений можно легко изменить для публикации сообщений "Сетка событий".</span><span class="sxs-lookup"><span data-stu-id="d5c49-125">Using standard HTTP protocols, even legacy apps can be easily modified to publish Event Grid messages.</span></span> <span data-ttu-id="d5c49-126">Веб-перехватчики доступны для других служб и платформ для получения сообщений "Сетка событий".</span><span class="sxs-lookup"><span data-stu-id="d5c49-126">Web hooks are available for other services and platforms to consume Event Grid messages.</span></span>

### <a name="serverless-apps"></a><span data-ttu-id="d5c49-127">Бессерверные приложения</span><span class="sxs-lookup"><span data-stu-id="d5c49-127">Serverless apps</span></span>

![Бессерверные приложения](./media/serverless-apps.png)

<span data-ttu-id="d5c49-129">"Сетка событий" может активировать функции Azure, Logic Apps или собственный код.</span><span class="sxs-lookup"><span data-stu-id="d5c49-129">Event Grid can trigger Azure Functions, Logic Apps, or your own custom code.</span></span> <span data-ttu-id="d5c49-130">Главным преимуществом с помощью сетки событий является применение *принудительной* механизм для отправки сообщений при возникновении событий.</span><span class="sxs-lookup"><span data-stu-id="d5c49-130">A major benefit of using Event Grid is that it uses a *push* mechanism to send messages when events occur.</span></span> <span data-ttu-id="d5c49-131">Архитектура принудительной потребляет меньше ресурсов и масштабируется лучше, чем *опроса* механизмы.</span><span class="sxs-lookup"><span data-stu-id="d5c49-131">The push architecture consumes fewer resources and scales better than *polling* mechanisms.</span></span> <span data-ttu-id="d5c49-132">Опроса необходимо проверить наличие обновлений на регулярной основе.</span><span class="sxs-lookup"><span data-stu-id="d5c49-132">Polling must check for updates on a regular interval.</span></span>

## <a name="event-grid-vs-other-azure-messaging-services"></a><span data-ttu-id="d5c49-133">"Сетка событий" и других служб Azure для обмена сообщениями</span><span class="sxs-lookup"><span data-stu-id="d5c49-133">Event Grid vs. other Azure messaging services</span></span>

<span data-ttu-id="d5c49-134">Azure предоставляет несколько служб обмена сообщениями, включая [концентраторов событий](https://docs.microsoft.com/azure/event-hubs) и [служебной шины](https://docs.microsoft.com/azure/service-bus-messaging).</span><span class="sxs-lookup"><span data-stu-id="d5c49-134">Azure provides several messaging services, including [Event Hubs](https://docs.microsoft.com/azure/event-hubs) and [Service Bus](https://docs.microsoft.com/azure/service-bus-messaging).</span></span> <span data-ttu-id="d5c49-135">Каждый предназначен для определенного набора вариантов использования.</span><span class="sxs-lookup"><span data-stu-id="d5c49-135">Each is designed to address a specific set of use cases.</span></span> <span data-ttu-id="d5c49-136">Следующей схеме представлен общий обзор различий между службами.</span><span class="sxs-lookup"><span data-stu-id="d5c49-136">The following diagram provides a high-level overview of the differences between the services.</span></span>

![Обмена сообщениями сравнения в Azure](./media/azure-messaging-services.png)

<span data-ttu-id="d5c49-138">Более подробное сравнение см. в разделе [сравнение служб обмена сообщениями](https://docs.microsoft.com/azure/event-grid/compare-messaging-services).</span><span class="sxs-lookup"><span data-stu-id="d5c49-138">For a more in-depth comparison, see [Compare messaging services](https://docs.microsoft.com/azure/event-grid/compare-messaging-services).</span></span>

## <a name="performance-targets"></a><span data-ttu-id="d5c49-139">Целевые показатели по производительности</span><span class="sxs-lookup"><span data-stu-id="d5c49-139">Performance targets</span></span>

<span data-ttu-id="d5c49-140">С помощью сетки событий, можно воспользоваться преимуществами следующих производительности гарантирует:</span><span class="sxs-lookup"><span data-stu-id="d5c49-140">Using Event Grid you can take advantage of the following performance guarantees:</span></span>

* <span data-ttu-id="d5c49-141">Subsecond end-to-end задержки на 99-го процентиля.</span><span class="sxs-lookup"><span data-stu-id="d5c49-141">Subsecond end-to-end latency in the 99th percentile.</span></span>
* <span data-ttu-id="d5c49-142">доступность 99,99%.</span><span class="sxs-lookup"><span data-stu-id="d5c49-142">99.99% availability.</span></span>
* <span data-ttu-id="d5c49-143">10 млн событий в секунду для каждого региона.</span><span class="sxs-lookup"><span data-stu-id="d5c49-143">10 million events per second per region.</span></span>
* <span data-ttu-id="d5c49-144">100 миллионов подписки на регион.</span><span class="sxs-lookup"><span data-stu-id="d5c49-144">100 million subscriptions per region.</span></span>
* <span data-ttu-id="d5c49-145">Издатель задержке в 50 мс.</span><span class="sxs-lookup"><span data-stu-id="d5c49-145">50-ms publisher latency.</span></span>
* <span data-ttu-id="d5c49-146">24-часовом повторных попыток с экспоненциальной отсрочки для гарантированной доставки в окне 1 день.</span><span class="sxs-lookup"><span data-stu-id="d5c49-146">24-hour retry with exponential back-off for guaranteed delivery in the 1-day window.</span></span>
* <span data-ttu-id="d5c49-147">Прозрачную региональную отработку отказа.</span><span class="sxs-lookup"><span data-stu-id="d5c49-147">Transparent regional failover.</span></span>

## <a name="event-grid-schema"></a><span data-ttu-id="d5c49-148">Схема сетки событий</span><span class="sxs-lookup"><span data-stu-id="d5c49-148">Event Grid schema</span></span>

<span data-ttu-id="d5c49-149">Сетка событий использует со стандартной схемой программы-оболочки для пользовательских событий.</span><span class="sxs-lookup"><span data-stu-id="d5c49-149">Event Grid uses a standard schema to wrap custom events.</span></span> <span data-ttu-id="d5c49-150">Схема выглядит подобно конверт, обертывающий ваш пользовательский элемент data.</span><span class="sxs-lookup"><span data-stu-id="d5c49-150">The schema is like an envelope that wraps your custom data element.</span></span> <span data-ttu-id="d5c49-151">Ниже приведен пример сообщения "Сетка событий".</span><span class="sxs-lookup"><span data-stu-id="d5c49-151">Here is an example Event Grid message:</span></span>

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

<span data-ttu-id="d5c49-152">Все о сообщение является стандартным, за исключением `data` свойство.</span><span class="sxs-lookup"><span data-stu-id="d5c49-152">Everything about the message is standard except the `data` property.</span></span> <span data-ttu-id="d5c49-153">Вы можете проверить сообщение и использовать `eventType` и `dataVersion` выполнить десериализацию настраиваемых часть полезных данных.</span><span class="sxs-lookup"><span data-stu-id="d5c49-153">You can inspect the message and use the `eventType` and `dataVersion` to de-serialize the custom portion of the payload.</span></span>

## <a name="azure-resources"></a><span data-ttu-id="d5c49-154">ресурсов Azure</span><span class="sxs-lookup"><span data-stu-id="d5c49-154">Azure resources</span></span>

<span data-ttu-id="d5c49-155">Главным преимуществом с помощью сетки событий является автоматическое сообщения, созданные Azure.</span><span class="sxs-lookup"><span data-stu-id="d5c49-155">A major benefit of using Event Grid is the automatic messages produced by Azure.</span></span> <span data-ttu-id="d5c49-156">В Azure, ресурсы автоматически опубликовать *разделе* , позволяет подписаться на различные события.</span><span class="sxs-lookup"><span data-stu-id="d5c49-156">In Azure, resources automatically publish to a *topic* that allows you to subscribe for various events.</span></span> <span data-ttu-id="d5c49-157">Ниже перечислены типы ресурсов, типы сообщений и событий, которые были доступны автоматически.</span><span class="sxs-lookup"><span data-stu-id="d5c49-157">The following table lists the resource types, message types, and events that are available automatically.</span></span>

| <span data-ttu-id="d5c49-158">Ресурсов Azure</span><span class="sxs-lookup"><span data-stu-id="d5c49-158">Azure resource</span></span> | <span data-ttu-id="d5c49-159">Тип события.</span><span class="sxs-lookup"><span data-stu-id="d5c49-159">Event type</span></span> | <span data-ttu-id="d5c49-160">Описание</span><span class="sxs-lookup"><span data-stu-id="d5c49-160">Description</span></span> |
| -------------- | ---------- | ----------- |
| <span data-ttu-id="d5c49-161">Подписка Azure</span><span class="sxs-lookup"><span data-stu-id="d5c49-161">Azure subscription</span></span> | <span data-ttu-id="d5c49-162">Microsoft.Resources.ResourceWriteSuccess</span><span class="sxs-lookup"><span data-stu-id="d5c49-162">Microsoft.Resources.ResourceWriteSuccess</span></span> | <span data-ttu-id="d5c49-163">Возникает при создании ресурса, или операция обновления завершается успешно.</span><span class="sxs-lookup"><span data-stu-id="d5c49-163">Raised when a resource create or update operation succeeds.</span></span> |
| | <span data-ttu-id="d5c49-164">Microsoft.Resources.ResourceWriteFailure</span><span class="sxs-lookup"><span data-stu-id="d5c49-164">Microsoft.Resources.ResourceWriteFailure</span></span> | <span data-ttu-id="d5c49-165">Вызывается, когда Создание ресурса или происходит сбой операции обновления.</span><span class="sxs-lookup"><span data-stu-id="d5c49-165">Raised when a resource create or update operation fails.</span></span> |
| | <span data-ttu-id="d5c49-166">Microsoft.Resources.ResourceWriteCancel</span><span class="sxs-lookup"><span data-stu-id="d5c49-166">Microsoft.Resources.ResourceWriteCancel</span></span> | <span data-ttu-id="d5c49-167">Возникает при создании ресурса, или операция обновления отмене.</span><span class="sxs-lookup"><span data-stu-id="d5c49-167">Raised when a resource create or update operation is canceled.</span></span> |
|  | <span data-ttu-id="d5c49-168">Microsoft.Resources.ResourceDeleteSuccess</span><span class="sxs-lookup"><span data-stu-id="d5c49-168">Microsoft.Resources.ResourceDeleteSuccess</span></span> | <span data-ttu-id="d5c49-169">Возникает при успешном удалении ресурса.</span><span class="sxs-lookup"><span data-stu-id="d5c49-169">Raised when a resource delete operation succeeds.</span></span> |
|  | <span data-ttu-id="d5c49-170">Microsoft.Resources.ResourceDeleteFailure</span><span class="sxs-lookup"><span data-stu-id="d5c49-170">Microsoft.Resources.ResourceDeleteFailure</span></span> | <span data-ttu-id="d5c49-171">Возникает при неудачном удалении ресурса.</span><span class="sxs-lookup"><span data-stu-id="d5c49-171">Raised when a resource delete operation fails.</span></span> |
| | <span data-ttu-id="d5c49-172">Microsoft.Resources.ResourceDeleteCancel</span><span class="sxs-lookup"><span data-stu-id="d5c49-172">Microsoft.Resources.ResourceDeleteCancel</span></span> | <span data-ttu-id="d5c49-173">Вызывается, когда отменяется операция удаления ресурса.</span><span class="sxs-lookup"><span data-stu-id="d5c49-173">Raised when a resource delete operation is canceled.</span></span> <span data-ttu-id="d5c49-174">Это событие происходит при отмене развертывания шаблона.</span><span class="sxs-lookup"><span data-stu-id="d5c49-174">This event happens when a template deployment is canceled.</span></span> |
| <span data-ttu-id="d5c49-175">Хранилище BLOB-объектов</span><span class="sxs-lookup"><span data-stu-id="d5c49-175">Blob storage</span></span> | <span data-ttu-id="d5c49-176">Microsoft.Storage.BlobCreated</span><span class="sxs-lookup"><span data-stu-id="d5c49-176">Microsoft.Storage.BlobCreated</span></span> | <span data-ttu-id="d5c49-177">Возникает при создании большого двоичного объекта.</span><span class="sxs-lookup"><span data-stu-id="d5c49-177">Raised when a blob is created.</span></span> |
| | <span data-ttu-id="d5c49-178">Microsoft.Storage.BlobDeleted</span><span class="sxs-lookup"><span data-stu-id="d5c49-178">Microsoft.Storage.BlobDeleted</span></span> | <span data-ttu-id="d5c49-179">Возникает при удалении большого двоичного объекта.</span><span class="sxs-lookup"><span data-stu-id="d5c49-179">Raised when a blob is deleted.</span></span> |
| <span data-ttu-id="d5c49-180">Концентраторы событий</span><span class="sxs-lookup"><span data-stu-id="d5c49-180">Event hubs</span></span> | <span data-ttu-id="d5c49-181">Microsoft.EventHub.CaptureFileCreated</span><span class="sxs-lookup"><span data-stu-id="d5c49-181">Microsoft.EventHub.CaptureFileCreated</span></span> | <span data-ttu-id="d5c49-182">Возникает при создании файла записи.</span><span class="sxs-lookup"><span data-stu-id="d5c49-182">Raised when a capture file is created.</span></span>
| <span data-ttu-id="d5c49-183">Центр Интернета вещей</span><span class="sxs-lookup"><span data-stu-id="d5c49-183">IoT Hub</span></span> | <span data-ttu-id="d5c49-184">Microsoft.Devices.DeviceCreated</span><span class="sxs-lookup"><span data-stu-id="d5c49-184">Microsoft.Devices.DeviceCreated</span></span> | <span data-ttu-id="d5c49-185">Публикуется при регистрации устройства в центре Интернета вещей.</span><span class="sxs-lookup"><span data-stu-id="d5c49-185">Published when a device is registered to an IoT hub.</span></span> |
| | <span data-ttu-id="d5c49-186">Microsoft.Devices.DeviceDeleted</span><span class="sxs-lookup"><span data-stu-id="d5c49-186">Microsoft.Devices.DeviceDeleted</span></span> | <span data-ttu-id="d5c49-187">Публикуется при удалении устройства из центра Интернета вещей.</span><span class="sxs-lookup"><span data-stu-id="d5c49-187">Published when a device is deleted from an IoT hub.</span></span> |
| <span data-ttu-id="d5c49-188">Группы ресурсов</span><span class="sxs-lookup"><span data-stu-id="d5c49-188">Resource groups</span></span> | <span data-ttu-id="d5c49-189">Microsoft.Resources.ResourceWriteSuccess</span><span class="sxs-lookup"><span data-stu-id="d5c49-189">Microsoft.Resources.ResourceWriteSuccess</span></span> | <span data-ttu-id="d5c49-190">Возникает при создании ресурса, или операция обновления завершается успешно.</span><span class="sxs-lookup"><span data-stu-id="d5c49-190">Raised when a resource create or update operation succeeds.</span></span> |
| | <span data-ttu-id="d5c49-191">Microsoft.Resources.ResourceWriteFailure</span><span class="sxs-lookup"><span data-stu-id="d5c49-191">Microsoft.Resources.ResourceWriteFailure</span></span> | <span data-ttu-id="d5c49-192">Вызывается, когда Создание ресурса или происходит сбой операции обновления.</span><span class="sxs-lookup"><span data-stu-id="d5c49-192">Raised when a resource create or update operation fails.</span></span> |
| | <span data-ttu-id="d5c49-193">Microsoft.Resources.ResourceWriteCancel</span><span class="sxs-lookup"><span data-stu-id="d5c49-193">Microsoft.Resources.ResourceWriteCancel</span></span> | <span data-ttu-id="d5c49-194">Возникает при создании ресурса, или операция обновления отмене.</span><span class="sxs-lookup"><span data-stu-id="d5c49-194">Raised when a resource create or update operation is canceled.</span></span> |
| | <span data-ttu-id="d5c49-195">Microsoft.Resources.ResourceDeleteSuccess</span><span class="sxs-lookup"><span data-stu-id="d5c49-195">Microsoft.Resources.ResourceDeleteSuccess</span></span> | <span data-ttu-id="d5c49-196">Возникает при успешном удалении ресурса.</span><span class="sxs-lookup"><span data-stu-id="d5c49-196">Raised when a resource delete operation succeeds.</span></span> |
| | <span data-ttu-id="d5c49-197">Microsoft.Resources.ResourceDeleteFailure</span><span class="sxs-lookup"><span data-stu-id="d5c49-197">Microsoft.Resources.ResourceDeleteFailure</span></span> | <span data-ttu-id="d5c49-198">Возникает при неудачном удалении ресурса.</span><span class="sxs-lookup"><span data-stu-id="d5c49-198">Raised when a resource delete operation fails.</span></span> |
| | <span data-ttu-id="d5c49-199">Microsoft.Resources.ResourceDeleteCancel</span><span class="sxs-lookup"><span data-stu-id="d5c49-199">Microsoft.Resources.ResourceDeleteCancel</span></span> | <span data-ttu-id="d5c49-200">Вызывается, когда отменяется операция удаления ресурса.</span><span class="sxs-lookup"><span data-stu-id="d5c49-200">Raised when a resource delete operation is canceled.</span></span> <span data-ttu-id="d5c49-201">Это событие происходит при отмене развертывания шаблона.</span><span class="sxs-lookup"><span data-stu-id="d5c49-201">This event happens when a template deployment is canceled.</span></span> |

<span data-ttu-id="d5c49-202">Дополнительные сведения см. в разделе [схема событий службы "Сетка событий Azure"](https://docs.microsoft.com/azure/event-grid/event-schema).</span><span class="sxs-lookup"><span data-stu-id="d5c49-202">For more information, see [Azure Event Grid event schema](https://docs.microsoft.com/azure/event-grid/event-schema).</span></span>

<span data-ttu-id="d5c49-203">"Сетка событий" доступны из любого типа приложения, даже если он работает локально.</span><span class="sxs-lookup"><span data-stu-id="d5c49-203">You can access Event Grid from any type of application, even one that runs on-premises.</span></span>

## <a name="conclusion"></a><span data-ttu-id="d5c49-204">Заключение</span><span class="sxs-lookup"><span data-stu-id="d5c49-204">Conclusion</span></span>

<span data-ttu-id="d5c49-205">В этой главе вы узнали о платформе Azure без сервера, который состоит из функций Azure, Logic Apps и "Сетка событий".</span><span class="sxs-lookup"><span data-stu-id="d5c49-205">In this chapter you learned about the Azure serverless platform that is composed of Azure Functions, Logic Apps, and Event Grid.</span></span> <span data-ttu-id="d5c49-206">Можно использовать эти ресурсы для построения архитектуры полностью бессерверного приложения или создать гибридное решение, которое взаимодействует с другими облачными ресурсами, а также на локальных серверах.</span><span class="sxs-lookup"><span data-stu-id="d5c49-206">You can use these resources to build an entirely serverless app architecture, or create a hybrid solution that interacts with other cloud resources and on-premises servers.</span></span> <span data-ttu-id="d5c49-207">Вместе с платформой данных в бессерверной, такие как [Azure SQL](https://docs.microsoft.com/azure/sql-database) или [CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction), вы можете создавать полностью управляемая облачная собственного приложения.</span><span class="sxs-lookup"><span data-stu-id="d5c49-207">Combined with a serverless data platform such as [Azure SQL](https://docs.microsoft.com/azure/sql-database) or [CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction), you can build fully managed cloud native applications.</span></span>

## <a name="recommended-resources"></a><span data-ttu-id="d5c49-208">Рекомендуемые ресурсы</span><span class="sxs-lookup"><span data-stu-id="d5c49-208">Recommended resources</span></span>

* [<span data-ttu-id="d5c49-209">Планы службы приложений</span><span class="sxs-lookup"><span data-stu-id="d5c49-209">App service plans</span></span>](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)
* [<span data-ttu-id="d5c49-210">Application Insights</span><span class="sxs-lookup"><span data-stu-id="d5c49-210">Application Insights</span></span>](https://docs.microsoft.com/azure/application-insights)
* [<span data-ttu-id="d5c49-211">Аналитика Application Insights</span><span class="sxs-lookup"><span data-stu-id="d5c49-211">Application Insights Analytics</span></span>](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)
* [<span data-ttu-id="d5c49-212">Azure: Перенос приложения в облако с помощью бессерверных функций Azure</span><span class="sxs-lookup"><span data-stu-id="d5c49-212">Azure: Bring your app to the cloud with serverless Azure Functions</span></span>](https://channel9.msdn.com/events/Connect/2017/E102)
* [<span data-ttu-id="d5c49-213">Сетка событий Azure</span><span class="sxs-lookup"><span data-stu-id="d5c49-213">Azure Event Grid</span></span>](https://docs.microsoft.com/azure/azure-event-grid/overview)
* [<span data-ttu-id="d5c49-214">Схема событий службы "Сетка событий" Azure</span><span class="sxs-lookup"><span data-stu-id="d5c49-214">Azure Event Grid event schema</span></span>](https://docs.microsoft.com/azure/event-grid/event-schema)
* [<span data-ttu-id="d5c49-215">Концентраторы событий Azure</span><span class="sxs-lookup"><span data-stu-id="d5c49-215">Azure Event Hubs</span></span>](https://docs.microsoft.com/azure/event-hubs)
* [<span data-ttu-id="d5c49-216">Документация по функциям Azure</span><span class="sxs-lookup"><span data-stu-id="d5c49-216">Azure Functions documentation</span></span>](https://docs.microsoft.com/azure/azure-functions)
* [<span data-ttu-id="d5c49-217">Триггеры функций Azure и основные понятия привязки</span><span class="sxs-lookup"><span data-stu-id="d5c49-217">Azure Functions triggers and bindings concepts</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)
* [<span data-ttu-id="d5c49-218">Azure Logic Apps</span><span class="sxs-lookup"><span data-stu-id="d5c49-218">Azure Logic Apps</span></span>](https://docs.microsoft.com/azure/logic-apps)
* [<span data-ttu-id="d5c49-219">Служебная шина Azure</span><span class="sxs-lookup"><span data-stu-id="d5c49-219">Azure Service Bus</span></span>](https://docs.microsoft.com/azure/service-bus-messaging)
* [<span data-ttu-id="d5c49-220">Хранилище таблиц Azure</span><span class="sxs-lookup"><span data-stu-id="d5c49-220">Azure Table Storage</span></span>](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)
* [<span data-ttu-id="d5c49-221">Сравнение функций 1.x и 2.x</span><span class="sxs-lookup"><span data-stu-id="d5c49-221">Compare functions 1.x and 2.x</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-versions)
* [<span data-ttu-id="d5c49-222">Подключение к локальным источникам данных с Azure на локальный шлюз данных</span><span class="sxs-lookup"><span data-stu-id="d5c49-222">Connecting to on-premises data sources with Azure On-premises Data Gateway</span></span>](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)
* [<span data-ttu-id="d5c49-223">Создание первой функции на портале Azure</span><span class="sxs-lookup"><span data-stu-id="d5c49-223">Create your first function in the Azure portal</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)
* [<span data-ttu-id="d5c49-224">Создание первой функции с помощью Azure CLI</span><span class="sxs-lookup"><span data-stu-id="d5c49-224">Create your first function using the Azure CLI</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)
* [<span data-ttu-id="d5c49-225">Создание первой функции с помощью Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d5c49-225">Create your first function using Visual Studio</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)
* [<span data-ttu-id="d5c49-226">Функции поддерживаемые языки</span><span class="sxs-lookup"><span data-stu-id="d5c49-226">Functions supported languages</span></span>](https://docs.microsoft.com/azure/azure-functions/supported-languages)
* [<span data-ttu-id="d5c49-227">Мониторинг функций Azure</span><span class="sxs-lookup"><span data-stu-id="d5c49-227">Monitor Azure Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)
* [<span data-ttu-id="d5c49-228">Работа с прокси функций Azure</span><span class="sxs-lookup"><span data-stu-id="d5c49-228">Work with Azure Functions Proxies</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-proxies)

>[!div class="step-by-step"]
<span data-ttu-id="d5c49-229">[Назад](logic-apps.md)
[Вперед](durable-azure-functions.md)</span><span class="sxs-lookup"><span data-stu-id="d5c49-229">[Previous](logic-apps.md)
[Next](durable-azure-functions.md)</span></span>
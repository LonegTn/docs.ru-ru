---
title: Сопоставление eShopOnContainers со службами Azure
description: Сопоставление eShopOnContainers со службами Azure, такими как служба Kubernetes Azure, шлюз API и служебная шина Azure.
ms.date: 06/30/2019
ms.openlocfilehash: 67430da18c0a12c694426214de33e85c2113e454
ms.sourcegitcommit: 992f80328b51b165051c42ff5330788627abe973
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/11/2019
ms.locfileid: "73841195"
---
# <a name="mapping-eshoponcontainers-to-azure-services"></a>Сопоставление eShopOnContainers со службами Azure

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Хотя это и не является обязательным, Azure хорошо подходит для поддержки eShopOnContainers, поскольку проект был создан в качестве облачного приложения. Приложение создается с помощью .NET Core, поэтому оно может выполняться в контейнерах Linux или Windows в зависимости от узла DOCKER. Приложение состоит из нескольких автономных микрослужб, каждая из которых имеет собственные данные. Различные микрослужбы демонстрируют различные подходы, от простых операций CRUD до более сложных шаблонов DDD и CQRS. Микрослужбы взаимодействуют с клиентами по протоколу HTTP и друг с другом через связь на основе сообщений. Приложение поддерживает несколько платформ для клиентов, так как оно использует протокол HTTP в качестве стандартного протокола связи и включает ASP.NET Core и мобильные приложения Xamarin, работающие на платформах Android, iOS и Windows.

Архитектура приложения показана на рисунке 2-5. В левой части находятся клиентские приложения, разбитые на мобильные, традиционные веб-приложения и разновидности веб-приложений с одной страницей (SPA). Справа находятся компоненты на стороне сервера, которые составляют систему, каждая из которых может размещаться в контейнерах DOCKER и кластерах Kubernetes. Традиционное веб-приложение работает на основе приложения ASP.NET Core MVC, показанного желтым цветом. Это приложение и приложения для мобильных устройств и веб-приложений SPA взаимодействуют с отдельными микрослужбами через один или несколько шлюзов API. Шлюзы API соответствуют шаблону "Серверная часть для внешних интерфейсов" (БФФ), что означает, что каждый шлюз предназначен для поддержки данного клиентского клиента. Отдельные микрослужбы перечислены справа от шлюзов API и включают как бизнес-логику, так и хранилище сохраняемости. Различные службы используют SQL Server базы данных, экземпляры кэша Redis и MongoDB/CosmosDB Stores. В правом углу находится шина системных событий, используемая для обмена данными между микрослужбами.

![архитектура eShopOnContainers](./media/eshoponcontainers-architecture.png)
**рис. 2-5**. Архитектура eShopOnContainers.

Серверные компоненты этой архитектуры легко сопоставляются со службами Azure.

## <a name="container-orchestration-and-clustering"></a>Оркестрации контейнеров и кластеризация

Службы, размещенные в контейнере приложения, от ASP.NET Core приложений MVC до отдельного каталога и заказа микрослужб, могут размещаться и управляться в службе Azure Kubernetes Service (AKS). Приложение может быть запущено локально в DOCKER и Kubernetes, а те же контейнеры можно развернуть в промежуточной и рабочей средах, размещенных в AKS. Этот процесс можно автоматизировать, как мы увидим в следующем разделе.

AKS предоставляет службы управления для отдельных кластеров контейнеров. Приложение будет развертывать отдельные кластеры AKS для каждой микрослужбы, показанной на схеме архитектуры выше. Такой подход позволяет каждой отдельной службе масштабироваться независимо от требований к ресурсам. Каждую микрослужбу также можно развернуть независимо, и в идеале такие развертывания должны вызывать нулевое время простоя системы.

## <a name="api-gateway"></a>Шлюз API

Приложение eShopOnContainers имеет несколько клиентских клиентов и несколько разных серверных служб. Между клиентскими приложениями и микрослужбами, которые их поддерживают, нет соответствия "один к одному". В таком случае может возникнуть значительная сложность при написании клиентского программного обеспечения для взаимодействия с различными серверными службами безопасным способом. Каждый клиент должен решить эту сложность самостоятельно, что приведет к дублированию и многим местам, в которых будут обновляться изменения служб или реализованы новые политики.

Управление API Azure (APIM) помогает организациям публиковать интерфейсы API единообразно, управляемым образом. APIM состоит из трех компонентов: шлюза API и портала администрирования (портал Azure) и портала разработчика.

Шлюз API принимает вызовы API и направляет их в соответствующий API серверной части. Кроме того, он может предоставлять дополнительные службы, такие как проверка ключей API или маркеров JWT и преобразование API, без изменения кода (например, для размещения клиентов, ожидающих более старый интерфейс).

Портал Azure, где вы определяете схему API и упаковывают различные интерфейсы API в продукты. Вы также настраиваете доступ пользователей, просмотр отчетов и настройку политик для квот или преобразований.

Портал разработчика выступает в качестве основного ресурса для разработчиков. Он предоставляет разработчикам документацию по API, интерактивную консоль тестирования и создает отчеты по собственному использованию. Разработчики также используют портал для создания собственных учетных записей и управления ими, включая подписку и поддержку ключей API.

С помощью APIM приложения могут предоставлять несколько различных групп служб, каждый из которых предоставляет серверную часть для конкретного клиентского клиента. APIM рекомендуется использовать для сложных сценариев. Для более простых потребностей можно использовать упрощенный шлюз API Оцелот. Приложение eShopOnContainers использует Оцелот из-за простоты и его можно развернуть в той же среде приложения, что и само приложение. [Дополнительные сведения о eShopOnContainers, APIM и Оцелот.](https://docs.microsoft.com/dotnet/architecture/microservices/architect-microservice-container-applications/direct-client-to-microservice-communication-versus-the-api-gateway-pattern#azure-api-management)

Другой вариант, если приложение использует AKS, — развертывание контроллера входящего шлюза Azure в качестве Pod в кластере AKS. Это позволяет кластеру интегрироваться с шлюзом приложений Azure, позволяя шлюзу балансировать нагрузку на трафик в модули AKS. Дополнительные [сведения о контроллере входящего трафика шлюза Azure для AKS](https://github.com/Azure/application-gateway-kubernetes-ingress).

## <a name="data"></a>Data

Различные серверные службы, используемые eShopOnContainers, имеют разные требования к хранению. Несколько микрослужб используют SQL Server базы данных. Микрослужба корзины использует кэш Redis для сохранения. Микрослужба Locations ожидает для своих данных API MongoDB. Azure поддерживает каждый из этих форматов данных.

Для поддержки SQL Serverных баз данных Azure содержит продукты для всех элементов, начиная с отдельных баз данных и до высокомасштабируемых пулов эластичных баз данных SQL. Отдельные микрослужбы можно настроить для быстрого и простого взаимодействия с собственными SQL Server базами данных. Эти базы данных можно масштабировать по мере необходимости для поддержки каждой отдельной микрослужбы в соответствии с потребностями.

В приложении eShopOnContainers хранится текущая корзина покупок пользователя между запросами. Это управляется микрослужбой корзины, которая хранит данные в кэше Redis. В процессе разработки этот кэш можно развернуть в контейнере, в то время как в рабочей среде он может использовать кэш Azure для Redis. Кэш Azure для Redis — это полностью управляемая служба, которая обеспечивает высокую производительность и надежность без необходимости развертывать экземпляры Redis или контейнеры и управлять ими самостоятельно.

Микрослужба Locations использует базу данных MongoDB NoSQL для сохраняемости. Во время разработки база данных может быть развернута в собственном контейнере, а в рабочей среде служба может использовать [API Azure Cosmos DB для MongoDB](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction). Одним из преимуществ Azure Cosmos DB является возможность использовать несколько различных протоколов связи, включая API SQL и общие API NoSQL, включая MongoDB, Cassandra, Gremlin и хранилище таблиц Azure. Azure Cosmos DB предлагает полностью управляемую и глобально распределенную базу данных в качестве службы, которая может масштабироваться в соответствии с потребностями служб, использующих ее.

Распределенные данные в облачных приложениях более подробно рассматриваются в [главе 5](distributed-data.md).

## <a name="event-bus"></a>Шина событий

Приложение использует события для обмена изменениями между разными службами. Эту функцию можно реализовать с помощью различных реализаций, а локально приложение eShopOnContainers использует [RabbitMQ](https://www.rabbitmq.com/). При размещении в Azure приложение будет использовать [служебную шину Azure](https://docs.microsoft.com/azure/service-bus/) для обмена сообщениями. Служебная шина Azure — это полностью управляемый брокер сообщений интеграции, который позволяет приложениям и службам взаимодействовать друг с другом в несвязанном, надежном асинхронном режиме. Служебная шина Azure поддерживает отдельные очереди, а также отдельные *разделы* для поддержки сценариев подписчиков издателя. Приложение eShopOnContainers будет использовать разделы с служебной шиной Azure для поддержки распространения сообщений от одной микрослужбы к другой микрослужбе, необходимой для реагирования на конкретное сообщение.

## <a name="resiliency"></a>Устойчивость

После развертывания в рабочей среде приложение eShopOnContainers сможет воспользоваться преимуществами нескольких доступных служб Azure, чтобы повысить устойчивость. Приложение публикует проверки работоспособности, которые можно интегрировать с Application Insights для предоставления отчетов и оповещений на основе доступности приложения. Ресурсы Azure также предоставляют журналы диагностики, которые можно использовать для обнаружения и исправления ошибок и проблем с производительностью. В журналах ресурсов содержатся подробные сведения о том, когда и как используются другие ресурсы Azure. Дополнительные сведения о функциях обеспечения устойчивости, встроенных в облако, см. в [главе 6](resiliency.md).

## <a name="references"></a>Ссылки

- [Архитектура eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Architecture)
- [Управление микрослужбами и многоконтейнерными приложениями для обеспечения высокого уровня масштабируемости и доступности](https://docs.microsoft.com/dotnet/architecture/microservices/architect-microservice-container-applications/scalable-available-multi-container-microservice-applications)
- [Управление API Azure](https://docs.microsoft.com/azure/api-management/api-management-key-concepts)
- [Обзор базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview)
- [Кэш Azure для Redis](https://azure.microsoft.com/services/cache/)
- [API Azure Cosmos DB для MongoDB](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction)
- [Служебная шина Azure](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)
- [Обзор Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview)

>[!div class="step-by-step"]
>[Назад](introduce-eshoponcontainers-reference-app.md)
>[Вперед](deploy-eshoponcontainers-azure.md)
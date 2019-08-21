---
title: Примеры бизнес-сценариев и примеры использования для бессерверных приложений
description: Изучите практический подход, обращаясь к примерам из обработки изображений на мобильные серверные и ETL-конвейеры.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: adc4e1f3249cd72c423430ad4cb5dbb8eea8baf9
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577287"
---
# <a name="serverless-business-scenarios-and-use-cases"></a><span data-ttu-id="427cd-103">Бессерверные сценарии и варианты использования для бизнеса</span><span class="sxs-lookup"><span data-stu-id="427cd-103">Serverless business scenarios and use cases</span></span>

<span data-ttu-id="427cd-104">Существует множество вариантов использования и сценариев для бессерверных приложений.</span><span class="sxs-lookup"><span data-stu-id="427cd-104">There are many use cases and scenarios for serverless applications.</span></span> <span data-ttu-id="427cd-105">В этой главе содержатся примеры, иллюстрирующие различные сценарии.</span><span class="sxs-lookup"><span data-stu-id="427cd-105">This chapter includes samples that illustrate the different scenarios.</span></span> <span data-ttu-id="427cd-106">Сценарии включают ссылки на связанные документы и репозитории общедоступного исходного кода.</span><span class="sxs-lookup"><span data-stu-id="427cd-106">The scenarios include links to related documentation and public source code repositories.</span></span> <span data-ttu-id="427cd-107">Примеры в этой главе позволяют приступить к созданию и реализации бессерверных решений.</span><span class="sxs-lookup"><span data-stu-id="427cd-107">The samples in this chapter enable you to get started on your own building and implementing serverless solutions.</span></span>

## <a name="analyze-and-archive-images"></a><span data-ttu-id="427cd-108">Анализ и архивирование образов</span><span class="sxs-lookup"><span data-stu-id="427cd-108">Analyze and archive images</span></span>

<span data-ttu-id="427cd-109">В этом примере демонстрируются бессерверные события (сетка событий), рабочие процессы (приложение логики) и код (функции Azure).</span><span class="sxs-lookup"><span data-stu-id="427cd-109">This sample demonstrates serverless events (Event Grid), workflows (Logic App), and code (Azure Functions).</span></span> <span data-ttu-id="427cd-110">Также показано, как интегрироваться с другим ресурсом, в данном случае Cognitive Services для анализа изображений.</span><span class="sxs-lookup"><span data-stu-id="427cd-110">It also shows how to integrate with another resource, in this case Cognitive Services for image analysis.</span></span>

<span data-ttu-id="427cd-111">Консольное приложение позволяет передавать ссылку на URL-адрес в Интернете.</span><span class="sxs-lookup"><span data-stu-id="427cd-111">A console application allows you to pass a link to a URL on the web.</span></span> <span data-ttu-id="427cd-112">Приложение публикует URL-адрес как сообщение сетки событий.</span><span class="sxs-lookup"><span data-stu-id="427cd-112">The app publishes the URL as an event grid message.</span></span> <span data-ttu-id="427cd-113">Параллельно приложение-функция и приложение логики подписываются на сообщение.</span><span class="sxs-lookup"><span data-stu-id="427cd-113">In parallel, a serverless function app and a logic app subscribe to the message.</span></span> <span data-ttu-id="427cd-114">Приложение-функция бессерверной функции сериализует образ в хранилище BLOB-объектов.</span><span class="sxs-lookup"><span data-stu-id="427cd-114">The serverless function app serializes the image to blob storage.</span></span> <span data-ttu-id="427cd-115">Он также хранит информацию в хранилище таблиц Azure.</span><span class="sxs-lookup"><span data-stu-id="427cd-115">It also stores information in Azure Table Storage.</span></span> <span data-ttu-id="427cd-116">Метаданные хранят исходный URL-адрес изображения и имя образа большого двоичного объекта.</span><span class="sxs-lookup"><span data-stu-id="427cd-116">The metadata stores the original image URL and the name of the blob image.</span></span> <span data-ttu-id="427cd-117">Приложение логики взаимодействует с API Пользовательское визуальное распознавание для анализа изображения и создания сопроводительного заголовка, созданного на компьютере.</span><span class="sxs-lookup"><span data-stu-id="427cd-117">The logic app interacts with the Custom Vision API to analyze the image and create a machine-generated caption.</span></span> <span data-ttu-id="427cd-118">Заголовок хранится в таблице метаданных.</span><span class="sxs-lookup"><span data-stu-id="427cd-118">The caption is stored in the metadata table.</span></span>

![Архитектура анализа и архивирования образов](./media/image-processing-example.png)

<span data-ttu-id="427cd-120">Отдельное одностраничное приложение (SPA) вызывает бессерверную функцию для получения списка образов и метаданных.</span><span class="sxs-lookup"><span data-stu-id="427cd-120">A separate single page application (SPA) calls a serverless function to get a list of images and metadata.</span></span> <span data-ttu-id="427cd-121">Для каждого образа вызывается другая функция, которая доставляет данные изображения из архива.</span><span class="sxs-lookup"><span data-stu-id="427cd-121">For each image, it calls another function that delivers the image data from the archive.</span></span> <span data-ttu-id="427cd-122">Окончательный результат — коллекция с автоматическими субтитрами.</span><span class="sxs-lookup"><span data-stu-id="427cd-122">The final result is a gallery with automatic captions.</span></span>

![Автоматизированная Коллекция образов](./media/automated-image-gallery.png)

<span data-ttu-id="427cd-124">Полный репозиторий и инструкции по созданию приложения логики доступны здесь: [Приклеивание сетки событий](https://github.com/JeremyLikness/Event-Grid-Glue).</span><span class="sxs-lookup"><span data-stu-id="427cd-124">The full repository and instructions to build the logic app are available here: [Event grid glue](https://github.com/JeremyLikness/Event-Grid-Glue).</span></span>

## <a name="cross-platform-mobile-client-using-xamarinforms-and-functions"></a><span data-ttu-id="427cd-125">Кросс-платформенный мобильный клиент с использованием Xamarin. Forms и функций</span><span class="sxs-lookup"><span data-stu-id="427cd-125">Cross-platform mobile client using Xamarin.Forms and functions</span></span>

<span data-ttu-id="427cd-126">Узнайте, как реализовать простую бессерверную функцию Azure на веб-портале Azure или в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="427cd-126">See how to implement a simple serverless Azure Function in the Azure Web Portal or in Visual Studio.</span></span> <span data-ttu-id="427cd-127">Создание клиента с помощью Xamarin. Forms, работающего в Android, iOS и Windows.</span><span class="sxs-lookup"><span data-stu-id="427cd-127">Build a client with Xamarin.Forms that runs on Android, iOS, and Windows.</span></span> <span data-ttu-id="427cd-128">После этого приложение будет оптимизировано для использования нотация объектов JavaScript (JSON) в качестве носителя обмена данными между сервером и мобильными клиентами с серверной внутренней службой.</span><span class="sxs-lookup"><span data-stu-id="427cd-128">The application is then refined to use JavaScript Object Notation (JSON) as a communication medium between the server and the mobile clients with a serverless back end.</span></span>

<span data-ttu-id="427cd-129">Дополнительные сведения см. в статье [Реализация простой функции Azure с помощью клиента Xamarin. Forms.](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)</span><span class="sxs-lookup"><span data-stu-id="427cd-129">For more information, see [Implementing a simple Azure Function with a Xamarin.Forms client](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)</span></span>

## <a name="generate-a-photo-mosaic-with-serverless-image-recognition"></a><span data-ttu-id="427cd-130">Создание мозаики для фотографий с помощью распознавания несерверных изображений</span><span class="sxs-lookup"><span data-stu-id="427cd-130">Generate a photo mosaic with serverless image recognition</span></span>

<span data-ttu-id="427cd-131">В примере используются функции Azure и Microsoft Cognitive Services Пользовательская служба визуального распознавания для создания мозаики с фотографией из входного изображения.</span><span class="sxs-lookup"><span data-stu-id="427cd-131">The sample uses Azure Functions and Microsoft Cognitive Services Custom Vision Service to generate a photo mosaic from an input image.</span></span> <span data-ttu-id="427cd-132">Модель обучена для распознавания изображений.</span><span class="sxs-lookup"><span data-stu-id="427cd-132">The model is trained to recognize images.</span></span> <span data-ttu-id="427cd-133">При передаче изображения он распознает изображение и выполняет поиск в Bing.</span><span class="sxs-lookup"><span data-stu-id="427cd-133">When an image is uploaded, it recognizes the image and searches with Bing.</span></span> <span data-ttu-id="427cd-134">Исходное изображение будет повторно составлено с использованием результатов поиска.</span><span class="sxs-lookup"><span data-stu-id="427cd-134">The original image is recomposed using the search results.</span></span>

![Фото и мозаика в Орландо глаза](./media/orlando-eye-both.png)

<span data-ttu-id="427cd-136">Например, вы можете обучить модель с ориентирами в Орландо, например с глазом в Орландо.</span><span class="sxs-lookup"><span data-stu-id="427cd-136">For example, you can train your model with Orlando landmarks, such as the Orlando Eye.</span></span> <span data-ttu-id="427cd-137">Пользовательское визуальное распознавание распознает изображение глаза, и функция создаст мозаику с фотографией, состоящую из результатов поиска изображений Bing для «глаз».</span><span class="sxs-lookup"><span data-stu-id="427cd-137">Custom Vision will recognize an image of the Orlando Eye, and the function will create a photo mosaic composed of Bing image search results for "Orlando Eye."</span></span>

<span data-ttu-id="427cd-138">Дополнительные сведения см. в статье генератор для фотомозаики по [функциям Azure](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/).</span><span class="sxs-lookup"><span data-stu-id="427cd-138">For more information, see [Azure Functions photo mosaic generator](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/).</span></span>

## <a name="migrate-an-existing-application-to-the-cloud"></a><span data-ttu-id="427cd-139">Перенос существующего приложения в облако</span><span class="sxs-lookup"><span data-stu-id="427cd-139">Migrate an existing application to the cloud</span></span>

<span data-ttu-id="427cd-140">Как обсуждалось в предыдущих главах, для размещения приложения в локальной среде обычно требуется N-уровневая архитектура.</span><span class="sxs-lookup"><span data-stu-id="427cd-140">As discussed in previous chapters, it's common to embrace an N-Tier architecture to host your application on-premises.</span></span> <span data-ttu-id="427cd-141">Несмотря на то что перенос ресурсов "как есть" с помощью виртуальных машин — это наименее рискованный путь к облаку, многие компании решили использовать возможность рефакторинга своих приложений.</span><span class="sxs-lookup"><span data-stu-id="427cd-141">Although migrating resources "as is" using virtual machines is the least risky path to the cloud, many companies choose to use the opportunity to refactor their applications.</span></span> <span data-ttu-id="427cd-142">К счастью, рефакторинг не обязательно должен быть "все или ничего".</span><span class="sxs-lookup"><span data-stu-id="427cd-142">Fortunately, refactoring doesn't have to be an "all-or-nothing" effort.</span></span> <span data-ttu-id="427cd-143">На самом деле, можно перенести приложение, а затем поэтапно заменить компоненты облачными аналогами в облаке.</span><span class="sxs-lookup"><span data-stu-id="427cd-143">In fact, it's possible to migrate your app then piecemeal replace components with cloud native counterparts.</span></span>

<span data-ttu-id="427cd-144">Приложение использует функцию "прокси" функций Azure для включения рефакторинга конечной точки из устаревшего локального кода в бессерверную конечную точку.</span><span class="sxs-lookup"><span data-stu-id="427cd-144">The application uses the proxies feature of Azure Functions to enable refactoring an endpoint from legacy on-premises code to a serverless endpoint.</span></span>

![Архитектура миграции](./media/migration-architecture.png)

<span data-ttu-id="427cd-146">Прокси-сервер предоставляет одну конечную точку API, которая обновляется для перенаправления отдельных запросов при их перемещении в бессерверные функции.</span><span class="sxs-lookup"><span data-stu-id="427cd-146">The proxy provides a single API endpoint that is updated to reroute individual requests as they're moved into serverless functions.</span></span>

<span data-ttu-id="427cd-147">Вы можете просмотреть видео, которое проходит всю миграцию: Перенос [и сдвиг с помощью безсерверных функций Azure](https://channel9.msdn.com/Events/Connect/2017/E102).</span><span class="sxs-lookup"><span data-stu-id="427cd-147">You can view a video that walks through the entire migration: [Lift and shift with serverless Azure functions](https://channel9.msdn.com/Events/Connect/2017/E102).</span></span> <span data-ttu-id="427cd-148">Доступ к образцу кода: [Перенесите свое приложение](https://github.com/JeremyLikness/bring-own-app-connect-17).</span><span class="sxs-lookup"><span data-stu-id="427cd-148">Access the sample code: [Bring your own app](https://github.com/JeremyLikness/bring-own-app-connect-17).</span></span>

## <a name="parse-a-csv-file-and-insert-into-a-database"></a><span data-ttu-id="427cd-149">Анализ CSV-файла и вставка в базу данных</span><span class="sxs-lookup"><span data-stu-id="427cd-149">Parse a CSV file and insert into a database</span></span>

<span data-ttu-id="427cd-150">Извлечение, преобразование и загрузка (ETL) — это обычная бизнес-функция, которая интегрирует разные системы.</span><span class="sxs-lookup"><span data-stu-id="427cd-150">Extract, Transform, and Load (ETL) is a common business function that integrates different systems.</span></span> <span data-ttu-id="427cd-151">Традиционные подходы часто подразумевают настройку выделенных FTP-серверов, а затем развертывание запланированных заданий для анализа файлов и их преобразования для использования в бизнесе.</span><span class="sxs-lookup"><span data-stu-id="427cd-151">Traditional approaches often involve setting up dedicated FTP servers then deploying scheduled jobs to parse files and translate them for business use.</span></span> <span data-ttu-id="427cd-152">Бессерверная архитектура упрощает работу, поскольку триггер может срабатывать при передаче файла.</span><span class="sxs-lookup"><span data-stu-id="427cd-152">Serverless architecture makes the job easier because a trigger can fire when the file is uploaded.</span></span> <span data-ttu-id="427cd-153">Служба "функции Azure" решает такие задачи, как ETL, с помощью идеальной композиции небольших фрагментов кода, которые сосредоточены на конкретной проблеме.</span><span class="sxs-lookup"><span data-stu-id="427cd-153">Azure Functions tackles tasks like ETL through its ideal composition of small pieces of code that focus on a specific problem.</span></span>

![Снимок экрана, показывающий процесс синтаксического анализа CSV.](./media/serverless-business-scenarios/csv-parse-database-import.png)

<span data-ttu-id="427cd-155">Исходный код и практическое лабораторное занятие см. в разделе [CSV Importing Lab](https://github.com/JeremyLikness/azure-fn-file-process-hol).</span><span class="sxs-lookup"><span data-stu-id="427cd-155">For source code and a hands-on lab, see [CSV import lab](https://github.com/JeremyLikness/azure-fn-file-process-hol).</span></span>

## <a name="shorten-links-and-track-metrics"></a><span data-ttu-id="427cd-156">Сокращение ссылок и контроль метрик</span><span class="sxs-lookup"><span data-stu-id="427cd-156">Shorten links and track metrics</span></span>

<span data-ttu-id="427cd-157">Средства сокращения ссылок, первоначально посвященные кодированию URL-адресов в коротких записях Twitter, чтобы обеспечить ограничение в 140 символов.</span><span class="sxs-lookup"><span data-stu-id="427cd-157">Link shortening tools originally helped encode URLs in short twitter posts to accommodate the 140 character limit.</span></span> <span data-ttu-id="427cd-158">Они выросли несколько способов использования, чаще всего отслеживание переходов по щелчку для аналитики.</span><span class="sxs-lookup"><span data-stu-id="427cd-158">They've grown to encompass several uses, most commonly to track click-throughs for analytics.</span></span> <span data-ttu-id="427cd-159">Сценарий сокращения ссылок — это полностью бессерверное приложение, которое управляет связями и отчетами.</span><span class="sxs-lookup"><span data-stu-id="427cd-159">The link shortener scenario is an entirely serverless application that manages links and reports metrics.</span></span>

<span data-ttu-id="427cd-160">Функции Azure используются для обслуживания одностраничных приложений (SPA), которые позволяют вставлять длинные URL-адреса и создавать короткие URL-адреса.</span><span class="sxs-lookup"><span data-stu-id="427cd-160">Azure Functions is used to serve a Single Page Application (SPA) that allows you to paste the long URL and generate short URLs.</span></span> <span data-ttu-id="427cd-161">URL-адреса помечаются для записи таких объектов, как кампании (разделы) и средние (например, социальные сети, в которые публикуются ссылки).</span><span class="sxs-lookup"><span data-stu-id="427cd-161">The URLs are tagged to track things like campaigns (topics) and mediums (such as social networks that the links are posted to).</span></span> <span data-ttu-id="427cd-162">Короткий код хранится в хранилище таблиц Azure в качестве ключа с длинным URL-адресом в качестве значения.</span><span class="sxs-lookup"><span data-stu-id="427cd-162">The short code is stored in Azure Table Storage as the key, with the long URL as the value.</span></span> <span data-ttu-id="427cd-163">При щелчке короткой ссылки другая функция ищет длинный URL-адрес, отправляет перенаправление и помещает сведения о событии в очередь.</span><span class="sxs-lookup"><span data-stu-id="427cd-163">When you click on the short link, another function looks up the long URL, sends a redirect, and places information about the event on a queue.</span></span> <span data-ttu-id="427cd-164">Другая функция Azure обрабатывает очередь и помещает сведения в Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="427cd-164">Another Azure Function processes the queue and places the information into Azure Cosmos DB.</span></span>

![Архитектура сокращения ссылок](./media/link-shortener-architecture.png)

<span data-ttu-id="427cd-166">Затем можно создать Power BIную панель мониторинга для сбора сведений о собираемых данных.</span><span class="sxs-lookup"><span data-stu-id="427cd-166">You can then create a Power BI dashboard to gather insights about the data collected.</span></span> <span data-ttu-id="427cd-167">В серверной части Application Insights предоставляет важные метрики.</span><span class="sxs-lookup"><span data-stu-id="427cd-167">On the back end, Application Insights provides important metrics.</span></span> <span data-ttu-id="427cd-168">Данные телеметрии включают время, затрачиваемое средним числом пользователей для перенаправления, а также время, затрачиваемое на доступ к хранилищу таблиц Azure.</span><span class="sxs-lookup"><span data-stu-id="427cd-168">Telemetry includes how long it takes for the average user to redirect and how long it takes to access Azure Table Storage.</span></span>

![Пример Power BI](./media/power-bi-example.png)

<span data-ttu-id="427cd-170">Полный репозиторий сокращения ссылок с инструкциями можно найти здесь: [Несерверный URL-адрес](https://github.com/jeremylikness/serverless-url-shortener).</span><span class="sxs-lookup"><span data-stu-id="427cd-170">The full link shortener repository with instructions is available here: [Serverless URL shortener](https://github.com/jeremylikness/serverless-url-shortener).</span></span> <span data-ttu-id="427cd-171">Более простую версию можно прочитать здесь: Служба [хранилища Azure для безсерверных приложений .NET за считаные минуты](https://blogs.msdn.microsoft.com/webdev/2018/01/25/azure-storage-for-serverless-net-apps-in-minutes/).</span><span class="sxs-lookup"><span data-stu-id="427cd-171">You can read about a simplified version here: [Azure Storage for serverless .NET apps in minutes](https://blogs.msdn.microsoft.com/webdev/2018/01/25/azure-storage-for-serverless-net-apps-in-minutes/).</span></span>

## <a name="verify-device-connectivity-using-a-ping"></a><span data-ttu-id="427cd-172">Проверка подключения устройства с помощью проверки связи</span><span class="sxs-lookup"><span data-stu-id="427cd-172">Verify device connectivity using a ping</span></span>

<span data-ttu-id="427cd-173">Пример состоит из центра Интернета вещей Azure и функции Azure.</span><span class="sxs-lookup"><span data-stu-id="427cd-173">The sample consists of an Azure IoT Hub and an Azure Function.</span></span> <span data-ttu-id="427cd-174">Новое сообщение в центре Интернета вещей активирует функцию Azure.</span><span class="sxs-lookup"><span data-stu-id="427cd-174">A new message on the IoT Hub triggers the Azure Function.</span></span> <span data-ttu-id="427cd-175">Несерверный код отправляет одинаковое содержимое сообщения обратно на устройство, которое его отправило.</span><span class="sxs-lookup"><span data-stu-id="427cd-175">The serverless code sends the same message content back to the device that sent it.</span></span> <span data-ttu-id="427cd-176">Проект содержит весь код и конфигурацию развертывания, необходимые для решения.</span><span class="sxs-lookup"><span data-stu-id="427cd-176">The project has all the code and deployment configuration needed for the solution.</span></span>

<span data-ttu-id="427cd-177">Дополнительные сведения см. в статье [Проверка связи с центром Интернета вещей Azure](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/).</span><span class="sxs-lookup"><span data-stu-id="427cd-177">For more information, see [Azure IoT Hub ping](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/).</span></span>

## <a name="recommended-resources"></a><span data-ttu-id="427cd-178">Рекомендуемые ресурсы</span><span class="sxs-lookup"><span data-stu-id="427cd-178">Recommended resources</span></span>

* [<span data-ttu-id="427cd-179">Генератор фотомозаики по функциям Azure</span><span class="sxs-lookup"><span data-stu-id="427cd-179">Azure Functions photo mosaic generator</span></span>](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/)
* [<span data-ttu-id="427cd-180">Проверка связи с центром Интернета вещей Azure</span><span class="sxs-lookup"><span data-stu-id="427cd-180">Azure IoT Hub ping</span></span>](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/)
* [<span data-ttu-id="427cd-181">Хранилище Azure для безсерверных приложений .NET за считаные минуты</span><span class="sxs-lookup"><span data-stu-id="427cd-181">Azure Storage for serverless .NET apps in minutes</span></span>](https://blogs.msdn.microsoft.com/webdev/2018/01/25/azure-storage-for-serverless-net-apps-in-minutes/)
* [<span data-ttu-id="427cd-182">Перенесите свое приложение</span><span class="sxs-lookup"><span data-stu-id="427cd-182">Bring your own app</span></span>](https://github.com/JeremyLikness/bring-own-app-connect-17)
* [<span data-ttu-id="427cd-183">Лаборатория импорта CSV</span><span class="sxs-lookup"><span data-stu-id="427cd-183">CSV import lab</span></span>](https://github.com/JeremyLikness/azure-fn-file-process-hol)
* [<span data-ttu-id="427cd-184">Приклеивание сетки событий</span><span class="sxs-lookup"><span data-stu-id="427cd-184">Event grid glue</span></span>](https://github.com/JeremyLikness/Event-Grid-Glue)
* [<span data-ttu-id="427cd-185">Реализация простой функции Azure с помощью клиента Xamarin. Forms</span><span class="sxs-lookup"><span data-stu-id="427cd-185">Implementing a simple Azure Function with a Xamarin.Forms client</span></span>](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)
* [<span data-ttu-id="427cd-186">Прогнозирование и сдвиг с помощью безсерверных функций Azure</span><span class="sxs-lookup"><span data-stu-id="427cd-186">Lift and shift with serverless Azure functions</span></span>](https://channel9.msdn.com/Events/Connect/2017/E102)
* [<span data-ttu-id="427cd-187">Несерверный URL-адрес</span><span class="sxs-lookup"><span data-stu-id="427cd-187">Serverless URL shortener</span></span>](https://github.com/jeremylikness/serverless-url-shortener)

>[!div class="step-by-step"]
><span data-ttu-id="427cd-188">[Назад](orchestration-patterns.md)
>[Вперед](serverless-conclusion.md)</span><span class="sxs-lookup"><span data-stu-id="427cd-188">[Previous](orchestration-patterns.md)
[Next](serverless-conclusion.md)</span></span>
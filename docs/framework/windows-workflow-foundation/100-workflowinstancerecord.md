---
title: 100 ― WorkflowInstanceRecord
ms.date: 03/30/2017
ms.assetid: ed4d1851-b378-489b-a22d-c1db09571fb4
ms.openlocfilehash: c0780aa21e76eb0d72f83b5d2de7d16ff84a6ac7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96240047"
---
# <a name="100---workflowinstancerecord"></a>100 ― WorkflowInstanceRecord

## <a name="properties"></a>Свойства  
  
|||  
|-|-|  
|Идентификатор|100|  
|Keywords|EndToEndMonitoring, Troubleshooting, HealthMonitoring, WFTracking|  
|Level|Сведения|  
|Канал|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Описание  

 Это событие формируется участником отслеживания ETW, когда экземпляр рабочего процесса формирует запись WorkflowInstanceRecord для следующих состояний рабочего процесса: «Started», «Resumed», «Persisted», «Idle», «Deleted», «Completed», «Canceled», «Unloaded», «Unsuspended».  
  
## <a name="message"></a>Сообщение  

 TrackRecord=WorkflowInstanceRecord, InstanceId=%1, RecordNumber=%2, EventTime=%3, ActivityDefinitionId=%4, State=%5, Annotations=%6, ProfileName=%7  
  
## <a name="details"></a>Сведения  
  
|Имя элемента данных|Тип элемента данных|Описание|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|Идентификатор экземпляра для рабочего процесса.|  
|RecordNumber|xs:long|Порядковый номер созданной записи.|  
|EventTime|xs:dateTime|Время в формате UTC, когда было создано событие.|  
|ActivityDefinitionId|xs:string|Имя корневого действия в рабочем процессе.|  
|Состояние|xs:string|Текущее состояние рабочего процесса.|  
|Заметки|xs:string|Заметки, добавленные к этому событию.  Значения хранятся в XML-элементе в формате \<items> \< item  name = "annotationName" type="System.String"> аннотатионвалуе \</item> \</items> .  Если заметки не указаны, строка содержит \<items/> . Размер событий ETW ограничен размером буфера ETW или максимальным размером полезных данных для события ETW. Если размер события превышает предел ETW, то событие усекается путем удаления заметок и замены значения аннотации на \<items> ... \</items> .|  
|ProfileName|xs:string|Имя или профиль отслеживания, который привел к созданию этого события.|  
|HostReference|xs:string|Для служб, размещенных на веб-сайтах, это поле служит уникальным идентификатором службы в веб-иерархии.  Его формат определяется как "имя веб-сайта виртуальный путь к приложению&#124;виртуальный путь службы&#124;ServiceName" example: "Default Web site/Калкулатораппликатион&#124;/Калкулаторсервице.СВК&#124;CalculatorService"|  
|Домен приложения|xs:string|Строка, возвращаемая AppDomain.CurrentDomain.FriendlyName.|

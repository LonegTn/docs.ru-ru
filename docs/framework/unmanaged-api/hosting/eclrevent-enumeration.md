---
title: Перечисление EClrEvent
ms.date: 03/30/2017
api_name:
- EClrEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrEvent
helpviewer_keywords:
- EClrEvent enumeration [.NET Framework hosting]
ms.assetid: 7c36a7c2-75a2-4971-bc23-abf54c812154
topic_type:
- apiref
ms.openlocfilehash: 5d6ec42da60a7b294177063b9f8bd5afbf352c62
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726825"
---
# <a name="eclrevent-enumeration"></a>Перечисление EClrEvent

Описывает события среды CLR, для которых узел может регистрировать обратные вызовы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a>Члены  
  
|Член|Описание|  
|------------|-----------------|  
|`Event_ClrDisabled`|Указывает неустранимую ошибку среды CLR.|  
|`Event_DomainUnload`|Задает выгрузку конкретного объекта <xref:System.AppDomain> .|  
|`Event_MDAFired`|Указывает, что создано сообщение помощника по отладке управляемого кода (MDA).|  
|`Event_StackOverflow`|Указывает, что произошла ошибка переполнения стека.|  
  
## <a name="remarks"></a>Комментарии  

 Узел может регистрировать обратные вызовы для любого из типов событий, описанных путем `EClrEvent` вызова методов интерфейса [ICLROnEventManager](iclroneventmanager-interface.md) . Узел получает указатель на этот интерфейс путем вызова метода [ICLRControl:: GetCLRManager](iclrcontrol-getclrmanager-method.md) .  
  
 `Event_CLRDisabled`События и `Event_DomainUnload` могут вызываться более одного раза и из разных потоков для сигнализации выгрузки или отключения среды CLR.  
  
 `Event_MDAFired`Событие вызывает создание экземпляра [мдаинфо](mdainfo-structure.md) , содержащего подробные сведения о сообщении MDA. Дополнительные сведения о помощниках MDA см. в разделе [Диагностика ошибок с помощью помощников по отладке управляемого](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)кода.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** MSCorEE. h  
  
 **Библиотека:** MSCorEE.dll  
  
 **.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс IActionOnCLREvent](iactiononclrevent-interface.md)
- [Интерфейс ICLRControl](iclrcontrol-interface.md)
- [Размещение перечислений](hosting-enumerations.md)

---
title: Метод ICorDebugManagedCallback::LogSwitch
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogSwitch
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogSwitch
helpviewer_keywords:
- LogSwitch method [.NET Framework debugging]
- ICorDebugManagedCallback::LogSwitch method [.NET Framework debugging]
ms.assetid: 0ac59d27-783f-4a87-b7a8-baa3ccc54582
topic_type:
- apiref
ms.openlocfilehash: db6ccd63bbeadd7dcff1c7f8491b59017d431d12
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720702"
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a>Метод ICorDebugManagedCallback::LogSwitch

Уведомляет отладчик о том, что управляемый поток среды CLR вызвал метод в <xref:System.Diagnostics.Switch> классе для создания, изменения или удаления переключателя отладки или трассировки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
## <a name="parameters"></a>Параметры  

 `PAppDomain`  
 окне Указатель на объект ICorDebugAppDomain, представляющий домен приложения, содержащий управляемый поток, который создал, изменил или удалил параметр отладки/трассировки.  
  
 `pThread`  
 окне Указатель на объект ICorDebugThread, представляющий управляемый поток.  
  
 `lLevel`  
 окне Значение, указывающее степень серьезности описательного сообщения, записанного в журнал событий.  
  
 `ulReason`  
 окне Значение перечисления [логсвитчкаллреасон](logswitchcallreason-enumeration.md) , указывающее операцию, выполняемую с переключателем "Отладка/трассировка".  
  
 `pLogSwitchName`  
 окне Указатель на имя переключателя отладки/трассировки.  
  
 `pParentName`  
 окне Указатель на имя родителя переключателя "Отладка/трассировка".  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorDebugManagedCallback](icordebugmanagedcallback-interface.md)

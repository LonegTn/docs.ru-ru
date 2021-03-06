---
title: Метод ICorDebugModule::EnableJITDebugging
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableJITDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableJITDebugging
helpviewer_keywords:
- ICorDebugModule::EnableJITDebugging method [.NET Framework debugging]
- EnableJITDebugging method [.NET Framework debugging]
ms.assetid: 0a65e2a4-5bb6-496c-ae6f-40474426b5a6
topic_type:
- apiref
ms.openlocfilehash: 359db27878ea4adf794bcd6221d4b5387026e5c0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710315"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a>Метод ICorDebugModule::EnableJITDebugging

Определяет, сохраняет ли JIT-компилятор сведения об отладке для методов в этом модуле.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a>Параметры  

 `bTrackJITInfo`  
 окне Установите это значение, чтобы `true` разрешить JIT-компилятору сохранять сведения о сопоставлении между версией MSIL и версией каждого метода в этом модуле, скомпилированном по требованию.  
  
 `bAllowJitOpts`  
 окне Установите это значение, чтобы `true` разрешить JIT-компилятору создавать код с определенными оптимизацией JIT для отладки.  
  
## <a name="remarks"></a>Комментарии  

 JIT-отладка включается по умолчанию для всех модулей, загружаемых при активном отладчике. Программное включение или отключение параметров переопределяет глобальные параметры.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

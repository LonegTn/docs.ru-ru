---
title: Метод ICorProfilerCallback::JITCachedFunctionSearchFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchFinished
helpviewer_keywords:
- JITCachedFunctionSearchFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchFinished method [.NET Framework profiling]
ms.assetid: 3c325c82-cddd-4b00-b3da-e450c36abf62
topic_type:
- apiref
ms.openlocfilehash: fe07270989df897c3dbf689305784f9f0af65742
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684048"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a>Метод ICorProfilerCallback::JITCachedFunctionSearchFinished

Уведомляет профилировщик о завершении поиска для функции, которая была скомпилирована ранее с помощью генератора образов в машинном кодах (NGen.exe).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
## <a name="parameters"></a>Параметры

- `functionId`

  \[in] идентификатор функции, для которой был выполнен поиск.

- `result`

  \[в] значение перечисления [COR_PRF_JIT_CACHE](cor-prf-jit-cache-enumeration.md) , указывающее результат поиска.

## <a name="remarks"></a>Комментарии  

 В .NET Framework версии 2,0 функции [ICorProfilerCallback:: JITCachedFunctionSearchStarted](icorprofilercallback-jitcachedfunctionsearchstarted-method.md) и `JITCachedFunctionSearchFinished` обратные вызовы не будут выполняться для всех функций в обычных образах Ngen. Только образы NGen, оптимизированные для профилировщика, будут создавать обратные вызовы для всех функций в образе. Однако из-за дополнительных издержек профилировщик должен запросить оптимизированные профилировщиком генераторы NGen только в том случае, если планируется использовать эти обратные вызовы для принудительной компиляции функции JIT (JIT). В противном случае профилировщик должен использовать отложенную стратегию для сбора сведений о функции.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorProfilerCallback](icorprofilercallback-interface.md)

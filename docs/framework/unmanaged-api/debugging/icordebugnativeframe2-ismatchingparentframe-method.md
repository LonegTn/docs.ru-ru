---
title: Метод ICorDebugNativeFrame2::IsMatchingParentFrame
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.IsMatchingParentFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::IsMatchingParentFrame
helpviewer_keywords:
- IsMatchingParentFrame method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsMatchingParentFrame method [.NET Framework debugging]
ms.assetid: d2ca20db-df22-4528-a0dd-a09ea62c8998
topic_type:
- apiref
ms.openlocfilehash: 213bee96531fa0bbc9bf0ae76b2505019833abfc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724706"
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a>Метод ICorDebugNativeFrame2::IsMatchingParentFrame

Определяет, является ли указанный кадр родительским по отношению к текущему кадру.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
## <a name="parameters"></a>Параметры  

 `pPotentialParentFrame`  
 окне Указатель на объект Frame, для которого необходимо оценить состояние родителя.  
  
 `pIsParent`  
 [out] `true` `pPotentialParentFrame` , если является родительским для текущего кадра; в противном случае — значение `false` .  
  
## <a name="return-value"></a>Возвращаемое значение  

 Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.  
  
|HRESULT|Описание:|  
|-------------|-----------------|  
|S_OK|Состояние родительского объекта успешно возвращено.|  
|E_FAIL|Не удалось вернуть родительское состояние.|  
|E_INVALIDARG|`pPotentialParentFrame` или `pIsParent` равно null.|  
  
## <a name="exceptions"></a>Исключения  
  
## <a name="remarks"></a>Remarks  

 `IsMatchingParentFrame` Возвращает значение, `true` Если объект Frame, передаваемый в метод, является родительским для объекта Frame, для которого был вызван метод. При вызове метода для фрейма, который не является дочерним по отношению к указанному кадру, возвращается ошибка.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **.NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorDebugNativeFrame2](icordebugnativeframe2-interface.md)
- [Интерфейсы отладки](debugging-interfaces.md)
- [Отладка](index.md)

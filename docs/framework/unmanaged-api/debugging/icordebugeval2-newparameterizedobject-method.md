---
title: Метод ICorDebugEval2::NewParameterizedObject
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObject
helpviewer_keywords:
- NewParameterizedObject method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObject method [.NET Framework debugging]
ms.assetid: 3d705463-e640-4249-8036-4e8206d03cfe
topic_type:
- apiref
ms.openlocfilehash: 8c91296bd4185fd98962d49f611a3cdcb5f0ad28
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729668"
---
# <a name="icordebugeval2newparameterizedobject-method"></a>Метод ICorDebugEval2::NewParameterizedObject

Создает новый объект параметризованного типа и вызывает метод конструктора объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT NewParameterizedObject (  
    [in] ICorDebugFunction     *pConstructor,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a>Параметры  

 `pConstructor`  
 окне Указатель на объект ICorDebugFunction, представляющий конструктор объекта, для которого создается экземпляр.  
  
 `nTypeArgs`  
 окне Число переданных аргументов типа.  
  
 `ppTypeArgs`  
 окне Массив указателей, каждый из которых указывает на объект ICorDebugType, представляющий аргумент типа для объекта, для которого создается экземпляр.  
  
 `nArgs`  
 окне Число аргументов, переданных конструктору.  
  
 `ppArgs`  
 окне Массив указателей, каждый из которых указывает на объект ICorDebugValue, представляющий значение аргумента, передаваемое конструктору.  
  
## <a name="remarks"></a>Комментарии  

 Конструктор объекта может принимать <xref:System.Type> Параметры.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

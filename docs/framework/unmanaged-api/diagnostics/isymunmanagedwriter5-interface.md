---
title: Интерфейс ISymUnmanagedWriter5
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
ms.openlocfilehash: 894f3b0e45df2c681cbdec1f154703be64f32fc5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725798"
---
# <a name="isymunmanagedwriter5-interface"></a>Интерфейс ISymUnmanagedWriter5

Интерфейс ISymUnmanagedWriter5.  
  
## <a name="syntax"></a>Синтаксис  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a>Методы  

 Этот интерфейс содержит следующие методы:  
  
|Метод|Описание|  
|------------|-----------------|  
|[Метод CloseMapTokensToSourceSpans](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|Закройте Специальный раздел настраиваемых данных, чтобы получить сведения о сопоставлении диапазона "токен-источник". После закрытия не удается добавить дополнительные сведения о сопоставлении.|  
|[Метод MapTokenToSourceSpan](isymunmanagedwriter5-maptokentosourcespan-method.md)|Сопоставляет заданный токен метаданных с заданным диапазоном исходной строки в указанном исходном файле.<br /><br /> Должен вызываться между вызовами [метода OpenMapTokensToSourceSpans](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) и [метода CloseMapTokensToSourceSpans](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).|  
|[Метод OpenMapTokensToSourceSpans](isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|Откройте Специальный раздел настраиваемых данных, чтобы выдать сведения о сопоставлении диапазона от токена к источнику в. Открытие этого раздела, если метод уже открыт или наоборот, является ошибкой.|  
  
## <a name="requirements"></a>Требования  

 **Заголовок:** Корсим. idl, Корсим. h  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейсы хранилища символов диагностики](diagnostics-symbol-store-interfaces.md)
- [Интерфейс ISymUnmanagedWriter4](isymunmanagedwriter4-interface.md)

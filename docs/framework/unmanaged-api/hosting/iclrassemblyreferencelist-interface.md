---
title: Интерфейс ICLRAssemblyReferenceList
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList
helpviewer_keywords:
- ICLRAssemblyReferenceList interface [.NET Framework hosting]
ms.assetid: 5f890fdf-d22a-429e-a35f-135273d1a636
topic_type:
- apiref
ms.openlocfilehash: a75235cd0ac0e55412f0ba58881796e3ebc801f1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679244"
---
# <a name="iclrassemblyreferencelist-interface"></a>Интерфейс ICLRAssemblyReferenceList

Управляет списком сборок, загружаемых средой CLR, а не узлом.  
  
## <a name="methods"></a>Методы  
  
|Метод|Описание|  
|------------|-----------------|  
|[Метод IsAssemblyReferenceInList](iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|Возвращает значение, указывающее, ссылается ли указанный указатель на сборку в списке.|  
|[Метод IsStringAssemblyReferenceInList](iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|Возвращает значение, указывающее, совпадает ли заданное имя с именем сборки в списке.|  
  
## <a name="remarks"></a>Комментарии  

 Вызовите метод [ICLRAssemblyIdentityManager:: getclrassemblyreferencelist-](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) , чтобы получить указатель на экземпляр `ICLRAssemblyReferenceList` .  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** MSCorEE. h  
  
 **Библиотека:** Включается в качестве ресурса в MSCorEE.dll  
  
 **.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс ICLRAssemblyIdentityManager](iclrassemblyidentitymanager-interface.md)
- [Интерфейс IHostAssemblyStore](ihostassemblystore-interface.md)
- [Интерфейсы размещения](hosting-interfaces.md)

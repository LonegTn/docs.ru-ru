---
title: Интерфейс IMetaDataAssemblyEmit
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit
helpviewer_keywords:
- IMetaDataAssemblyEmit interface [.NET Framework metadata]
ms.assetid: 34fb03cc-2285-4a45-ac48-ad993b7a921a
topic_type:
- apiref
ms.openlocfilehash: 5d8bc54a94e1571ff8335c934407bbf235179ecc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728294"
---
# <a name="imetadataassemblyemit-interface"></a>Интерфейс IMetaDataAssemblyEmit

Предоставляет методы, поддерживающие модель самоописания, которая используется средой CLR для разрешения и потребления ресурсов.  
  
## <a name="methods"></a>Методы  
  
|Метод|Описание|  
|------------|-----------------|  
|[Метод DefineAssembly](imetadataassemblyemit-defineassembly-method.md)|Создает структуру данных сборки, содержащую метаданные для заданной сборки, и возвращает связанный токен метаданных.|  
|[Метод DefineAssemblyRef](imetadataassemblyemit-defineassemblyref-method.md)|Создает структуру `AssemblyRef`, содержащую метаданные для сборки, на которую ссылается данная сборка, и возвращает связанный токен метаданных.|  
|[Метод DefineExportedType](imetadataassemblyemit-defineexportedtype-method.md)|Создает структуру `ExportedType`, содержащую метаданные для указанного экспортированного типа, и возвращает связанный токен метаданных.|  
|[Метод DefineFile](imetadataassemblyemit-definefile-method.md)|Создает структуру метаданных `File`, содержащую метаданные для сборки, на которую ссылается данная сборка, и возвращает связанный токен метаданных.|  
|[Метод DefineManifestResource](imetadataassemblyemit-definemanifestresource-method.md)|Создает структуру `ManifestResource`, содержащую метаданные для указанного ресурса манифеста, и возвращает связанный токен метаданных.|  
|[Метод SetAssemblyProps](imetadataassemblyemit-setassemblyprops-method.md)|Изменяет указанную структуру метаданных `Assembly`.|  
|[Метод SetAssemblyRefProps](imetadataassemblyemit-setassemblyrefprops-method.md)|Изменяет указанную структуру метаданных `AssemblyRef`.|  
|[Метод SetExportedTypeProps](imetadataassemblyemit-setexportedtypeprops-method.md)|Изменяет указанную структуру метаданных `ExportedType`.|  
|[Метод SetFileProps](imetadataassemblyemit-setfileprops-method.md)|Изменяет указанную структуру метаданных `File`.|  
|[Метод SetManifestResourceProps](imetadataassemblyemit-setmanifestresourceprops-method.md)|Изменяет указанную структуру метаданных `ManifestResource`.|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** COR. h  
  
 **Библиотека:** Используется в качестве ресурса в MsCorEE.dll  
  
 **.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейсы метаданных](metadata-interfaces.md)
- [Интерфейс IMetaDataAssemblyImport](imetadataassemblyimport-interface.md)

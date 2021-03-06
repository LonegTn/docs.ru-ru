---
title: Метод ISymUnmanagedBinder2::GetReaderForFile2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2.GetReaderForFile2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2
helpviewer_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2 method [.NET Framework debugging]
- GetReaderForFile2 method [.NET Framework debugging]
ms.assetid: dd92dcaf-403c-464d-a254-21594985dddd
topic_type:
- apiref
ms.openlocfilehash: e0fc6cf2a08de4a00cb8b7f98d3922df98f427c5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706974"
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a>Метод ISymUnmanagedBinder2::GetReaderForFile2

При наличии интерфейса метаданных и имени файла возвращает правильный интерфейс [ISymUnmanagedReader](isymunmanagedreader-interface.md) , который будет считывать символы отладки, связанные с модулем.  
  
 Этот метод обеспечивает более широкий поиск файла базы данных программы (PDB), чем метод [ISymUnmanagedBinder:: getreaderforfile:](isymunmanagedbinder-getreaderforfile-method.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a>Параметры  

 `importer`  
 окне Указатель на интерфейс импорта метаданных.  
  
 `fileName`  
 окне Указатель на имя файла.  
  
 `searchPath`  
 окне Указатель на путь поиска.  
  
 `searchPolicy`  
 окне Значение перечисления [корсимсеарчполициаттрибутес](corsymsearchpolicyattributes-enumeration.md) , указывающее политику, используемую при поиске средства чтения символов.  
  
 `pRetVal`  
 заполняет Указатель, которому присваивается возвращаемый интерфейс [ISymUnmanagedReader](isymunmanagedreader-interface.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  

 S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.  
  
## <a name="requirements"></a>Требования  

 **Заголовок:** Корсим. idl, Корсим. h  
  
## <a name="remarks"></a>Комментарии  

 Эта версия метода может искать PDB-файл в областях, отличных от right рядом с модулем. Политику поиска можно контролировать путем объединения [корсимсеарчполициаттрибутес](corsymsearchpolicyattributes-enumeration.md). Например, `AllowReferencePathAccess | AllowSymbolServerAccess` выполняет поиск PDB-файла рядом с исполняемым файлом и на сервере символов, но не запрашивает реестр или не использует путь в исполняемом файле. Если `searchPath` указан параметр, то поиск в этих каталогах будет выполняться всегда.  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс ISymUnmanagedBinder2](isymunmanagedbinder2-interface.md)
- [Метод GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md)

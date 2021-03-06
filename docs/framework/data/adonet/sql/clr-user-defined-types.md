---
title: Определяемые пользователем типы данных CLR
ms.date: 03/30/2017
ms.assetid: 9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2
ms.openlocfilehash: 84d588e0c415daa7de19ea695c817f3eb24f732f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173592"
---
# <a name="clr-user-defined-types"></a>Определяемые пользователем типы данных CLR

Microsoft SQL Server предоставляет поддержку определяемых пользователем типов данных (UDT), реализованную при помощи среды CLR в Microsoft .NET Framework. Среда CLR встроена в SQL Server. Этот механизм позволяет расширять систему типов базы данных. Определяемые пользователем типы дают возможность расширять систему типов данных SQL Server, а также позволяют определять сложные структурированные типы.  
  
 Для архитектуры приложений использование определяемых пользователем типов имеет два основных преимущества.  
  
- Строгая инкапсуляция (и на клиенте, и на сервере) между внутренним состоянием и внешней функциональностью.  
  
- Тесная интеграция между другими связанными возможностями сервера. После определения собственного типа данных его можно использовать во всех контекстах, где в SQL Server можно использовать системные типы, включая определения столбцов, а также в качестве переменных, параметров, результатов функций, курсоров, триггеров и репликации.  
  
 Дополнительные сведения см. в документации по [SQL Server](/sql) версии SQL Server, которую вы используете.
  
 **Документация по SQL Server**
  
1. [Определяемые пользователем типы CLR](/sql/relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types)  
  
## <a name="see-also"></a>См. также раздел

- [Общие сведения об ADO.NET](../ado-net-overview.md)

---
title: Параметр кодировки экземпляров
ms.date: 03/30/2017
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
ms.openlocfilehash: c4de7c45d899f45a7b5b71d563257d9accb8fdbb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61928724"
---
# <a name="instance-encoding-option"></a>Параметр кодировки экземпляров
**Instance Encoding Option** Store экземпляра рабочего процесса SQL позволяет указать, должен ли поставщик сохраняемости SQL сжимать сведения о состоянии экземпляра рабочего процесса, с помощью алгоритма GZip перед сохранением сведения в базе данных сохраняемости. Ниже приведены допустимые значения для этого свойства. GZip и None. По умолчанию используется значение None. Эти варианты описаны в следующем списке.  
  
1. **GZip**. Поставщик сохраняемости кодирует сведения о состоянии с использованием алгоритма сжатия GZip перед их сохранением в базе данных сохраняемости.  
  
2. **Нет**. Поставщик сохраняемости не сжимает сведения о состоянии перед их сохранением в базе данных сохраняемости.  
  
 При кодировании и сжатии сведений о состоянии экземпляра рабочего процесса с использованием экземпляра GZip снижается потребление памяти базой данных SQL, а также снижается нагрузка на сеть (в случае если база данных расположена на другом компьютере в сети, а не на компьютере, на котором запущена служба рабочего процесса). Общая рекомендация заключается в задании **Instance Encoding Option** свойства **None** при небольших состояния экземпляра рабочего процесса.

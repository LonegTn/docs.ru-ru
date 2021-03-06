---
title: Отображение идентификаторов объектов на криптографические алгоритмы
description: См. раздел как сопоставлять идентификатор объекта (OID) с алгоритмом шифрования в .NET с помощью элементов Оидентри и элементе nameentry в XML-файле конфигурации.
ms.date: 03/30/2017
helpviewer_keywords:
- digital signatures
- identifiers, mapping object identifiers
- cryptographic algorithms
- mapping object identifiers
- cryptography, mapping object identifiers
ms.assetid: c9673f81-bf9e-47fd-bc6f-6bc1c1c4c15e
ms.openlocfilehash: 5416ddbb766dfde56fa28a3853ed448cc73f25a2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189387"
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a>Отображение идентификаторов объектов на криптографические алгоритмы

Цифровые подписи гарантируют, что данные не были изменены при отправке из одной программы в другую. Обычно цифровая подпись вычислена путем применения математической функции к хэшу подписываемых данных. При форматировании хэш-значения для подписи некоторые алгоритмы цифровых подписей добавляют в операцию форматирования идентификатор объекта ASN. 1 (OID). OID определяет алгоритм, который использовался для вычисления хэша. Вы можете сопоставлять алгоритмы с идентификаторами объектов, чтобы расширить механизм криптографии для использования пользовательских алгоритмов. В следующем примере показано, как сопоставлять идентификатор объекта с новым алгоритмом хэширования.  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MyNewHash="MyNewHashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="NewHash" class="MyNewHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.14.33.42.46"  name="NewHash"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 [ \<oidEntry> Элемент](./file-schema/cryptography/oidentry-element.md) содержит два атрибута. Атрибут **OID** — это номер идентификатора объекта. Атрибут **Name** — это значение атрибута **Name** из [ \<nameEntry> элемента](./file-schema/cryptography/nameentry-element.md). Необходимо сопоставить имя алгоритма с классом, чтобы идентификатор объекта можно было сопоставить с простым именем.  
  
## <a name="see-also"></a>См. также раздел

- [Настройка криптографических классов](configure-cryptography-classes.md)
- [службы шифрования](../../standard/security/cryptographic-services.md)

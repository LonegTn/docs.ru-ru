---
title: Тип члена <membername> не является CLS-совместимым
ms.date: 07/20/2015
f1_keywords:
- bc40025
- vbc40025
helpviewer_keywords:
- BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
ms.openlocfilehash: c8c14a2d6df8804967807af881384bc7d9ccd99f
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163484"
---
# <a name="bc40025-type-of-member-membername-is-not-cls-compliant"></a>BC40025: тип члена "" несовместим с \<membername> CLS

Тип данных, заданный для этого элемента, не входит в [независимость от языка и Language-Independent компоненты](../../../standard/language-independence-and-language-independent-components.md) (CLS). Это не ошибка в компоненте, так как .NET Framework и Visual Basic поддерживают этот тип данных. Однако другой компонент, написанный в строго CLS-совместимом коде, может не поддерживать этот тип данных. Такой компонент, возможно, не сможет успешно взаимодействовать с компонентом.

 Следующие типы данных Visual Basic несовместимы с CLS:

- [Тип данных SByte](../data-types/sbyte-data-type.md)

- [Тип данных UInteger](../data-types/uinteger-data-type.md)

- [Тип данных ULong](../data-types/ulong-data-type.md)

- [Тип данных UShort](../data-types/ushort-data-type.md)

 По умолчанию данное сообщение является предупреждением. Дополнительные сведения о скрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).

 **Идентификатор ошибки:** BC40025

## <a name="to-correct-this-error"></a>Исправление ошибки

- Если компонент работает только с другими компонентами .NET Framework или не взаимодействует с другими компонентами, изменять ничего не нужно.

- Если вы взаимодействуете с компонентом, не написанным для .NET Framework, вы можете определить, поддерживает ли этот тип данных либо с помощью отражения, либо из документации. Если это так, вам не нужно ничего менять.

- При взаимоработе с компонентом, который не поддерживает этот тип данных, необходимо заменить его ближайшим CLS-совместимым типом. Например, вместо `UInteger` вы можете использовать `Integer` , если вам не нужен диапазон значений, превышающий 2 147 483 647. Если вам нужен расширенный диапазон, вы можете заменить `UInteger` на `Long`.

- При взаимоработе с автоматизацией или COM-объектами Помните, что некоторые типы имеют разную ширину данных, чем в .NET Framework. Например, данные типа `uint` часто являются 16-битными в других средах. При передаче 16-разрядного аргумента в такой компонент объявите его как `UShort` вместо `UInteger` в управляемом коде Visual Basic.

## <a name="see-also"></a>См. также

- [Отражение](../../../framework/reflection-and-codedom/reflection.md)

---
title: Совместимость версий в .NET Framework
description: Узнайте о совместимости между версиями .NET Framework, включая обратную совместимость и параллельное выполнение.
ms.date: 04/02/2019
helpviewer_keywords:
- .NET Framework, version compatibility
- .NET Framework, compatibility with earlier versions
- .NET Framework versions, compatibility
ms.assetid: 2f25e522-456a-48c3-8a53-e5f39275649f
ms.openlocfilehash: 2be9c4e12d6a613e7f1062ec7492b0b99203f39d
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400700"
---
# <a name="version-compatibility"></a>Совместимость версий

Обратная совместимость означает, что приложение, разработанное для конкретной версии платформы, будет запускаться и в более поздних версиях этой платформы. На платформе .NET Framework в максимально возможной степени обеспечивается обратная совместимость: исходный код, написанный для одной версии платформы .NET Framework, должен компилироваться в более поздних версиях этой платформы, а двоичные файлы, работающие в одной версии платформы .NET Framework, должны точно так же работать в более поздних версиях этой платформы.

## <a name="version-compatibility-for-apps"></a><a name="Apps"></a> Совместимость версий приложений

По умолчанию приложение запускается в той версии платформы .NET Framework, для которой оно было создано. Если эта версия отсутствует и в файле конфигурации приложения не определены поддерживаемые версии, может произойти ошибка инициализации .NET Framework. В этом случае попытка запустить приложение завершится сбоем.

Чтобы определить конкретные версии, в которых запускается приложение, добавьте в файл конфигурации этого приложения один или несколько элементов [\<supportedRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md). Каждый элемент `<supportedRuntime>` определяет поддерживаемую версию среды выполнения. При этом первый элемент указывает наиболее предпочтительную версию, а последний элемент — наименее предпочтительную версию.

```xml
<configuration>
   <startup>
      <supportedRuntime version="v2.0.50727" />
      <supportedRuntime version="v4.0" />
   </startup>
</configuration>
```

Дополнительные сведения см. в разделе [Практическое руководство. Настройка приложения для поддержки платформы .NET Framework 4 или 4.x](how-to-configure-an-app-to-support-net-framework-4-or-4-5.md).

## <a name="version-compatibility-for-components"></a>Совместимость версий компонентов

Приложение может определять версию платформы .NET Framework, в которой оно запускается, однако компонент не может. Компоненты и библиотеки классов загружаются в контексте конкретного приложения и, следовательно, автоматически запускаются в той версии .NET Framework, в которой запускается это приложение.

Из-за этого ограничения гарантии совместимости особенно важны для компонентов. Начиная с .NET Framework 4, можно задать, в какой степени компонент должен оставаться совместимым в различных версиях, применив к этому компоненту атрибут <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=nameWithType>. Этот атрибут может использоваться разными средствами для обнаружения возможных нарушений гарантии совместимости в будущих версиях компонента.

## <a name="backward-compatibility"></a>Обратная совместимость

Платформа .NET Framework 4.5 и более поздних версий обратно совместима с приложениями, созданными с помощью более ранних версий .NET Framework. Иными словами, приложения и компоненты, созданные с использованием предыдущих версий платформы .NET Framework, будут без внесения изменений работать в .NET Framework 4.5 и более поздних версий. Однако по умолчанию приложения выполняются в той версии среды CLR, для которой они были разработаны, поэтому, чтобы обеспечить возможность выполнения приложения в .NET Framework 4.5 и более поздних версий, может потребоваться предоставить файл конфигурации. Дополнительные сведения см. в разделе [Совместимость версий для приложений](#Apps) выше.

На практике эту совместимость можно нарушить на первый взгляд несущественными изменениями в платформе .NET Framework и изменениями в методах программирования. Например, улучшения в производительности в платформе .NET Framework 4.5 могут привести к состоянию гонки, которого не было в предыдущих версиях. Следует также иметь в виду, что такие действия, как использование жестко запрограммированного пути к сборкам .NET Framework, сравнение на равенство с конкретной версией платформы .NET Framework и получение значения частного поля с помощью отражения, нарушают обратную совместимость. Кроме того, каждая версия платформы .NET Framework содержит исправления ошибок и изменения, связанные с безопасностью, которые могут влиять на совместимость некоторых приложений и компонентов.

Если приложение или компонент не работает в .NET Framework 4.5 и в доработанных выпусках, .NET Framework 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 или 4.8, ожидаемым образом, воспользуйтесь следующими контрольными списками:

- Если приложение разработано для выполнения в любой версии платформы .NET Framework, начиная с .NET Framework 4.0, см. раздел [Совместимость приложений](application-compatibility.md), чтобы создать списки изменений между вашей целевой версией .NET Framework и версией, в которой выполняется приложение.

- Если приложение предназначено для .NET Framework 3.5, см. также раздел [Проблемы при миграции на .NET Framework 4](net-framework-4-migration-issues.md).

- Если приложение предназначено для .NET Framework 2.0, см. также раздел [Изменения в .NET Framework 3.5 SP1](/previous-versions/dotnet/articles/dd310284(v=msdn.10)).

- Если приложение предназначено для .NET Framework 1.1, см. также раздел [Изменения в .NET Framework 2.0](/previous-versions/aa570326(v=msdn.10)).

- Если вы перекомпилируете существующий исходный код для запуска в платформе .NET Framework 4.5 (или ее доработанных выпусках) или разрабатываете новую версию приложения или компонента для запуска в .NET Framework 4.5 или ее доработанных выпусках на основе существующей базы исходного кода, просмотрите раздел [Что устарело в библиотеке классов](../whats-new/whats-obsolete.md) на предмет устаревших типов и членов и используйте описанный обходной путь. (Скомпилированный ранее код будет продолжать работать с типами и членами, которые отмечены как устаревшие.)

- Если обнаруживается, что изменение в .NET Framework 4.5 нарушило работу приложения, обратитесь к разделу [Схема параметров среды выполнения](../configure-apps/file-schema/runtime/index.md) и, в частности, к подразделу [Элемент \<AppContextSwitchOverrides>](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), чтобы определить, можно ли использовать параметры среды выполнения в файле конфигурации приложения для восстановления предыдущего поведения.

- Если у вас возникла незадокументированная проблема, откройте проблему на [веб-сайте сообщества разработчиков .NET](https://aka.ms/feedback/report?space=61) или в [репозитории GitHub Microsoft/dotnet](https://github.com/microsoft/dotnet/issues).

## <a name="side-by-side-execution"></a>Параллельное выполнение

Если найти подходящий обходной путь для проблемы не удается, помните, что платформа .NET Framework 4.5 (или один из ее доработанных выпусков) работает параллельно с версиями 1.1, 2.0 и 3.5 и представляет собой обновление "на месте", заменяющее версию 4. Для приложений, предназначенных для версий 1.1, 2.0 и 3.5, можно установить на целевом компьютере соответствующую версию .NET Framework и запускать приложение в оптимальной для него среде. Дополнительные сведения о параллельном выполнении см. в разделе [Параллельное выполнение](../deployment/side-by-side-execution.md).

## <a name="see-also"></a>См. также

- [Новые возможности](../whats-new/index.md)
- [Устаревшие классы библиотеки классов](../whats-new/whats-obsolete.md)
- [Совместимость приложений](application-compatibility.md)
- [Официальная политика поддержки .NET Framework](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [Проблемы при миграции на .NET Framework 4](net-framework-4-migration-issues.md)

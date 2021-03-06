---
title: Практическое руководство. Как сопоставить иерархии наследования
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: c0709fde96a5d2f39f04a08ccd24ddf90c782f30
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166421"
---
# <a name="how-to-map-inheritance-hierarchies"></a>Практическое руководство. Как сопоставить иерархии наследования

Чтобы реализовать сопоставление наследования в LINQ, необходимо указать атрибуты и свойства атрибутов в корневом классе иерархии наследования, как описано в следующих шагах. Разработчики, использующие Visual Studio, могут использовать реляционный конструктор объектов для отображения иерархий наследования. См. раздел [как настроить наследование с помощью реляционного конструктора O/R](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).  
  
> [!NOTE]
> Особые атрибуты или свойства подклассов не требуются. Обратите особое внимание на то, что подклассы не имеют атрибута <xref:System.Data.Linq.Mapping.TableAttribute>.  
  
### <a name="to-map-an-inheritance-hierarchy"></a>Сопоставление иерархий наследования  
  
1. Добавьте к корневому классу атрибут <xref:System.Data.Linq.Mapping.TableAttribute>.  
  
2. Кроме того, в корневом классе необходимо добавить атрибут <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> для каждого класса в структуре иерархии.  
  
3. Определите свойство <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> для каждого атрибута <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>.  
  
     Это свойство содержит значение, которое отображается в столбце <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> таблицы базы данных и указывает, к какому классу или подклассу принадлежит эта строка данных.  
  
4. Добавьте также для каждого атрибута <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> свойство <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A>.  
  
     Данное свойство содержит значение, которое указывает, на какой класс или подкласс указывает значение ключа.  
  
5. Добавьте свойство <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> только к одному атрибуту <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A>.  
  
     Это свойство служит для обозначения *резервного* сопоставления, если значение дискриминатора из таблицы базы данных не соответствует какому-либо <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> значению в сопоставлениях наследования.  
  
6. Добавьте свойство <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> к атрибуту <xref:System.Data.Linq.Mapping.ColumnAttribute>.  
  
     Это свойство означает, что данный столбец содержит значение <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>.  
  
## <a name="example"></a>Пример  
  
> [!NOTE]
> Если вы используете Visual Studio, можно использовать реляционный конструктор объектов для настройки наследования. См [. раздел как настроить наследование с помощью реляционного конструктора O/R.](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)  
  
 В следующем примере кода `Vehicle` определен как корневой класс, а предыдущие шаги были реализованы для описания иерархии для LINQ.  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>См. также раздел

- [Поддержка наследования](inheritance-support.md)
- [Практическое руководство. Как настроить классы сущностей с помощью редактора кода](how-to-customize-entity-classes-by-using-the-code-editor.md)

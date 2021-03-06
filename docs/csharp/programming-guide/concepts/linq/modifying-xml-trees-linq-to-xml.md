---
title: Изменение деревьев XML (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 8ec47e6d-2363-4694-be46-8d5ca4d15fc9
ms.openlocfilehash: 55e75762772a071b97eecb7d6d78e28c3002a179
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505723"
---
# <a name="modifying-xml-trees-linq-to-xml-c"></a>Изменение деревьев XML (LINQ to XML) (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] служит для хранения XML-дерева в памяти. После загрузки или синтаксического анализа XML-дерева из источника [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] позволяет изменить это дерево, после чего его можно сериализовать, сохранив, например, в файл или отправив на удаленный сервер.  
  
 При изменении дерева на месте используются такие методы, как <xref:System.Xml.Linq.XContainer.Add%2A>.  
  
 Однако существует другой подход, который заключается в использовании функционального построения для создания нового дерева другой формы. В зависимости от типов изменений, которые необходимо внести в XML-дерево, а также в зависимости от размера самого дерева, этот подход может быть более надежным и простым для разработки. В первом разделе этой части приведено сравнение обоих подходов.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Описание:|  
|-----------|-----------------|  
|[Сравнение изменения дерева XML в памяти с функциональной сборкой (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)|Сравниваются изменение XML-дерева в памяти и функциональное построение.|  
|[Добавление элементов, атрибутов и узлов в дерево XML (C#)](../../../../csharp/programming-guide/concepts/linq/adding-elements-attributes-and-nodes-to-an-xml-tree.md)|Приводятся сведения о добавлении элементов, атрибутов или узлов к XML-дереву.|  
|[Изменение элементов, атрибутов и узлов в дереве XML](../../../../csharp/programming-guide/concepts/linq/modifying-elements-attributes-and-nodes-in-an-xml-tree.md)|Приводятся сведения о добавлении существующих элементов, атрибутов или узлов.|  
|[Удаление элементов, атрибутов и узлов из дерева XML (C#)](../../../../csharp/programming-guide/concepts/linq/removing-elements-attributes-and-nodes-from-an-xml-tree.md)|Приводятся сведения об удалении элементов, атрибутов или узлов из XML-дерева.|  
|[Обслуживание пар "имя-значение" (C#)](../../../../csharp/programming-guide/concepts/linq/maintaining-name-value-pairs.md)|Приводится описание того, как следует поддерживать сведения о приложении, которые лучше всего хранятся в парах «имя-значение», например сведения о настройках или глобальные настройки.|  
|[Практическое руководство. Изменение пространства имен для всего дерева XML (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-change-the-namespace-for-an-entire-xml-tree.md)|Показывается, как переместить XML-дерево из одного пространства имен в другое.|  
  
## <a name="see-also"></a>См. также

- [Руководство по программированию (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)

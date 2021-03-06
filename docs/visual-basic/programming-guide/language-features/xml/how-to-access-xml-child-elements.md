---
title: Практическое руководство. Доступ к дочерним XML-элементам (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: 4ec7743a30b8101d813ac414a8f5164aeb6c593d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649208"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a>Практическое руководство. Доступ к дочерним XML-элементам (Visual Basic)
В этом примере показано, как использовать дочерний свойство оси для доступа к все дочерние элементы XML, которые имеют указанное имя в элементе XML. В частности, он использует <xref:System.Xml.Linq.XElement.Value%2A> свойство, чтобы получить значение первого элемента в коллекции, `name` возвращает свойство дочерней оси. `name` Свойство дочерней оси возвращает все дочерние элементы с именем `phone` в `contact` объекта. В этом примере также используется `phone` свойство дочерней оси для доступа к все дочерние элементы с именем `phone` , содержащихся в `contact` объекта.  
  
## <a name="example"></a>Пример  
 [!code-vb[VbXMLSamples#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-child-elements_1.vb)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера требуются:  
  
-   ссылка на пространство имен <xref:System.Xml.Linq>.  
  
## <a name="see-also"></a>См. также  
 <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>  
 [Свойство дочерней оси XML](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [Свойство значения XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)  
 [Доступ к XML в Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)

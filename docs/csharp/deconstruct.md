---
title: "Деконструкция кортежей и других типов"
description: "Сведения о деконструкции кортежей и других типов."
keywords: .NET,.NET Core,C#
author: rpetrusha
ms-author: ronpet
ms.date: 07/18/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 0b0c4b0f-4a47-4f66-9b8e-f5c63b195960
ms.translationtype: HT
ms.sourcegitcommit: 863940512f33568ee10569da4712e7e646bc3ba7
ms.openlocfilehash: ad0ed6568da073683545727ef47f6a223942c8d6
ms.contentlocale: ru-ru
ms.lasthandoff: 08/12/2017

---
# <a name="deconstructing-tuples-and-other-types"></a>Деконструкция кортежей и других типов #

Кортеж позволяет вам легко получить несколько значений при вызове метода. Но после получения кортежа вам нужно будет обработать его отдельные элементы. Это довольно неудобно, как показано в следующем примере. Метод `QueryCityData` возвращает кортеж из трех элементов, и каждый из его элементов присваивается переменной за отдельную операцию.

[!code-csharp[Без деконструкции](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple1.cs)]

Получение множества значений полей и свойств из объекта может быть столь же неудобно: необходимо присваивать значение каждого поля или свойства отдельной переменной. 

Начиная с C# 7 вы можете извлекать из кортежа множество элементов или получать множество значений полей, свойств и вычисляемых значений из объекта, используя всего одну операцию *деконструкции*. При деконструкции кортежа вы присваиваете его элементы отдельным переменным. При деконструкции объекта вы присваиваете отдельным переменным выбранные значения. 

## <a name="deconstructing-a-tuple"></a>Деконструкция кортежа

Язык C# имеет встроенную поддержку деконструкции кортежей, которая позволяет извлекать из кортежа все элементы за одну операцию. Общий синтаксис деконструкции кортежа напоминает синтаксис его определения: переменные, которым будут присвоены элементы кортежа, указываются в круглых скобках в левой части оператора присваивания. Например, следующий оператор присваивает элементы кортежа из четырех элементов четырем отдельным переменным:

```csharp
var (name, address, city, zip) = contact.GetAddressInfo();
```

Существует два способа деконструкции кортежа:

- Вы можете явно объявить тип каждого поля в скобках. В следующем примере этот способ используется для деконструкции кортежа из трех элементов, возвращаемого методом `QueryCityData`.

    [!code-csharp[Явная деконструкция](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple2.cs#1)]

- Вы можете использовать ключевое слово `var`, чтобы C# определил тип каждой переменной. Ключевое слово `var` помещается за пределами скобок. В следующем примере используется определение типа при деконструкции кортежа из трех элементов, возвращаемого методом `QueryCityData`.
 
    [!code-csharp[Deconstruction-Infer](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple3.cs#1)]

    Кроме того, вы можете использовать ключевое слово `var` при объявлении отдельных или всех переменных внутри скобок. 

    [!code-csharp[Deconstruction-Infer-Some](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple4.cs#1)]

    Это неудобно и не рекомендуется.

Обратите внимание, что вы не можете указать определенный тип за скобками, даже если все поля в кортеже имеют один и тот же тип. Это приведет к возникновению ошибки компилятора CS8136 "Форма деконструкции 'var (...)' не разрешает использовать конкретный тип для 'var'.".

Обратите внимание, что каждый элемент кортежа необходимо присвоить переменной. Если вы пропустите какие-то элементы, компилятор выдаст сообщение об ошибке CS8132 "Невозможно деконструировать кортеж из "x" элементов на "y" переменных".

## <a name="deconstructing-tuple-elements-with-discards"></a>Деконструкция элементов кортежа с использованием пустых переменных

При деконструкции кортежа нас часто интересуют значения только некоторых элементов. Начиная с C# 7 вы можете воспользоваться поддержкой *пустых переменных*, которые представляют собой доступные только для записи переменные, значения которых нас не интересуют. Пустая переменная обозначается символом нижнего подчеркивания ("\_") в операторе присваивания. Вы можете сделать пустыми сколько угодно значений. Все они будут считаться одной переменной, `_`.

В следующем примере показано использование кортежей с пустыми переменными. Метод `QueryCityDataForYears` возвращает кортеж из шести элементов: название города, его площадь, год, численность населения города в этом году, другой год и численность населения в том году. В примере показано изменение численности населения за эти два года. Из доступных в кортеже данных нас не интересует площадь города, а название города и две даты известны нам уже на этапе разработки. Следовательно, нас интересуют только два значения численности населения, которые хранятся в кортеже. Остальные значения можно обработать как пустые переменные.  

[!code-csharp[Кортеж и пустые переменные](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

### <a name="deconstructing-user-defined-types"></a>Деконструкция пользовательских типов

Типы, не являющиеся кортежами, не предоставляют встроенную поддержку пустых переменных. Тем не менее, если вы являетесь создателем класса, структуры или интерфейса, вы можете разрешить деконструкцию экземпляров определенного типа, реализовав один или несколько методов `Deconstruct`. Метод возвращает "void", и каждое деконструируемое значение обозначается параметром [out](language-reference/keywords/out-parameter-modifier.md) в сигнатуре метода. Например, следующий метод `Deconstruct` класса `Person` возвращает имя, отчество и фамилию:

[!code-csharp[Деконструкция класса](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#1)]

Затем вы можете выполнить деконструкцию экземпляра класса `Person` с именем `p`, используя подобное присваивание:

[!code-csharp[Деконструкция класса](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#2)]

В следующем примере показана перегрузка метода `Deconstruct` для возвращения различных сочетаний свойств объекта `Person`. Отдельные перегрузки возвращают следующие значения:

- Имя и фамилия.
- Имя, фамилия и отчество.
- Имя, фамилия, название города и название штата.

[!code-csharp[Деконструкция класса](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class2.cs)]

Так как метод `Deconstruct` может быть перегружен с учетом групп данных, которые часто извлекаются из объекта, следует соблюдать осторожность и определять методы `Deconstruct` с уникальными и однозначными сигнатурами. Различные методы `Deconstruct` с одинаковым количеством параметров `out` или с одинаковым количеством и типом параметров `out` в разном порядке могут привести к путанице. 

Перегруженный метод `Deconstruct` в следующем примере иллюстрирует один из источников возможной путаницы. Первая перегрузка возвращает имя, отчество, фамилию и возраст объекта `Person` именно в таком порядке. Вторая перегрузка возвращает только сведения об имени вместе с годовым доходом, но имя, отчество и фамилия стоят в другом порядке. Это позволяет легко перепутать порядок аргументов при деконструкции экземпляра `Person`.

[!code-csharp[Неоднозначность при деконструкции](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-ambiguous.cs)]

## <a name="deconstructing-a-user-defined-type-with-discards"></a>Деконструкция пользовательского типа с пустыми переменными

Как и с [кортежами](#deconstructing-tuple-elements-with-discards), пустые переменные можно применять с пользовательскими типами, чтобы игнорировать определенные элементы, возвращаемые методом `Deconstruct`. Каждая пустая переменная определяется переменной с именем "\_", и одна операция деконструкции может включать несколько пустых переменных.

В следующем примере показана деконструкция объекта `Person` на четыре строки (имя, фамилия, город и область), но для фамилии и области используются пустые переменные.

[!code-csharp[Класс и пустые переменные](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs#1)]

## <a name="deconstructing-a-user-defined-type-with-an-extension-method"></a>Деконструкция пользовательского типа с использованием метода расширения

Если вы не являетесь создателем класса, структуры или интерфейса, вы все равно можете выполнять деконструкцию объектов этого типа, реализовав один или несколько `Deconstruct`методов расширения[ ](programming-guide/classes-and-structs/extension-methods.md), которые будут возвращать интересующие вас значения. 

В приведенном ниже примере определены два метода расширения `Deconstruct` для класса <xref:System.Reflection.PropertyInfo?displayProperty=fullName>. Первый метод возвращает набор значений, которые указывают характеристики свойства, в том числе его тип, является ли оно статическим свойством или экземпляром, доступно ли оно только для чтения и является ли оно индексируемым. Второй метод показывает уровень доступа свойства. Так как методы доступа для чтения и записи у свойства могут иметь разный уровень доступа, мы используем логические значения, которые показывают, имеет ли свойство разные методы для чтения и записи и, если это так, имеют ли эти методы один уровень доступа. Если существует только один метод доступа или если методы доступа для чтения и записи имеют один и тот же уровень доступа, переменная `access` показывает доступность свойства в целом. В противном случае доступность методов чтения и записи указывается в переменных `getAccess` и `setAccess`.

[!code-csharp[Деконструкция с использованием метода расширения](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-extension1.cs)]
 
## <a name="see-also"></a>См. также
[Пустые переменные](discards.md)   
[Кортежи](tuples.md)  

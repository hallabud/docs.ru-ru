---
title: Справочник по C#. Оператор ~
ms.custom: seodec18
ms.date: 11/05/2018
f1_keywords:
- ~_CSharpKeyword
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
ms.openlocfilehash: 57e5baee423c0b5d9292d0ad4cbf909646eb3a38
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235729"
---
# <a name="-operator-c-reference"></a>Оператор ~ (справочник по C#)

Оператор битового дополнения `~` — это унарный оператор, который создает битовое дополнение своего операнда с инвертированием каждого бита. Оператор `~` поддерживает все целочисленные типы.

> [!NOTE]
> Символ `~` также используется для объявления методов завершения. Дополнительные сведения см. в разделе [Методы завершения](../../programming-guide/classes-and-structs/destructors.md).

В следующем примере иллюстрируется использование оператора `~`.

[!code-csharp-interactive[bitwise NOT](~/samples/snippets/csharp/language-reference/operators/BitwiseComplementExamples.cs#Example)]

> [!NOTE]
> В предыдущем примере используются двоичные литералы, [впервые появившиеся в C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) и [улучшенные в C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).

## <a name="operator-overloadability"></a>Возможность перегрузки оператора

Определяемые пользователем типы могут [перегружать](../keywords/operator.md) оператор `~`.

## <a name="c-language-specification"></a>Спецификация языка C#

Дополнительные сведения см. в разделе об [операторе битового дополнения](~/_csharplang/spec/expressions.md#bitwise-complement-operator) статьи [Предварительная спецификация C# 6.0](../language-specification/index.md).

## <a name="see-also"></a>См. также

- [Справочник по C#](../index.md)
- [Руководство по программированию на C#](../../programming-guide/index.md)
- [Операторы в C#](index.md)
- [Методы завершения](../../programming-guide/classes-and-structs/destructors.md)
- [Оператор &](and-operator.md)
- [Оператор |](or-operator.md)
- [Оператор ^](xor-operator.md)

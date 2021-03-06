---
title: Создание библиотеки классов .NET Standard на C# с помощью Visual Studio 2017
description: Сведения о создании библиотеки классов .NET Standard, написанной на языке C#, с помощью Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 0c98f8c8fc4847570964d8d4ea8deb221164441d
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168940"
---
# <a name="build-a-net-standard-class-library-with-c-and-the-net-core-sdk-in-visual-studio-2017"></a>Создание библиотеки классов .NET Standard с помощью C# и пакета SDK для .NET Core в Visual Studio 2017

*Библиотека классов* определяет типы и методы, которые могут быть вызваны из любого приложения. Библиотеку классов, предназначенную для .NET Standard 2.0, можно вызывать из любой реализации .NET, которая поддерживает эту версию .NET Standard. Когда вы завершите создание библиотеки классов, вы сможете по своему усмотрению распространять ее как независимый компонент или включить в состав одного или нескольких приложений.

> [!NOTE]
> Список версий .NET Standard и поддерживаемых ими платформ см. в разделе [.NET Standard](../../standard/net-standard.md).

В этой статье вы создадите простую служебную библиотеку с одним методом для обработки строк. Вы реализуете его как [метод расширения](../../csharp/programming-guide/classes-and-structs/extension-methods.md), чтобы вызывать его так же, как любой член класса <xref:System.String>.

## <a name="creating-a-class-library-solution"></a>Создание решения для библиотеки классов

Начнем с создания решения для нашего проекта библиотеки классов и связанных с ней проектов. Решение Visual Studio служит контейнером для одного или нескольких проектов. Чтобы создать решение, выполните следующее.

1. В строке меню Visual Studio выберите **Файл** > **Создать** > **Проект**.

1. В диалоговом окне **Новый проект** разверните узел **Другие типы проектов** и выберите **Решения Visual Studio**. Присвойте решению имя ClassLibraryProjects и нажмите кнопку **ОК**.

   ![Диалоговое окно создания проекта с выделенным новым решением](./media/library-with-visual-studio/new-project-dialog.png)

## <a name="creating-the-class-library-project"></a>Создание проекта для библиотеки классов

Теперь можно создать проект библиотеки классов.

1. В **обозревателе решений** щелкните правой кнопкой мыши решение **ClassLibraryProjects** и в контекстном меню выберите **Добавить** > **Новый проект**.

1. В диалоговом окне **Добавление нового проекта** разверните узел **Visual C#**, выберите узел **.NET Standard**, а затем — шаблон проекта **Библиотека классов (.NET Standard)**. В текстовом поле **Имя** введите имя проекта StringLibrary. Нажмите **ОК**, чтобы создать проект библиотеки классов.

   ![Диалоговое окно добавления нового проекта библиотеки](./media/library-with-visual-studio/add-new-library-project.png)

   Окно кода затем откроется в среде разработки Visual Studio.

   ![Окно приложения Visual Studio, отображающее код шаблона библиотеки классов по умолчанию](./media/library-with-visual-studio/string-library-project.png)

1. Проверьте, предназначена ли библиотека для правильной версии .NET Standard. В **обозревателе решений** щелкните проект библиотеки правой кнопкой мыши и выберите пункт **Свойства**. В текстовом поле **Целевая платформа** указано, что целевой платформой является .NET Standard 2.0.

   ![Свойства проекта для библиотеки классов](./media/library-with-visual-studio/library-project-properties.png)

1. Замените код, отображаемый в окне кода, следующим текстом, а затем сохраните файл.

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   Библиотека классов (`UtilityLibraries.StringLibrary`) содержит метод с именем `StartsWithUpper`, который возвращает значение <xref:System.Boolean>. Это значение указывает, является ли первым символом текущего экземпляра строки символ верхнего регистра. Символы верхнего регистра определяются по стандарту Юникод. Метод <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> возвращает `true`, если символ является символом верхнего регистра.

1. В строке меню выберите **Сборка** > **Собрать решение**. Проект должен скомпилироваться без ошибок.

   ![Область вывода, показывающая успешное завершение сборки](./media/library-with-visual-studio/output-pane-successful-build.png)

## <a name="next-step"></a>Дальнейшие действия

Итак, вы успешно создали библиотеку. Пока вы еще не вызывали ее методов, поэтому нельзя быть уверенным, что все работает так, как ожидалось. Следующий шаг в разработке библиотеки — тестирование с помощью [проекта модульного теста](testing-library-with-visual-studio.md).
---
title: "Стратегия безопасности WPF — проектирование безопасности | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "управление критичным кодом"
  - "SDL (Безопасность цикла разработки), управление критичным кодом"
  - "SDL (Безопасность цикла разработки), анализ безопасности"
  - "SDL (Безопасность цикла разработки), средства анализа исходного кода"
  - "SDL (Безопасность цикла разработки), средства редактирования исходного кода"
  - "SDL (Безопасность цикла разработки), способы тестирования"
  - "SDL (Безопасность цикла разработки), моделирование угроз"
  - "безопасность, способы тестирования"
  - "средства анализа исходного кода"
  - "средства редактирования исходного кода"
  - "проверка, безопасность"
  - "моделирование угроз"
ms.assetid: 0fc04394-4e47-49ca-b0cf-8cd1161d95b9
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Стратегия безопасности WPF — проектирование безопасности
Trustworthy Computing \(защищенные информационные системы\) — это инициатива корпорации Майкрософт по созданию безопасного кода.  Ключевым элементом для создания защищенных информационных систем является [!INCLUDE[TLA#tla_sdl](../../../includes/tlasharptla-sdl-md.md)].  [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] является технической практикой, которая используется в сочетании со стандартными инженерными процессами для облегчения доставки безопасного кода.  [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] состоит из десяти этапов, которые объединяют рекомендации с формализацией, измеряемостью и дополнительными структурами, включая:  
  
-   анализ разработки безопасности;  
  
-   проверки качества на основе инструментов;  
  
-   тестирование уязвимости;  
  
-   окончательный анализ безопасности;  
  
-   управление безопасностью после выпуска продукта.  
  
## Особенности WPF  
 Группа разработки [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] применяет и расширяет [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)], сочетание которых включает следующие ключевые аспекты.  
  
 [Моделирование угроз](#thread_modeling)  
  
 [Анализ безопасности и средства редактирования](#tools)  
  
 [Способы тестирования](#techniques)  
  
 [Управление критическим кодом](#critical_code)  
  
<a name="threat_modeling"></a>   
### Моделирование угроз  
 Моделирование угроз является основным компонентом [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] и используется для профилирования системы, чтобы определить потенциальные уязвимости системы безопасности.  После обнаружения уязвимостей моделирование угроз также гарантирует принятие соответствующих мер по снижению уязвимости.  
  
 На высоком уровне моделирование угроз включает следующие основные этапы, если использовать в качестве примера продуктовый магазин.  
  
1.  **Идентификация активов**.  Активы продуктового магазина могут включать сотрудников, сейф, кассовые аппараты и склад.  
  
2.  **Перечисление точек входа**.  Точки входа продуктового магазина могут включать переднюю и заднюю двери, окна, погрузочный док и установки для кондиционирования воздуха.  
  
3.  **Изучение атак на активы с использованием точек входа**.  Одна из возможных атак может быть предпринята на *сейф* продуктового магазина через *установку для кондиционирования воздуха*; эта установка может быть выкручена, чтобы вытянуть через нее сейф и покинуть магазин.  
  
 Моделирование угроз применяется во всем [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] и включает следующее.  
  
-   Как средство синтаксического анализа [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] читает файлы, сопоставляет текст с соответствующими классами объектной модели и создает фактический код.  
  
-   Как дескриптор окна \(hWnd\) создается, отправляет сообщения и используется для отображения содержимого окна.  
  
-   Как привязка данных получает ресурсы и взаимодействует с системой.  
  
 Эти модели угроз важны для идентификации требований к разработке системы безопасности и снижения угроз в процессе разработки.  
  
<a name="tools"></a>   
### Анализ безопасности и средства редактирования  
 В дополнение к ручному анализу кода безопасности элементов [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] группа  [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] использует несколько средств для анализа источника и связанных правок для уменьшения уязвимости системы безопасности.  Используются широкий диапазон средств, который включает следующее.  
  
-   **FXCop**: выполняется поиск общих проблем безопасности в управляемом коде — от правил наследования до использования управления доступом для кода для безопасного взаимодействия с неуправляемым кодом.  См. описание [FXCop](http://www.gotdotnet.com/team/fxcop/).  
  
-   **Prefix\/Prefast**: выполняется поиск уязвимостей системы безопасности и общих проблем безопасности в неуправляемом коде, таких как переполнение буфера, проблемы форматирования строк и проверка ошибок.  
  
-   **Запрещенные API**: выполняется поиск в исходном коде случайного использования функций, которые известны своими проблемами безопасности, таких как `strcpy`.  После обнаружения эти функции заменяются альтернативными, которые имеют более высокий уровень безопасности.  
  
<a name="techniques"></a>   
### Способы тестирования  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] использует различные методы тестирования безопасности, включая следующие.  
  
-   **Тестирование методом белого ящика**. Тестировщики просматривают исходный код и затем создают эксплойт\-тесты.  
  
-   **Тестирование методом черного ящика**. Тестировщики пытаются найти атаки системы безопасности, проверяя API и компоненты, а затем пытаются атаковать продукт.  
  
-   **Регрессирование проблем безопасности от других продуктов**. Тестирование соответственных проблем безопасности от связанных продуктов.  Например, соответствующие варианты приблизительно шестидесяти проблем безопасности для [!INCLUDE[TLA2#tla_ie](../../../includes/tla2sharptla-ie-md.md)] определены и испытаны на их применимость к [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].  
  
-   **Тестирование уязвимости на основе инструментов с помощью нечеткого тестирования файлов**. Нечеткое тестирование файлов — это эксплуатация входного диапазона модуля чтения файлов с помощью разнообразных входных данных.  Одним из примеров в [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], где используется этот способ, является проверка неисправности в коде декодирования изображения.  
  
<a name="critical_code"></a>   
### Управление критическим кодом  
 Для [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] строит песочницу безопасности, используя поддержку [!INCLUDE[TLA2#tla_winfx](../../../includes/tla2sharptla-winfx-md.md)] пометки и отслеживания критического с точки зрения безопасности кода, который повышает права \(см. раздел **Методология, критическая с точки зрения безопасности** в статье [Стратегия безопасности WPF — безопасность платформы](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)\).  Учитывая требования к высокому качеству безопасности при защите важного кода, такой код получает дополнительный уровень управления источником и аудита безопасности.  Приблизительно от 5 % до 10 % [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] состоит из кода, критического с точки зрения безопасности, который анализируется выделенной группой анализа.  Исходный код и постановка кода на учет управляются путем отслеживания кода, критического с точки зрения безопасности, и сопоставления каждой критической сущности \(например,  метода, содержащего важный код\) с ее утвержденным состоянием.  Утвержденное состояние содержит имена одного или нескольких рецензентов.  Каждая ежедневная сборка [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] сравнивает критически важный код с этим кодом в предыдущих сборках для проверки неутвержденных изменений.  Если инженер изменяет критически важный код без получения утверждения от группы рецензирования, он немедленно обнаруживается и фиксируется.  Этот процесс обеспечивает применение и обслуживание особенно высокого уровня безопасности через код песочницы [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].  
  
## См. также  
 [Безопасность](../../../docs/framework/wpf/security-wpf.md)   
 [Безопасность частичного доверия в WPF](../../../docs/framework/wpf/wpf-partial-trust-security.md)   
 [Стратегия безопасности WPF — безопасность платформы](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)   
 [Защищенные информационные системы](http://www.microsoft.com/mscorp/twc/default.mspx)   
 [Моделирование угроз приложения](http://msdn.microsoft.com/security/securecode/threatmodeling/acetm/)   
 [Рекомендации по безопасности: .NET Framework 2.0](http://msdn.microsoft.com/library/default.asp?url=/library/dnpag2/html/PAGGuidelines0003.asp)
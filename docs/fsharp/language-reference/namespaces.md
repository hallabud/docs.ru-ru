---
title: "Пространства имен (F#)"
description: "Узнайте, как пространство имен F # позволяет организовать код в области связанной функциональности, позволяя присоединить имя группирования элементов программы."
keywords: "visual f#, f#, функциональное программирование"
author: cartermp
ms.author: phcart
ms.date: 04/24/2017
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ea42156f-e1b9-4535-9383-b45f46f3f7ca
ms.openlocfilehash: 4378afebe6fd0d9317f734457576dc75d7488bf0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="namespaces"></a><span data-ttu-id="f1a8c-104">Пространства имен</span><span class="sxs-lookup"><span data-stu-id="f1a8c-104">Namespaces</span></span>

<span data-ttu-id="f1a8c-105">С помощью пространства имен вы можете упорядочить код по областям соответствующей функциональности, подключив имя к группированию элементов программы.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-105">A namespace lets you organize code into areas of related functionality by enabling you to attach a name to a grouping of program elements.</span></span>


## <a name="syntax"></a><span data-ttu-id="f1a8c-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f1a8c-106">Syntax</span></span>

```fsharp
namespace [parent-namespaces.]identifier
```

## <a name="remarks"></a><span data-ttu-id="f1a8c-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="f1a8c-107">Remarks</span></span>
<span data-ttu-id="f1a8c-108">Если вы хотите поместить код в пространстве имен, первого объявления в файле необходимо объявить пространство имен.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-108">If you want to put code in a namespace, the first declaration in the file must declare the namespace.</span></span> <span data-ttu-id="f1a8c-109">Содержимое этого файла становится частью пространства имен.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-109">The contents of the entire file then become part of the namespace.</span></span>

<span data-ttu-id="f1a8c-110">Пространства имен не может содержать непосредственно значения и функции.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-110">Namespaces cannot directly contain values and functions.</span></span> <span data-ttu-id="f1a8c-111">Вместо этого значения и функции должны быть включены в модулях, а модули включены в пространствах имен.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-111">Instead, values and functions must be included in modules, and modules are included in namespaces.</span></span> <span data-ttu-id="f1a8c-112">Пространства имен могут содержать типы модулей.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-112">Namespaces can contain types, modules.</span></span>

<span data-ttu-id="f1a8c-113">Пространства имен может быть объявлено явно с помощью ключевого слова пространства имен или неявно при объявлении модуля.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-113">Namespaces can be declared explicitly with the namespace keyword, or implicitly when declaring a module.</span></span> <span data-ttu-id="f1a8c-114">Чтобы объявить пространство имен явно, используйте ключевое слово namespace, за которым следует имя пространства имен.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-114">To declare a namespace explicitly, use the namespace keyword followed by the namespace name.</span></span> <span data-ttu-id="f1a8c-115">Приведенный ниже показан файл кода, который объявляет пространство имен мини-приложения с типом и модуль, содержащийся в этом пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-115">The following example shows a code file that declares a namespace Widgets with a type and a module included in that namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

<span data-ttu-id="f1a8c-116">Если все содержимое файла является частью одного модуля, можно также объявить пространств имен неявно с помощью `module` ключевое слово и новое имя пространства имен в полное имя модуля.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-116">If the entire contents of the file are in one module, you can also declare namespaces implicitly by using the `module` keyword and providing the new namespace name in the fully qualified module name.</span></span> <span data-ttu-id="f1a8c-117">В следующем примере показано файл кода, который объявляет пространство имен `Widgets` и модуль `WidgetsModule`, содержащего функцию.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-117">The following example shows a code file that declares a namespace `Widgets` and a module `WidgetsModule`, which contains a function.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

<span data-ttu-id="f1a8c-118">Следующий код эквивалентен приведенный выше код, но модуль является объявление локального модуля.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-118">The following code is equivalent to the preceding code, but the module is a local module declaration.</span></span> <span data-ttu-id="f1a8c-119">В этом случае пространство имен должно отображаться на отдельной строке.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-119">In that case, the namespace must appear on its own line.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/namespaces/snippet6402.fs)]

<span data-ttu-id="f1a8c-120">Если требуется более чем в одном модуле в том же файле, в один или несколько пространств имен, необходимо использовать локальное объявление модулей.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-120">If more than one module is required in the same file in one or more namespaces, you must use local module declarations.</span></span> <span data-ttu-id="f1a8c-121">При использовании локальных объявления модулей, полное имя пространства имен нельзя использовать в объявлениях модуля.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-121">When you use local module declarations, you cannot use the qualified namespace in the module declarations.</span></span> <span data-ttu-id="f1a8c-122">Ниже приведен файл, содержащий объявление пространства имен и два локальных объявления модулей.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-122">The following code shows a file that has a namespace declaration and two local module declarations.</span></span> <span data-ttu-id="f1a8c-123">В этом случае модули содержатся непосредственно в пространстве имен; Нет не неявно созданного модуля, который имеет то же имя, что и файл.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-123">In this case, the modules are contained directly in the namespace; there is no implicitly created module that has the same name as the file.</span></span> <span data-ttu-id="f1a8c-124">Любой другой код в файле, такие как `do` привязки, является в пространстве имен, но не во внутренних модулях, поэтому вам необходимо для уточнения члена модуля `widgetFunction` , используя имя модуля.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-124">Any other code in the file, such as a `do` binding, is in the namespace but not in the inner modules, so you need to qualify the module member `widgetFunction` by using the module name.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

<span data-ttu-id="f1a8c-125">Выходные данные этого примера выглядит следующим образом.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-125">The output of this example is as follows.</span></span>

```fsharp
Module1 10 20
Module2 5 6
```

<span data-ttu-id="f1a8c-126">Дополнительные сведения см. в разделе [модулей](modules.md).</span><span class="sxs-lookup"><span data-stu-id="f1a8c-126">For more information, see [Modules](modules.md).</span></span>

## <a name="nested-namespaces"></a><span data-ttu-id="f1a8c-127">Вложенные пространства имен</span><span class="sxs-lookup"><span data-stu-id="f1a8c-127">Nested Namespaces</span></span>
<span data-ttu-id="f1a8c-128">При создании вложенных пространств имен, необходимо определить его полностью.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-128">When you create a nested namespace, you must fully qualify it.</span></span> <span data-ttu-id="f1a8c-129">В противном случае создается новое пространство имен верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-129">Otherwise, you create a new top-level namespace.</span></span> <span data-ttu-id="f1a8c-130">Отступ игнорируется в объявления пространств имен.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-130">Indentation is ignored in namespace declarations.</span></span>

<span data-ttu-id="f1a8c-131">В следующем примере показан способ объявления вложенных пространств имен.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-131">The following example shows how to declare a nested namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a><span data-ttu-id="f1a8c-132">Пространства имен в файлы и сборки</span><span class="sxs-lookup"><span data-stu-id="f1a8c-132">Namespaces in Files and Assemblies</span></span>
<span data-ttu-id="f1a8c-133">Пространства имен может охватывать несколько файлов проекта или компиляции.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-133">Namespaces can span multiple files in a single project or compilation.</span></span> <span data-ttu-id="f1a8c-134">Термин *фрагмент пространства имен* описываются части пространства имен, который включен в один файл.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-134">The term *namespace fragment* describes the part of a namespace that is included in one file.</span></span> <span data-ttu-id="f1a8c-135">Пространства имен также могут охватывать несколько сборок.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-135">Namespaces can also span multiple assemblies.</span></span> <span data-ttu-id="f1a8c-136">Например `System` пространство имен включает весь .NET Framework, которая охватывает несколько сборок и содержит много вложенных пространств имен.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-136">For example, the `System` namespace includes the whole .NET Framework, which spans many assemblies and contains many nested namespaces.</span></span>


## <a name="global-namespace"></a><span data-ttu-id="f1a8c-137">Глобальное пространство имен</span><span class="sxs-lookup"><span data-stu-id="f1a8c-137">Global Namespace</span></span>
<span data-ttu-id="f1a8c-138">Используйте стандартные пространства имен `global` включаемые имена в пространство имен .NET верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-138">You use the predefined namespace `global` to put names in the .NET top-level namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

<span data-ttu-id="f1a8c-139">Можно также использовать глобальный для ссылки на пространство имен верхнего уровня .NET, например, чтобы устранить конфликты имен с другими пространствами имен.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-139">You can also use global to reference the top-level .NET namespace, for example, to resolve name conflicts with other namespaces.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

##

<span data-ttu-id="f1a8c-140">F # 4.1 вводится понятие пространства имен, которая разрешает все автономные кода взаимно рекурсивные.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-140">F# 4.1 introduces the notion of namespaces which allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="f1a8c-141">Это выполняется через `namespace rec`.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-141">This is done via `namespace rec`.</span></span>  <span data-ttu-id="f1a8c-142">Использование `namespace rec` можно устранить некоторые усилия невозможности писать код взаимно ссылочной между типами и модулей.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-142">Use of `namespace rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span>  <span data-ttu-id="f1a8c-143">Ниже приведен пример этого:</span><span class="sxs-lookup"><span data-stu-id="f1a8c-143">The following is an example of this:</span></span>

```fsharp
namespace rec MutualReferences

type Orientation = Up | Down
type PeelState = Peeled | Unpeeled

// This exception depends on the type below.
exception DontSqueezeTheBananaException of Banana

type BananaPeel() = class end

type Banana(orientation : Orientation) =
    member val IsPeeled = false with get, set
    member val Orientation = orientation with get, set
    member val Sides: PeelState list = [ Unpeeled; Unpeeled; Unpeeled; Unpeeled] with get, set
    
    member self.Peel() = BananaHelpers.peel self // Note the dependency on the BananaHelpers module.
    member self.SqueezeJuiceOut() = raise (DontSqueezeTheBananaException self) // This member depends on the exception above.

module BananaHelpers =
    let peel (b : Banana) =
        let flip banana =
            match banana.Orientation with
            | Up -> 
                banana.Orientation <- Down
                banana
            | Down -> banana

        let peelSides banana =
            for side in banana.Sides do
                if side = Unpeeled then
                    side <- Peeled

        match b.Orientation with
        | Up ->   b |> flip |> peelSides
        | Down -> b |> peelSides
```

<span data-ttu-id="f1a8c-144">Обратите внимание, что исключение `DontSqueezeTheBananaException` и класс `Banana` оба обращаются друг к другу.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-144">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="f1a8c-145">Кроме того, модуль `BananaHelpers` и класс `Banana` также обращаются друг к другу.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-145">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span>  <span data-ttu-id="f1a8c-146">Это будет невозможно выразить в F #, если вы удалили `rec` ключевое слово из `MutualReferences` пространства имен.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-146">This would not be possible to express in F# if you removed the `rec` keyword from the `MutualReferences` namespace.</span></span>

<span data-ttu-id="f1a8c-147">Эта функция также доступна для верхнего уровня [модули](modules.md) в F # 4.1 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="f1a8c-147">This feature is also available for top-level [Modules](modules.md) in F# 4.1 or higher.</span></span>

## <a name="see-also"></a><span data-ttu-id="f1a8c-148">См. также</span><span class="sxs-lookup"><span data-stu-id="f1a8c-148">See Also</span></span>
[<span data-ttu-id="f1a8c-149">Справочник по языку F#</span><span class="sxs-lookup"><span data-stu-id="f1a8c-149">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="f1a8c-150">Модули</span><span class="sxs-lookup"><span data-stu-id="f1a8c-150">Modules</span></span>](modules.md)

[<span data-ttu-id="f1a8c-151">F # RFC FS-1009 - разрешить взаимно ссылочные типы и модули через большего пространства в файлах</span><span class="sxs-lookup"><span data-stu-id="f1a8c-151">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
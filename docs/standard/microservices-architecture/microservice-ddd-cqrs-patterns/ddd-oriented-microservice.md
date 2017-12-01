---
title: "Проектирование микрослужбу, ориентированных на DDD"
description: "Архитектура Микрослужбами .NET для приложений .NET в контейнерах | Проектирование микрослужбу, ориентированных на DDD"
keywords: "Docker, микрослужбы, ASP.NET, контейнер"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: df45441089fd59d5e0e52b4bcec409adcc11fb71
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="designing-a-ddd-oriented-microservice"></a><span data-ttu-id="999f2-104">Проектирование микрослужбу, ориентированных на DDD</span><span class="sxs-lookup"><span data-stu-id="999f2-104">Designing a DDD-oriented microservice</span></span>

<span data-ttu-id="999f2-105">Проектирование на основе домена (DDD) представляет моделирования, в зависимости от реальности бизнес-как относящиеся к сценариям использования.</span><span class="sxs-lookup"><span data-stu-id="999f2-105">Domain-driven design (DDD) advocates modeling based on the reality of business as relevant to your use cases.</span></span> <span data-ttu-id="999f2-106">В контексте создания приложений DDD рассказывает о проблемах как домены.</span><span class="sxs-lookup"><span data-stu-id="999f2-106">In the context of building applications, DDD talks about problems as domains.</span></span> <span data-ttu-id="999f2-107">Описывает независимых проблемных областей, как ограниченных контекстах (каждый контекст ограниченных соответствующее микрослужбу), подчеркиваются общий язык говорить о таких проблем.</span><span class="sxs-lookup"><span data-stu-id="999f2-107">It describes independent problem areas as Bounded Contexts (each Bounded Context correlates to a microservice), and emphasizes a common language to talk about these problems.</span></span> <span data-ttu-id="999f2-108">В нем также рассматриваются многие технические концепции и шаблоны, подобно сущностям домена с форматированным моделями (не [anemic доменной модели](https://martinfowler.com/bliki/AnemicDomainModel.html)), значение объектов, агрегаты и статистические корень (или корневой объект) правил для поддержки внутренней реализации.</span><span class="sxs-lookup"><span data-stu-id="999f2-108">It also suggests many technical concepts and patterns, like domain entities with rich models (no [anemic-domain model](https://martinfowler.com/bliki/AnemicDomainModel.html)), value objects, aggregates and aggregate root (or root entity) rules to support the internal implementation.</span></span> <span data-ttu-id="999f2-109">В этом разделе представлены на проектирование и реализацию этих внутренних шаблонов.</span><span class="sxs-lookup"><span data-stu-id="999f2-109">This section introduces the design and implementation of those internal patterns.</span></span>

<span data-ttu-id="999f2-110">Иногда эти DDD технические правила и закономерности считается препятствия, имеющих некоторого обучения для реализации подхода ддд.</span><span class="sxs-lookup"><span data-stu-id="999f2-110">Sometimes these DDD technical rules and patterns are perceived as obstacles that have a steep learning curve for implementing DDD approaches.</span></span> <span data-ttu-id="999f2-111">Однако важно не шаблоны сами себя, но организации кода, поэтому она выравнивается по бизнес-проблемы и с помощью одной бизнес-термины (единый язык).</span><span class="sxs-lookup"><span data-stu-id="999f2-111">But the important part is not the patterns themselves, but organizing the code so it is aligned to the business problems, and using the same business terms (ubiquitous language).</span></span> <span data-ttu-id="999f2-112">Кроме того подходов DDD должны применяться только в том случае, если вы реализуете сложных микрослужбами с значительные бизнес-правила.</span><span class="sxs-lookup"><span data-stu-id="999f2-112">In addition, DDD approaches should be applied only if you are implementing complex microservices with significant business rules.</span></span> <span data-ttu-id="999f2-113">Проще обязанности, таких как службы CRUD, можно управлять с простым подходов.</span><span class="sxs-lookup"><span data-stu-id="999f2-113">Simpler responsibilities, like a CRUD service, can be managed with simpler approaches.</span></span>

<span data-ttu-id="999f2-114">Где рисовать границы является основной задачей при разработке и определении микрослужбы.</span><span class="sxs-lookup"><span data-stu-id="999f2-114">Where to draw the boundaries is the key task when designing and defining a microservice.</span></span> <span data-ttu-id="999f2-115">DDD шаблоны помогают понять сложности в домене.</span><span class="sxs-lookup"><span data-stu-id="999f2-115">DDD patterns help you understand the complexity in the domain.</span></span> <span data-ttu-id="999f2-116">Для модели домена для каждого контекста ограниченных идентификации и определения сущностей, значение объектов и статистические функции, которые моделируют вашего домена.</span><span class="sxs-lookup"><span data-stu-id="999f2-116">For the domain model for each Bounded Context, you identify and define the entities, value objects, and aggregates that model your domain.</span></span> <span data-ttu-id="999f2-117">Постройте и детализации модели домена, содержащийся в границу, которая определяет контекст.</span><span class="sxs-lookup"><span data-stu-id="999f2-117">You build and refine a domain model that is contained within a boundary that defines your context.</span></span> <span data-ttu-id="999f2-118">И это явным образом в виде микрослужбы.</span><span class="sxs-lookup"><span data-stu-id="999f2-118">And that is very explicit in the form of a microservice.</span></span> <span data-ttu-id="999f2-119">Компоненты в пределах этих границ помещаться выполняется вашей микрослужбами, несмотря на то что в некоторых случаях a BC или микрослужбами бизнеса могут состоять из нескольких физических служб.</span><span class="sxs-lookup"><span data-stu-id="999f2-119">The components within those boundaries end up being your microservices, although in some cases a BC or business microservices can be composed of several physical services.</span></span> <span data-ttu-id="999f2-120">DDD посвящена границы, а следовательно, являются микрослужбами.</span><span class="sxs-lookup"><span data-stu-id="999f2-120">DDD is about boundaries and so are microservices.</span></span>

## <a name="keep-the-microservice-context-boundaries-relatively-small"></a><span data-ttu-id="999f2-121">Сохранить микрослужбу границ контекста относительно небольшой</span><span class="sxs-lookup"><span data-stu-id="999f2-121">Keep the microservice context boundaries relatively small</span></span>

<span data-ttu-id="999f2-122">Определение поместить границы между контекстами ограниченных сальдо два конкурирующих задач.</span><span class="sxs-lookup"><span data-stu-id="999f2-122">Determining where to place boundaries between Bounded Contexts balances two competing goals.</span></span> <span data-ttu-id="999f2-123">Во-первых необходимо первоначально создать наименьшее возможных микрослужбами, несмотря на то, что не должно быть основной драйвера. следует создать границу вещей, которые требуется связности.</span><span class="sxs-lookup"><span data-stu-id="999f2-123">First, you want to initially create the smallest possible microservices, although that should not be the main driver; you should create a boundary around things that need cohesion.</span></span> <span data-ttu-id="999f2-124">Во-вторых вы хотите избежать «многословных» обмена данными между микрослужбами.</span><span class="sxs-lookup"><span data-stu-id="999f2-124">Second, you want to avoid chatty communications between microservices.</span></span> <span data-ttu-id="999f2-125">Эти цели могут противоречить друг с другом.</span><span class="sxs-lookup"><span data-stu-id="999f2-125">These goals can contradict one another.</span></span> <span data-ttu-id="999f2-126">Вы должны сбалансировать по разбиение столько небольшой микрослужбами можно, пока не увидите быстро растет с каждой дополнительной попытки разделения новый контекст ограниченных границы связи в системе.</span><span class="sxs-lookup"><span data-stu-id="999f2-126">You should balance them by decomposing the system into as many small microservices as you can until you see communication boundaries growing quickly with each additional attempt to separate a new Bounded Context.</span></span> <span data-ttu-id="999f2-127">Связности является ключом, в рамках одного контекста ограниченной.</span><span class="sxs-lookup"><span data-stu-id="999f2-127">Cohesion is key within a single bounded context.</span></span>

<span data-ttu-id="999f2-128">Это похоже на [недопустимо тесные отношения кода Запах](https://sourcemaking.com/refactoring/smells/inappropriate-intimacy) при реализации классов.</span><span class="sxs-lookup"><span data-stu-id="999f2-128">It is similar to the [Inappropriate Intimacy code smell](https://sourcemaking.com/refactoring/smells/inappropriate-intimacy) when implementing classes.</span></span> <span data-ttu-id="999f2-129">Если два микрослужбами нужно совместно работать намного друг с другом, они, скорее всего, должны быть же микрослужбы.</span><span class="sxs-lookup"><span data-stu-id="999f2-129">If two microservices need to collaborate a lot with each other, they should probably be the same microservice.</span></span>

<span data-ttu-id="999f2-130">Другим способом, это является автономность.</span><span class="sxs-lookup"><span data-stu-id="999f2-130">Another way to look at this is autonomy.</span></span> <span data-ttu-id="999f2-131">Если микрослужбу должно полагаться на другую службу для обслуживания запроса напрямую, не полностью автономной.</span><span class="sxs-lookup"><span data-stu-id="999f2-131">If a microservice must rely on another service to directly service a request, it is not truly autonomous.</span></span>

## <a name="layers-in-ddd-microservices"></a><span data-ttu-id="999f2-132">Слои в DDD микрослужбами</span><span class="sxs-lookup"><span data-stu-id="999f2-132">Layers in DDD microservices</span></span>

<span data-ttu-id="999f2-133">Большинство приложений предприятия с значительные бизнеса и сложности: определяются несколько слоев.</span><span class="sxs-lookup"><span data-stu-id="999f2-133">Most enterprise applications with significant business and technical complexity are defined by multiple layers.</span></span> <span data-ttu-id="999f2-134">Слои являются артефакт логического и не относятся к развертыванию службы.</span><span class="sxs-lookup"><span data-stu-id="999f2-134">The layers are a logical artifact, and are not related to the deployment of the service.</span></span> <span data-ttu-id="999f2-135">Они существуют, чтобы помочь разработчикам управлять сложным процессом, в коде.</span><span class="sxs-lookup"><span data-stu-id="999f2-135">They exist to help developers manage the complexity in the code.</span></span> <span data-ttu-id="999f2-136">Различные уровни (например, уровень модели домена и уровень представления данных, т. д.) может иметь разные типы, которого требует преобразования между этими типами.</span><span class="sxs-lookup"><span data-stu-id="999f2-136">Different layers (like the domain model layer versus the presentation layer, etc.) might have different types, which mandates translations between those types.</span></span>

<span data-ttu-id="999f2-137">Например сущность может быть загружен из базы данных.</span><span class="sxs-lookup"><span data-stu-id="999f2-137">For example, an entity could be loaded from the database.</span></span> <span data-ttu-id="999f2-138">Затем эти сведения, и объединенные данные, включая дополнительные данные из других сущностей, могут отправляться клиенту пользовательский Интерфейс в веб-API REST.</span><span class="sxs-lookup"><span data-stu-id="999f2-138">Then part of that information, or an aggregation of information including additional data from other entities, can be sent to the client UI through a REST Web API.</span></span> <span data-ttu-id="999f2-139">Суть в том что сущность домена содержится в слой модели домена и не должны распространяться на других областей, которые он не принадлежит, как уровень представления данных.</span><span class="sxs-lookup"><span data-stu-id="999f2-139">The point here is that the domain entity is contained within the domain model layer and should not be propagated to other areas that it does not belong to, like to the presentation layer.</span></span>

<span data-ttu-id="999f2-140">Кроме того, необходимо иметь всегда действует сущностей (см. [проектирование проверок в уровне модели домена](#designing-validations-in-the-domain-model-layer) раздел) контролируются статистические корни (корневой сущности).</span><span class="sxs-lookup"><span data-stu-id="999f2-140">Additionally, you need to have always-valid entities (see the [Designing validations in the domain model layer](#designing-validations-in-the-domain-model-layer) section) controlled by aggregate roots (root entities).</span></span> <span data-ttu-id="999f2-141">Таким образом сущностей не были привязаны к представлениям клиента, так как на уровне ИП некоторые данные могут по-прежнему не удается проверить.</span><span class="sxs-lookup"><span data-stu-id="999f2-141">Therefore, entities should not be bound to client views, because at the UI level some data might still not be validated.</span></span> <span data-ttu-id="999f2-142">Это ViewModel возможности.</span><span class="sxs-lookup"><span data-stu-id="999f2-142">This is what the ViewModel is for.</span></span> <span data-ttu-id="999f2-143">ViewModel — это модель данных исключительно для потребности слой представления.</span><span class="sxs-lookup"><span data-stu-id="999f2-143">The ViewModel is a data model exclusively for presentation layer needs.</span></span> <span data-ttu-id="999f2-144">Сущности домена не принадлежат непосредственно ViewModel.</span><span class="sxs-lookup"><span data-stu-id="999f2-144">The domain entities do not belong directly to the ViewModel.</span></span> <span data-ttu-id="999f2-145">Вместо этого необходимо перевести между сущностями ViewModels и домена и наоборот.</span><span class="sxs-lookup"><span data-stu-id="999f2-145">Instead, you need to translate between ViewModels and domain entities and vice versa.</span></span>

<span data-ttu-id="999f2-146">При работе над сложности, очень важно модель домена управляется статистические корни (углубляться в это более подробно далее), убедитесь, что все инварианты и правила, связанные с этой группы сущностей (статистических) выполняются через одну запись точка или шлюзом, статистические корневой.</span><span class="sxs-lookup"><span data-stu-id="999f2-146">When tackling complexity, it is important to have a domain model controlled by aggregate roots (we go into this in more detail later) that make sure that all the invariants and rules related to that group of entities (aggregate) are performed through a single entry point or gate, the aggregate root.</span></span>

<span data-ttu-id="999f2-147">Рис. 9-5 показано реализации многоуровневая архитектура eShopOnContainers приложения.</span><span class="sxs-lookup"><span data-stu-id="999f2-147">Figure 9-5 shows how a layered design is implemented in the eShopOnContainers application.</span></span>

![](./media/image6.png)

<span data-ttu-id="999f2-148">**Рис. 9-5**.</span><span class="sxs-lookup"><span data-stu-id="999f2-148">**Figure 9-5**.</span></span> <span data-ttu-id="999f2-149">Слои DDD упорядочивания микрослужбу в eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="999f2-149">DDD layers in the ordering microservice in eShopOnContainers</span></span>

<span data-ttu-id="999f2-150">Необходимо разработать систему, чтобы каждый уровень взаимодействует только с некоторых других слоев.</span><span class="sxs-lookup"><span data-stu-id="999f2-150">You want to design the system so that each layer communicates only with certain other layers.</span></span> <span data-ttu-id="999f2-151">Что может быть проще принудительно, если слои реализованы в виде библиотеки другого класса, так как вы четко определить, какие зависимости устанавливаются между библиотеками.</span><span class="sxs-lookup"><span data-stu-id="999f2-151">That may be easier to enforce if layers are implemented as different class libraries, because you can clearly identify what dependencies are set between libraries.</span></span> <span data-ttu-id="999f2-152">Например, уровень модели домена не должен принимать зависимости на любом другом слое (классы модели домена должны быть обычные старые объекты CLR или [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object), классы).</span><span class="sxs-lookup"><span data-stu-id="999f2-152">For instance, the domain model layer should not take a dependency on any other layer (the domain model classes should be Plain Old CLR Objects, or [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object), classes).</span></span> <span data-ttu-id="999f2-153">Как показано на рисунке 9-6, **Ordering.Domain** библиотеки слоя имеет зависимости только в библиотеках .NET Core, но не на любой другой пользовательской библиотеки (библиотека данных, сохранения в библиотеке, и т. д.).</span><span class="sxs-lookup"><span data-stu-id="999f2-153">As shown in Figure 9-6, the **Ordering.Domain** layer library has dependencies only on the .NET Core libraries but not on any other custom library (data library, persistence library, etc.).</span></span>

![](./media/image7.PNG)

<span data-ttu-id="999f2-154">**Рис. 9-6**.</span><span class="sxs-lookup"><span data-stu-id="999f2-154">**Figure 9-6**.</span></span> <span data-ttu-id="999f2-155">Слои, реализован в виде библиотеки позволяют лучше управлять зависимостей между слоями</span><span class="sxs-lookup"><span data-stu-id="999f2-155">Layers implemented as libraries allow better control of dependencies between layers</span></span>

### <a name="the-domain-model-layer"></a><span data-ttu-id="999f2-156">Уровень модели домена</span><span class="sxs-lookup"><span data-stu-id="999f2-156">The domain model layer</span></span>

<span data-ttu-id="999f2-157">Отлично книги Eric Evans [Domain Driven Design](http://domainlanguage.com/ddd/) говорит следующие о уровень модели домена и на уровне приложения.</span><span class="sxs-lookup"><span data-stu-id="999f2-157">Eric Evans's excellent book [Domain Driven Design](http://domainlanguage.com/ddd/) says the following about the domain model layer and the application layer.</span></span>

<span data-ttu-id="999f2-158">**Уровень модели домена**: ответственность для представления понятия бизнеса, сведения о ситуации и бизнес-правил.</span><span class="sxs-lookup"><span data-stu-id="999f2-158">**Domain Model Layer**: Responsible for representing concepts of the business, information about the business situation, and business rules.</span></span> <span data-ttu-id="999f2-159">Состояние, которое отражает состояние дел контролироваться и использовать здесь, несмотря на то, что технические детали запоминался, делегируются в инфраструктуре.</span><span class="sxs-lookup"><span data-stu-id="999f2-159">State that reflects the business situation is controlled and used here, even though the technical details of storing it are delegated to the infrastructure.</span></span> <span data-ttu-id="999f2-160">Этот уровень является сердцем платформы бизнес-программ.</span><span class="sxs-lookup"><span data-stu-id="999f2-160">This layer is the heart of business software.</span></span>

<span data-ttu-id="999f2-161">Уровень модели домена — где выражены бизнеса.</span><span class="sxs-lookup"><span data-stu-id="999f2-161">The domain model layer is where the business is expressed.</span></span> <span data-ttu-id="999f2-162">При реализации слой модели домена микрослужбу в .NET, что слой будет закодировано как библиотеки классов с сущности домена, которые моделируют данных, а также возможности (методы с логикой).</span><span class="sxs-lookup"><span data-stu-id="999f2-162">When you implement a microservice domain model layer in .NET, that layer is coded as a class library with the domain entities that capture data plus behavior (methods with logic).</span></span>

<span data-ttu-id="999f2-163">Следующая [сохраняемости](http://deviq.com/persistence-ignorance/) и [пропуск инфраструктуры](https://ayende.com/blog/3137/infrastructure-ignorance) принципы, этот уровень полностью должен игнорировать детали сохраняемости данных.</span><span class="sxs-lookup"><span data-stu-id="999f2-163">Following the [Persistence Ignorance](http://deviq.com/persistence-ignorance/) and the [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) principles, this layer must completely ignore data persistence details.</span></span> <span data-ttu-id="999f2-164">Эти задачи сохранения следует выполнять на уровне инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="999f2-164">These persistence tasks should be performed by the infrastructure layer.</span></span> <span data-ttu-id="999f2-165">Таким образом, этот уровень не должен принимать прямых зависимостей на инфраструктуру, это означает, что правило, ваши классы сущностей модели домена должно быть [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)s.</span><span class="sxs-lookup"><span data-stu-id="999f2-165">Therefore, this layer should not take direct dependencies on the infrastructure, which means that an important rule is that your domain model entity classes should be [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)s.</span></span>

<span data-ttu-id="999f2-166">На любой платформе инфраструктуры данных access как Entity Framework и NHibernate для сущности домена не должен прямой зависимости (например, для создания класса, производного от базового класса).</span><span class="sxs-lookup"><span data-stu-id="999f2-166">Domain entities should not have any direct dependency (like deriving from a base class) on any data access infrastructure framework like Entity Framework or NHibernate.</span></span> <span data-ttu-id="999f2-167">В идеальном случае сущностей домена не следует наследовать или реализации любого типа, определенного в любую платформу инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="999f2-167">Ideally, your domain entities should not derive from or implement any type defined in any infrastructure framework.</span></span>

<span data-ttu-id="999f2-168">Большинство современных ORM платформ, таких как Entity Framework Core разрешить этот подход, чтобы ваши классы модели домена не привязаны к инфраструктуре.</span><span class="sxs-lookup"><span data-stu-id="999f2-168">Most modern ORM frameworks like Entity Framework Core allow this approach, so that your domain model classes are not coupled to the infrastructure.</span></span> <span data-ttu-id="999f2-169">Однако наличие сущности POCO не всегда возможно при использовании определенных базах данных NoSQL и платформы, например, субъектами и надежного коллекций в Azure Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="999f2-169">However, having POCO entities is not always possible when using certain NoSQL databases and frameworks, like Actors and Reliable Collections in Azure Service Fabric.</span></span>

<span data-ttu-id="999f2-170">Даже в том случае, когда важно следуйте принципу сохраняемости для модели домена, не следует пропускать проблемы сохраняемости.</span><span class="sxs-lookup"><span data-stu-id="999f2-170">Even when it is important to follow the Persistence Ignorance principle for you Domain model, you should not ignore persistence concerns.</span></span> <span data-ttu-id="999f2-171">По-прежнему очень важно для понимания модели физических данных и как он сопоставляется объектной модели сущности.</span><span class="sxs-lookup"><span data-stu-id="999f2-171">It is still very important to understand the physical data model and how it maps to your entity object model.</span></span> <span data-ttu-id="999f2-172">В противном случае можно создать макеты невозможно.</span><span class="sxs-lookup"><span data-stu-id="999f2-172">Otherwise you can create impossible designs.</span></span>

<span data-ttu-id="999f2-173">Кроме того это не означает, можно воспользоваться моделью, разработанной для реляционной базы данных и непосредственно переместить NoSQL или базы данных с учетом документа.</span><span class="sxs-lookup"><span data-stu-id="999f2-173">Also, this does not mean you can take a model designed for a relational database and directly move it to a NoSQL or document-oriented database.</span></span> <span data-ttu-id="999f2-174">В некоторых моделях сущности подойдут модели, но обычно нет.</span><span class="sxs-lookup"><span data-stu-id="999f2-174">In some entity models, the model might fit, but usually it does not.</span></span> <span data-ttu-id="999f2-175">Все еще существуют ограничения, должен соответствовать модели сущности, основанная на технологии хранения и технологией ORM.</span><span class="sxs-lookup"><span data-stu-id="999f2-175">There are still constraints that your entity model must adhere to, based both on the storage technology and ORM technology.</span></span>

### <a name="the-application-layer"></a><span data-ttu-id="999f2-176">Уровень приложения</span><span class="sxs-lookup"><span data-stu-id="999f2-176">The application layer</span></span>

<span data-ttu-id="999f2-177">Переход к уровень приложения мы снова можно упоминаются Eric Evans книги [Domain Driven Design](http://domainlanguage.com/ddd/):</span><span class="sxs-lookup"><span data-stu-id="999f2-177">Moving on to the application layer, we can again cite Eric Evans's book [Domain Driven Design](http://domainlanguage.com/ddd/):</span></span>

<span data-ttu-id="999f2-178">**Уровень приложения:** определяет задания, предусмотренных для программного обеспечения с указанием объекты выразительный домена для работы проблем с.</span><span class="sxs-lookup"><span data-stu-id="999f2-178">**Application Layer:** Defines the jobs the software is supposed to do and directs the expressive domain objects to work out problems.</span></span> <span data-ttu-id="999f2-179">Задачи, за которые отвечает этим слоем, может применяться для бизнеса или необходимые для взаимодействия с уровней приложения из других систем.</span><span class="sxs-lookup"><span data-stu-id="999f2-179">The tasks this layer is responsible for are meaningful to the business or necessary for interaction with the application layers of other systems.</span></span> <span data-ttu-id="999f2-180">Этот уровень хранится тонкой.</span><span class="sxs-lookup"><span data-stu-id="999f2-180">This layer is kept thin.</span></span> <span data-ttu-id="999f2-181">Он не содержит бизнес-правила или набора знаний, но только задачи координаты и делегаты работать на совместную работу объектов домена в следующий уровень вниз.</span><span class="sxs-lookup"><span data-stu-id="999f2-181">It does not contain business rules or knowledge, but only coordinates tasks and delegates work to collaborations of domain objects in the next layer down.</span></span> <span data-ttu-id="999f2-182">Состояние, отражая состояние дел не существует, но он может иметь состояние, которое отражает ход выполнения задачи для пользователя или программы.</span><span class="sxs-lookup"><span data-stu-id="999f2-182">It does not have state reflecting the business situation, but it can have state that reflects the progress of a task for the user or the program.</span></span>

<span data-ttu-id="999f2-183">Часто микрослужбу уровня приложения .NET закодирован как проект веб-API ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="999f2-183">A microservice’s application layer in .NET is commonly coded as an ASP.NET Core Web API project.</span></span> <span data-ttu-id="999f2-184">Проект реализует микрослужбу взаимодействия, удаленный доступ к сети и внешних веб-API, используемый из пользовательского интерфейса или клиентских приложений.</span><span class="sxs-lookup"><span data-stu-id="999f2-184">The project implements the microservice’s interaction, remote network access, and the external Web APIs used from the UI or client apps.</span></span> <span data-ttu-id="999f2-185">Запросы включает в том случае, если с помощью CQRS подход команд, принимаемое микрослужбу и даже событиями связи между микрослужбами (события интеграции).</span><span class="sxs-lookup"><span data-stu-id="999f2-185">It includes queries if using a CQRS approach, commands accepted by the microservice, and even the event-driven communication between microservices (integration events).</span></span> <span data-ttu-id="999f2-186">Веб-API ASP.NET Core, представляющее уровень приложения не должны содержать бизнес-правила или набора знаний домена (особенно правила домена для обновления или транзакции); Эти должен принадлежать библиотеки классов модели домена.</span><span class="sxs-lookup"><span data-stu-id="999f2-186">The ASP.NET Core Web API that represents the application layer must not contain business rules or domain knowledge (especially domain rules for transactions or updates); these should be owned by the domain model class library.</span></span> <span data-ttu-id="999f2-187">Только координату должен слой приложения задач и не должно хранения или определить состояние любого домена (модель домена).</span><span class="sxs-lookup"><span data-stu-id="999f2-187">The application layer must only coordinate tasks and must not hold or define any domain state (domain model).</span></span> <span data-ttu-id="999f2-188">Он делегирует выполнение бизнес-правила для домена модели сами классы (статистические корни и сущностями домена), что в конечном итоге приведет к обновлению данных в этих сущностей домена.</span><span class="sxs-lookup"><span data-stu-id="999f2-188">It delegates the execution of business rules to the domain model classes themselves (aggregate roots and domain entities), which will ultimately update the data within those domain entities.</span></span>

<span data-ttu-id="999f2-189">По сути логика приложения — где реализовать все случаи использования, которые зависят от данного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="999f2-189">Basically, the application logic is where you implement all use cases that depend on a given front end.</span></span> <span data-ttu-id="999f2-190">Например реализация, относящиеся к службе веб-API.</span><span class="sxs-lookup"><span data-stu-id="999f2-190">For example, the implementation related to a Web API service.</span></span>

<span data-ttu-id="999f2-191">Целью является доменную логику в слой модели домена, его инварианты, модели данных и связанных бизнес-правил необходимо полностью независим от уровни представления и приложения.</span><span class="sxs-lookup"><span data-stu-id="999f2-191">The goal is that the domain logic in the domain model layer, its invariants, the data model, and related business rules must be completely independent from the presentation and application layers.</span></span> <span data-ttu-id="999f2-192">Чаще всего уровень модели домена не должен зависеть непосредственно любую платформу инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="999f2-192">Most of all, the domain model layer must not directly depend on any infrastructure framework.</span></span>

### <a name="the-infrastructure-layer"></a><span data-ttu-id="999f2-193">Уровень инфраструктуры</span><span class="sxs-lookup"><span data-stu-id="999f2-193">The infrastructure layer</span></span>

<span data-ttu-id="999f2-194">Уровень инфраструктуры — это способ сохранения в базах данных или другое постоянное хранилище данных, изначально содержатся в сущности домена (в памяти).</span><span class="sxs-lookup"><span data-stu-id="999f2-194">The infrastructure layer is how the data that is initially held in domain entities (in memory) is persisted in databases or another persistent store.</span></span> <span data-ttu-id="999f2-195">Пример использует Entity Framework Core код для реализации классов шаблон репозитория, использование класса DBContext для сохранения данных в реляционной базе данных.</span><span class="sxs-lookup"><span data-stu-id="999f2-195">An example is using Entity Framework Core code to implement the Repository pattern classes that use a DBContext to persist data in a relational database.</span></span>

<span data-ttu-id="999f2-196">В соответствии с ранее упомянутых [сохраняемости](http://deviq.com/persistence-ignorance/) и [пропуск инфраструктуры](https://ayende.com/blog/3137/infrastructure-ignorance) принципы уровня инфраструктуры должен не «повлиять» уровень модели домена.</span><span class="sxs-lookup"><span data-stu-id="999f2-196">In accordance with the previously mentioned [Persistence Ignorance](http://deviq.com/persistence-ignorance/) and [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) principles, the infrastructure layer must not “contaminate” the domain model layer.</span></span> <span data-ttu-id="999f2-197">Независимость от классов для модели сущности домена необходимо предотвратить инфраструктуру, которая используется для хранения данных (EF или любой другой структуре), не выполнив жестких зависимостей из платформ.</span><span class="sxs-lookup"><span data-stu-id="999f2-197">You must keep the domain model entity classes agnostic from the infrastructure that you use to persist data (EF or any other framework) by not taking hard dependencies on frameworks.</span></span> <span data-ttu-id="999f2-198">Библиотека классов слой модели домена должен иметь только ваш код домена, просто [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object) сущности классы, реализующие лежит в основе программного обеспечения и полностью отделен от технологий инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="999f2-198">Your domain model layer class library should have only your domain code, just [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object) entity classes implementing the heart of your software and completely decoupled from infrastructure technologies.</span></span>

<span data-ttu-id="999f2-199">Таким образом, слои или библиотек классов и проекты должны в конечном счете зависят от уровня модели домена (библиотека), наоборот, как показано на рисунке 9-7.</span><span class="sxs-lookup"><span data-stu-id="999f2-199">Thus, your layers or class libraries and projects should ultimately depend on your domain model layer (library), not vice versa, as shown in Figure 9-7.</span></span>

![](./media/image8.png)

<span data-ttu-id="999f2-200">**Рис. 9-7**.</span><span class="sxs-lookup"><span data-stu-id="999f2-200">**Figure 9-7**.</span></span> <span data-ttu-id="999f2-201">Зависимости между слоями DDD</span><span class="sxs-lookup"><span data-stu-id="999f2-201">Dependencies between layers in DDD</span></span>

<span data-ttu-id="999f2-202">Такая структура слой должен быть независимым для каждого микрослужбы.</span><span class="sxs-lookup"><span data-stu-id="999f2-202">This layer design should be independent for each microservice.</span></span> <span data-ttu-id="999f2-203">Как отмечалось ранее, вы можете реализовать самые сложные микрослужбами следующие шаблоны DDD при реализации более простой управляемой данными микрослужбами (простой CRUD в одном слое) проще.</span><span class="sxs-lookup"><span data-stu-id="999f2-203">As noted earlier, you can implement the most complex microservices following DDD patterns, while implementing simpler data-driven microservices (simple CRUD in a single layer) in a simpler way.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="999f2-204">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="999f2-204">Additional resources</span></span>

-   <span data-ttu-id="999f2-205">**DevIQ. Принцип пропуск сохраняемости**
    [*http://deviq.com/persistence-ignorance/*](http://deviq.com/persistence-ignorance/)</span><span class="sxs-lookup"><span data-stu-id="999f2-205">**DevIQ. Persistence Ignorance principle**
[*http://deviq.com/persistence-ignorance/*](http://deviq.com/persistence-ignorance/)</span></span>

-   <span data-ttu-id="999f2-206">**Oren Eini. Пропуск инфраструктуры**
    [*https://ayende.com/blog/3137/infrastructure-ignorance*](https://ayende.com/blog/3137/infrastructure-ignorance)</span><span class="sxs-lookup"><span data-stu-id="999f2-206">**Oren Eini. Infrastructure Ignorance**
[*https://ayende.com/blog/3137/infrastructure-ignorance*](https://ayende.com/blog/3137/infrastructure-ignorance)</span></span>

-   <span data-ttu-id="999f2-207">**Angel Lopez. Многоуровневая архитектура в разработки на основе домена**
    [*https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/*](https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/)</span><span class="sxs-lookup"><span data-stu-id="999f2-207">**Angel Lopez. Layered Architecture In Domain-Driven Design**
[*https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/*](https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="999f2-208">[Предыдущие] (cqrs микрослужбу reads.md) [Далее] (model.md микрослужбу домена)</span><span class="sxs-lookup"><span data-stu-id="999f2-208">[Previous] (cqrs-microservice-reads.md) [Next] (microservice-domain-model.md)</span></span>
---
title: Хранилища экземпляров
ms.date: 03/30/2017
ms.assetid: f2629668-0923-4987-b943-67477131c1e0
ms.openlocfilehash: 7ea29c3604042d773590448e31ce4ea95125ca1f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519582"
---
# <a name="instance-stores"></a>Хранилища экземпляров
Хранилище экземпляров - это логический контейнер для экземпляров. Здесь хранятся данные и метаданные экземпляра. Хранилище экземпляров не предполагает выделения физического пространства. Хранилище экземпляра может содержать постоянные сведения в базе данных SQL Server или непостоянные сведения о состоянии в памяти. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] поставляется с хранилищем экземпляров рабочего процесса SQL - конкретной реализацией хранилища экземпляров, которая позволяет рабочему процессу хранить данные и метаданные в базе данных SQL Server 2005 или SQL Server 2008. Кроме того, Windows Server App Fabric также предоставляет конкретную реализацию хранилища экземпляров. Дополнительные сведения см. в разделе [Windows Server App Fabric экземпляр Store, запрос и поставщики управления](https://go.microsoft.com/fwlink/?LinkID=201201&clcid=0x409).  
  
 API сохраняемости - это интерфейс между узлом и хранилищем экземпляров, позволяющим узлу отправлять запросы на команды (например, <xref:System.Activities.DurableInstancing.LoadWorkflowCommand> и <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>) в хранилище экземпляров. Конкретная реализация данного API-интерфейса называется поставщиком сохраняемости. Поставщик сохраняемости получает запросы от узла и изменяет хранилище экземпляров.  
  
 Узлы и хранилища экземпляров являются подключаемыми; узел можно использовать с несколькими хранилищами экземпляров, хранилище экземпляров можно использовать с несколькими узлами. Хранилище экземпляров обычно оптимизируется под шаблоны использования определенного узла, хотя хранилище экземпляров и узел могут обрести независимые жизненные циклы. Например **WorkflowServiceHost** и **SqlWorkflowInstanceStore** предназначены для эффективной совместной работы. Можно создать свое собственное хранилище экземпляров для сохранения данных и метаданных экземпляров службы рабочего процесса и использовать это хранилище экземпляров с **WorkflowServiceHost**. Например, можно создать хранилище OracleWorkflowInstanceStore, позволяющее рабочему процессу хранить данные в базе данных Oracle, а не в базе данных SQL Server.  
  
 Узлы обычно снабжаются дополнительными функциями, которые модифицируют сохраненные объекты. Например в системе хранения экземпляров может иметь узел рабочего процесса, расширение, поддерживающее операцию «Suspend» и в хранилище экземпляров SQL.  Узел рабочего процесса может отправить стандартную команду, например «Save» или «Load», для сохранения рабочего процесса в хранилище экземпляров или для его загрузки соответственно. Расширение для приостановки может добавить командам сохранения или загрузки экземпляров рабочего процесса такую дополнительную семантику, что приостановленный экземпляр рабочего процесса нельзя будет загрузить. Поставщик сохраняемости для хранилища экземпляров SQL понимает команды сохранения или загрузки экземпляров рабочего процесса и применяет команды путем вызова соответствующих хранимых процедур, которые вносят изменения в таблицы сохраненных объектов в базе данных SQL Server.  
  
 В хранилище экземпляров узел является владельцем экземпляра. Одновременно узел может владеть несколькими экземплярами из нескольких разных хранилищ. Узел предоставляет идентификаторы GUID для ключей экземпляров, связанных с экземплярами. Ключ экземпляра - уникальный псевдоним, определяющий экземпляр. Система сохраняемости создает, обновляет и удаляет сведения о владельце экземпляра, когда выполняет команды, запрошенные узлами.  
  
 Следующий список содержит важные этапы взаимодействия узла с хранилищем экземпляров.  
  
1.  Получить **InstanceStore** от поставщика сохраняемости.  

2.  Получите дескриптор экземпляра путем вызова <xref:System.Runtime.DurableInstancing.InstanceStore.CreateInstanceHandle%2A> метод **InstanceStore**.  
  
3.  Вызовите команды для дескриптор экземпляра путем вызова <xref:System.Runtime.DurableInstancing.InstanceStore.Execute%2A> метод **InstanceStore**.  
  
4.  Изучите <xref:System.Runtime.DurableInstancing.InstanceView> возвращаемые **InstanceStore.Execute** чтобы определить результаты команд.

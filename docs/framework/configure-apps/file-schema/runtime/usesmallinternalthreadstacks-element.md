---
title: '&lt;UseSmallInternalThreadStacks&gt; элемент'
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 23a38297526090f1df35f8541026accd5a5cb9bc
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613795"
---
# <a name="ltusesmallinternalthreadstacksgt-element"></a>&lt;UseSmallInternalThreadStacks&gt; элемент
Запросы, что сокращает общеязыковой среды выполнения (CLR) используют путем указания явных размеров стека при создании определенных потоков, используемых для внутренних целей, вместо размер стека по умолчанию для этих потоков.  
  
 \<Конфигурация > элемент  
\<Среда выполнения > элемент  
\<UseSmallInternalThreadStacks > элемент  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|enabled|Обязательный атрибут.<br /><br /> Признак запроса, CLR использования явных размеров стека вместо размер стека по умолчанию при создании определенных потоков, используемых для внутренних целей. Явных размеров стека имеют меньший размер, чем размер стека по умолчанию 1 МБ.|  
  
## <a name="enabled-attribute"></a>Атрибут enabled  
  
|Значение|Описание:|  
|-----------|-----------------|  
|true|Запросите явных размеров стека.|  
|False|Используйте размер стека по умолчанию. Это значение по умолчанию для [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|`configuration`|Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.|  
|`runtime`|Содержит сведения о привязке сборок и сборке мусора.|  
  
## <a name="remarks"></a>Примечания  
 Этот элемент конфигурации используется для запроса Использование ограниченной виртуальной памяти в процессе, поскольку явные размеры потоков, которые среда CLR использует для своих внутренних потоков, если запрос выполняется, меньше, чем размер по умолчанию.  
  
> [!IMPORTANT]
>  Этот элемент конфигурации — это запрос на CLR, а не является обязательным требованием. В [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], запрос выполняется только для x86 архитектуры. Этот элемент может полностью обрабатывается в будущих версиях среды CLR или заменены явных размеров стека, которые всегда используются для выбранного внутренних потоков.  
  
 Указание данного элемента конфигурации меняет надежность для меньшего использования виртуальной памяти, если среда CLR учитывает запрос, так как меньшие размеры стека могут сделать стек переполнения более вероятно.  
  
## <a name="example"></a>Пример  
 Приведенный ниже показано, как для запроса, что CLR использования явных размеров стека для определенных потоков, используемых для внутренних целей.  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>См. также  
- [Схема параметров среды выполнения](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [Схема файла конфигурации](../../../../../docs/framework/configure-apps/file-schema/index.md)

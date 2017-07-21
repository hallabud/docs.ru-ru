---
title: "Безопасность сообщений в WCF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a80efb59-591a-4a37-bb3c-8fffa6ca0b7d
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Безопасность сообщений в WCF
В [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] имеется два основных режима для обеспечения безопасности \(`Transport` и `Message`\), а также третий режим \(`TransportWithMessageCredential`\), объединяющий в себе два предыдущих.В данном разделе рассматривается безопасность сообщения и причины для ее использования.  
  
## Что такое безопасность сообщения?  
 Безопасность сообщения использует спецификацию WS\-Security для защиты сообщений.В спецификации WS\-Security описываются дополнения к обмену сообщениями по протоколу SOAP, обеспечивающие конфиденциальность, целостность и проверку подлинности на уровне сообщений SOAP \(вместо транспортного уровня\).  
  
 Вкратце, безопасность сообщений отличается от безопасности транспорта тем, что учетные данные и утверждения безопасности инкапсулированы в каждое сообщение вместе с любой защитой сообщения \(подпись или шифрование\).Применение защиты непосредственно к сообщению с помощью изменения его содержимого позволяет защищенному сообщению быть самосодержащим в отношении аспектов безопасности.Это позволяет использовать некоторые сценарии, которые были невозможны в случае безопасности транспорта.  
  
## Причина для использования безопасности сообщения  
 В безопасности на уровне сообщения вся информация безопасности инкапсулирована внутри сообщения.Защита сообщения с помощью безопасности на уровне сообщения вместо защиты на транспортном уровне имеет следующие преимущества.  
  
-   Сквозная безопасность.Средства обеспечения безопасности транспорта, например протокол SSL, обеспечивают защиту только для соединения «точка\-точка».Если перед тем, как попасть к конечному получателю SOAP, сообщение проходит через один или несколько посредников \(например через маршрутизатор\), оно не будет защищено, когда посредник считывает его из потока.Кроме того, сведения проверки подлинности доступны только первому посреднику, поэтому, если необходимо, они должны передаваться конечному получателю вне потока.Это относится даже к сценариям, где на всем маршруте между отдельными прыжками используется безопасность SSL.Поскольку безопасность сообщения действует непосредственно в сообщении и защищает код XML в нем, защита обеспечивается вне зависимости от количества посредников, используемых для передачи сообщения конечному получателю.Это обеспечивает по\-настоящему сквозную безопасность.  
  
-   Повышенная гибкость.Можно подписывать части сообщения, а не только все сообщение.Это означает, что посредники могут просматривать части сообщения, предназначенные для них.Если отправителю необходимо сделать часть информации в сообщении видимой для посредников, но защитить ее от подделки, для этого достаточно подписать эту часть, но не зашифровывать ее.Поскольку подпись является частью сообщения, конечный получатель может проверить, что полученная информация в сообщении не была изменена.В одном из сценариев возможно использование службы посредника SOAP, которая направляет сообщение в соответствии со значением заголовка действия.По умолчанию в [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] значение действия не шифруется, но подписывается, если используется безопасность сообщения.Поэтому данная информация доступна всем посредникам, но не один из них не может изменить ее.  
  
-   Поддержка нескольких транспортов.Можно отправлять защищенные сообщения с помощью различных транспортов, таких как именованные каналы и TCP. При этом нет необходимости задействовать протокол для обеспечения безопасности.В случае с безопасностью на уровне транспорта вся информация безопасности действует в подключении транспорта и не доступна из содержимого самого сообщения.Безопасность сообщения обеспечивает защиту вне зависимости от того, какой транспорт используется для передачи, и контекст безопасности внедряется непосредственно в сообщение.  
  
-   Поддержка широкого набора учетных данных и утверждений.Безопасность сообщения основывается на спецификации WS\-Security, обеспечивающей расширяемую инфраструктуру для передачи любого типа утверждения внутри сообщения SOAP.В отличие от безопасности транспорта, набор механизмов проверки подлинности или утверждений не ограничен возможностями транспорта.В [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] безопасность передачи сообщений обеспечивается несколькими типами проверки подлинности и механизмами передачи утверждений, при необходимости можно добавить другие средства обеспечения безопасности.По этой причине сценарий с участием федеративных учетных данных невозможен без обеспечения защищенности сообщения.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] о федеративных сценариях, поддерживаемых WCF, см. в разделе [Федерация и выданные маркеры](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## Сравнение безопасности сообщений и транспорта  
  
### Преимущества и недостатки безопасности на транспортном уровне  
 Безопасность транспорта имеет следующие преимущества.  
  
-   Для взаимодействующих сторон не требуется поддержка принципов безопасности на уровне XML.Например, это позволяет улучшить взаимодействие при использовании протокола HTTPS для защиты связи.  
  
-   Общее повышение производительности.  
  
-   Наличие аппаратных ускорителей.  
  
-   Возможность потоковой передачи.  
  
 Безопасность транспорта имеет следующие недостатки.  
  
-   Доступна только между прыжками.  
  
-   Ограниченный и не расширяемый набор учетных данных.  
  
-   Зависимость от транспорта.  
  
### Недостатки безопасности на уровне сообщений  
 Безопасность сообщения имеет следующие недостатки.  
  
-   Производительность.  
  
-   Не поддерживается потоковая передача сообщений.  
  
-   Требуется реализация механизмов безопасности на уровне XML и поддержка спецификации WS\-Security.Это может повлиять на взаимодействие.  
  
## См. также  
 [Защита служб и клиентов](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [Безопасность транспорта](../../../../docs/framework/wcf/feature-details/transport-security.md)   
 [Как использовать средства обеспечения безопасности транспорта и учетные данные сообщения](../../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)   
 [Шаблоны и примеры Microsoft, глава 3: "Реализация безопасности на уровне транспорта и сообщений"](http://go.microsoft.com/fwlink/?LinkId=88897)
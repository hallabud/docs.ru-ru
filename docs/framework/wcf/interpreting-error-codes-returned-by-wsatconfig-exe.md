---
title: "Интерпретация кодов ошибок, возвращаемых wsatConfig.exe | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ab65f22b-0d69-4c21-9aaf-74acef0ca102
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Интерпретация кодов ошибок, возвращаемых wsatConfig.exe
В данном разделе перечисляются все коды ошибок, создаваемые программой настройки WS\-AtomicTransaction \(wsatConfig.exe\), и описываются действия, которые рекомендуется выполнить в каждом случае.  
  
## Список кодов ошибок  
  
|Код ошибки|Описание|Рекомендуемое действие|  
|----------------|--------------|----------------------------|  
|0|Операция выполнена успешно.|Нет|  
|1|Непредвиденная ошибка.|Обратитесь в Майкрософт.|  
|2|При попытке обратиться к координатору MSDTC с целью извлечения его параметров безопасности произошла непредвиденная ошибка.|Убедитесь в том, что служба MSDTC не отключена, и попытайтесь решить все проблемы, описанные в возвращенном исключении.|  
|3|Учетная запись, от имени которой выполнялся WsatConfig.exe, не имела необходимых разрешений для чтения параметров сетевой безопасности.|Выполните файл WsatConfig.exe от имени учетной записи администратора.|  
|4|Прежде чем пытаться включить поддержку WS\-AT включите "сетевой доступ DTC" для координатора MSDTC.|Включите "сетевой доступ DTC" для координатора MSDTC и повторно запустите программу.|  
|5|Порт, в который был выполнен вход, находился вне диапазона.Значение должно находиться в диапазоне от 1 до 65535.|Исправьте параметр командной строки `-port:<portNum>`,<br /><br /> как указано в сообщении об ошибке.|  
|6|В командной строке был задан недействительный сертификат конечной точки.Не удалось найти сертификат, или сертификат не прошел проверку.|Исправьте параметр командной строки `-endpointCert`.Убедитесь, что сертификат имеет закрытый ключ, предназначен для использования как в ClientAuthentication, так и в ServerAuthentication, установлен в хранилище сертификатов LocalMachine\\MY и является полностью доверенным.|  
|7|В командной строке был задан недействительный сертификат учетных записей.|Исправьте параметр командной строки `-accountsCerts`.Указанный сертификат был задан неверно, либо его не удалось найти.|  
|8|Время ожидания по умолчанию было задано вне диапазона от 1 до 3600 секунд.|Укажите значение времени ожидания по умолчанию, как указано.|  
|10|При попытке получения доступа к реестру возникла непредвиденная ошибка.|Проверьте сообщение об ошибке и код ошибки на наличие элементов, с которыми можно произвести какие\-либо действия.|  
|11|Не удается произвести запись в реестр.|Убедитесь, что ключ, указанный в сообщении об ошибке, поддерживает доступ к реестру той учетной записи, от имени которой был выполнен файл WsatConfig.exe.|  
|12|При попытке получения доступа к хранилищу сертификатов возникла непредвиденная ошибка.|Используйте возвращенный код ошибки для сопоставления с соответствующей системной ошибкой.|  
|13|Сбой конфигурации http.sys.Не удается создать новое резервирование HTTPS\-порта для MSDTC.|Используйте возвращенный код ошибки для сопоставления с соответствующей системной ошибкой.|  
|14|Сбой конфигурации http.sys.Не удается удалить предыдущее резервирование HTTPS\-порта для MSDTC.|Используйте возвращенный код ошибки для сопоставления с соответствующей системной ошибкой.|  
|15|Сбой конфигурации http.sys.Предыдущее резервирование HTTPS\-порта уже существует для указанного порта.|Другое приложение уже стало владельцем данного порта.Используйте другой порт либо удалите или перенастройте текущее приложение.|  
|16|Сбой конфигурации http.sys.Не удается привязать указанный сертификат к порту.|Используйте возвращенный в сообщении об ошибке код ошибки для сопоставления с соответствующей системной ошибкой.|  
|17|Сбой конфигурации http.sys.Не удается отменить привязку SSL\-сертификата к предыдущему порту.|Используйте возвращенный в сообщении об ошибке код ошибки для сопоставления с соответствующей системной ошибкой.При необходимости для удаления ошибочных резервирований порта используйте файл httpcfg.exe или netsh.exe.|  
|18|Сбой конфигурации http.sys.Не удается привязать указанный сертификат к порту, так как предыдущая SSL\-привязка уже существует.|Другое приложение уже стало владельцем данного порта.Используйте другой порт либо удалите или перенастройте текущее приложение.|  
|19|Ошибка перезапуска MSDTC.|При необходимости перезапустите MSDTC вручную.Если проблема повторится, обратитесь в Майкрософт.|  
|20|Платформа [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] не установлена на удаленном компьютере или установлена неверно.|Установите на компьютере [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)].|  
|21|Сбой удаленной конфигурации из\-за превышения времени ожидания операции.|Вызов настройки WS\-AT на удаленном компьютере должен продолжаться более 90 секунд.|  
|22|Платформа [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] не установлена на удаленном компьютере или установлена неверно.|Установите на компьютере [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)].|  
|23|Сбой удаленной настройки из\-за исключения на удаленном компьютере.|Проверьте сообщение об ошибке на наличие элементов, с которыми можно произвести какие\-либо действия.|  
|26|Файлу WsatConfig.exe передан недопустимый аргумент.|Проверьте командную строку на наличие ошибок.|  
|27|Недопустимый параметр командной строки `-accounts`.|Исправьте параметр командной строки \-`accounts`, чтобы правильно задать учетную запись пользователя.|  
|28|Недопустимый параметр командной строки `-network`.|Исправьте параметр командной строки `-network`, чтобы правильно задать значения "включить" или "отключить".|  
|29|Недопустимый параметр командной строки `-maxTimeout`.|Исправьте параметр командной строки `-maxTimeout`, как указано.|  
|30|Недопустимый параметр командной строки `-timeout`.|Исправьте параметр командной строки `-timeout`, как указано.|  
|31|Недопустимый параметр командной строки `-traceLevel`.|Исправьте параметр командной строки `-traceLevel`, чтобы задать допустимое значение из списка ниже:<br /><br /> -   Off<br />-   Ошибка<br />-   Critical<br />-   Предупреждение<br />-   Information<br />-   Verbose<br />-   Все|  
|32|Недопустимый параметр командной строки `-traceActivity`.|Исправьте параметр командной строки `-traceActivity`, задав значение enable или disable.|  
|33|Недопустимый параметр командной строки `-traceProp`.|Исправьте параметр командной строки `-traceProp`, задав значение enable или disable.|  
|34|Недопустимый параметр командной строки `-tracePII`.|Исправьте параметр командной строки `-tracePII`, задав значение enable или disable.|  
|37|Файлу WsatConfig.exe не удалось определить точный сертификат компьютера.Обычно это происходит при наличии нескольких кандидатов или их полном отсутствии.|Задайте отпечаток сертификата или пару Issuer\\SubjectName, чтобы правильно определить точный сертификат для настройки.|  
|38|Процесс или пользователь не обладает достаточными разрешениями для изменения конфигурации межсетевого экрана.|Выполните файл WsatConfig.exe от имени учетной записи администратора.|  
|39|В файле WsatConfig.exe возникла ошибка при обновлении конфигурации межсетевого экрана.|Проверьте сообщение об ошибке на наличие элементов, с которыми можно произвести какие\-либо действия.|  
|40|Файлу WsatConfig.exe не удалось предоставить MSDTC доступ на чтение файла закрытого ключа сертификата.|Выполните файл WsatConfig.exe от имени учетной записи администратора.|  
|41|Не удалось найти установку [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)], либо найденная версия не может быть настроена с помощью данного средства.|Убедитесь, что платформа [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] установлена правильно и используйте для настройки WS\-AT только средство WsatConfig.exe, поставляемое с соответствующей версией [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)].|  
|42|В командной строке несколько раз указан один и тот же аргумент.|При выполнении файла WsatConfig.exe указывайте каждый аргумент однократно.|  
|43|Файлу WsatConfig.exe не удается обновить параметры WS\-AT, если WS\-AT не включена.|Укажите `-network:enable` в качестве дополнительного аргумента командной строки.|  
|44|Отсутствует необходимое исправление, и не удается настроить WS\-AT до установки этого исправления.|Инструкции по установке необходимого исправления см. в заметках о выпуске [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)].|  
|45|Недопустимый параметр командной строки `-virtualServer`.|Исправьте параметр командной строки `-virtualServer`, задав сетевое имя ресурса кластера, в котором необходимо произвести настройку.|  
|46|При попытке запустить сеанс трассировки событий Windows произошла непредвиденная ошибка.|Используйте возвращенный код ошибки для сопоставления с соответствующей системной ошибкой.|  
|47|Процесс или пользователь не обладает достаточными разрешениями для включения сеанса трассировки событий Windows.|Выполните файл WsatConfig.exe от имени учетной записи администратора.|  
|48|При попытке запустить сеанс трассировки событий Windows произошла непредвиденная ошибка.|Обратитесь в Майкрософт.|  
|49|Не удается создать новый файл журнала, так как на %systemdrive% недостаточно места.|Убедитесь, что на %systemdrive% достаточно места для файла журнала.|  
|51|При попытке запустить сеанс трассировки событий Windows произошла непредвиденная ошибка.|Обратитесь в Майкрософт.|  
|52|При попытке запустить сеанс трассировки событий Windows произошла непредвиденная ошибка.|Обратитесь в Майкрософт.|  
|53|Не удалось создать резервную копию файла журнала предыдущего сеанса трассировки событий Windows.|Убедитесь, что на %systemdrive% достаточно места для файла журнала и резервной копии предыдущего файла журнала \(если таковой имеется\).При необходимости удалите предыдущий файл журнала вручную.|  
|55|При попытке запустить сеанс трассировки событий Windows произошла непредвиденная ошибка.|Обратитесь в Майкрософт.|  
|56|При попытке запустить сеанс трассировки событий Windows произошла непредвиденная ошибка.|Обратитесь в Майкрософт.|  
  
## См. также  
 [Программа конфигурации WS\-AtomicTransaction \(wsatConfig.exe\)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
---
title: Службы WCF и средство отслеживания событий для Windows
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: 100f9c0ce71eedaa4061fc894521597074b21b00
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198293"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a>Службы WCF и средство отслеживания событий для Windows
Этот образец демонстрирует использование аналитического отслеживания в Windows Communication Foundation (WCF) для передачи событий в Windows (Трассировка событий). Аналитические трассировки — это события, возникающие в ключевых точках стека WCF, позволяющие отлаживать службы WCF в рабочей среде.

 Трассировка аналитического отслеживания в службах WCF, которая может быть включен в рабочей среде с минимальным влиянием на производительность. Отслеживаемые события передаются в сеанс трассировки событий Windows.

 Этот пример включает базовой службы WCF, в котором они выдаются из службы в журнал событий, который можно просмотреть с помощью средства просмотра событий. Можно также запустить выделенный сеанс ETW, который прослушивает события из службы WCF. Данный образец включает скрипт для создания выделенного сеанса трассировки событий Windows, хранящего события в двоичном файле, который можно прочесть с помощью средства просмотра событий.

#### <a name="to-use-this-sample"></a>Использование этого образца

1.  С помощью Visual Studio 2012, откройте файл решения EtwAnalyticTraceSample.sln.

2.  Для построения решения нажмите CTRL+SHIFT+B.

3.  Чтобы запустить решение, нажмите клавиши CTRL+F5.

     В веб-браузере, щелкните **Calculator.svc**. В браузере должен появиться URI WSDL-документа для службы. Скопируйте этот URI.

     По умолчанию служба начинает прослушивание запросов на порту 1378 `http://localhost:1378/Calculator.svc`.

4.  Запустите тестовый клиент WCF (WcfTestClient.exe).

     Тестовый клиент WCF (WcfTestClient.exe) расположен в `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.  Каталог установки Visual Studio 2012 по умолчанию является `C:\Program Files\Microsoft Visual Studio 10.0`.

5.  В тестовом клиенте WCF, добавьте службу, выбрав **файл**, а затем **добавить службу**.

     Добавьте адрес конечной точки в поле ввода. Значение по умолчанию — `http://localhost:1378/Calculator.svc`.

6.  Откройте приложение просмотра событий.

     Перед запуском службы запустите средство просмотра событий и убедитесь, что в журнал событий прослушивает событий отслеживания от службы WCF.

7.  Из **запустить** меню, выберите **Администрирование**, а затем **средство просмотра событий**.  Включить **аналитический** и **Отладка** журналы.

8.  В представлении в виде дерева в средстве просмотра событий перейдите к **средство просмотра событий**, **журналы приложений и служб**, **Microsoft**, **Windows**, а затем **Сервер приложений-приложения**. Щелкните правой кнопкой мыши **Application Server-Applications**выберите **представление**, а затем **Отобразить аналитический и отладочный журналы**.

     Убедитесь, что **Отобразить аналитический и отладочный журналы** флажок.

9. Включить **аналитический** журнала.

     В представлении в виде дерева в средстве просмотра событий перейдите к **средство просмотра событий**, **журналы приложений и служб**, **Microsoft**, **Windows**, а затем **Сервер приложений-приложения**. Щелкните правой кнопкой мыши **аналитический** и выберите **включить журнал**.

#### <a name="to-test-the-service"></a>Проверка службы

1.  Вернитесь в тестовом клиенте WCF и дважды щелкните `Divide` и сохраните значения по умолчанию, в которых задано нулевое значение знаменателя 0.

     Если знаменатель равен 0, служба выдает ошибку.

2.  Просмотрите события, переданные из службы.

     Вернитесь в средство просмотра событий и перейдите к окну **средство просмотра событий**, **журналы приложений и служб**, **Microsoft**, **Windows**, а затем **Сервер приложений-приложения**. Щелкните правой кнопкой мыши **аналитический** и выберите **обновить**.

     События аналитического отслеживания WCF отображаются в средстве просмотра событий. Обратите внимание, что для возникшей ошибки в средстве просмотра событий отображается событие аналитического отслеживания.

3.  Повторите шаги 1 и 2, используя уже допустимые входные значения. Значением параметра `N2` может быть любое число, отличное от 0.

     Обновите канал аналитики, чтобы убедиться, что события WCF не включают событий, связанных с ошибкой.

 Образец иллюстрирует передачу событий аналитического отслеживания из службы WCF.

#### <a name="to-cleanup-optional"></a>Очистка (необязательно)

1.  Откройте средство просмотра событий.

2.  Перейдите к **средство просмотра событий**, **журналы приложений и служб**, **Microsoft**, **Windows**, а затем  **Application-Server-Applications**. Щелкните правой кнопкой мыши **аналитический** и выберите **отключить журнал**.

3.  Перейдите к **средство просмотра событий**, **журналы приложений и служб**, **Microsoft**, **Windows**, а затем  **Application-Server-Applications**. Щелкните правой кнопкой мыши **аналитический** и выберите **очистить журнал**.

4.  Выберите **снимите** параметр, чтобы удалить события.

> [!IMPORTANT]
>  Образцы уже могут быть установлены на компьютере. Перед продолжением проверьте следующий каталог (по умолчанию).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры. Этот образец расположен в следующем каталоге.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a>См. также  
 [Образцы наблюдения за AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)

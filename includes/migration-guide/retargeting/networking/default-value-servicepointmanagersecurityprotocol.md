### <a name="default-value-of-servicepointmanagersecurityprotocol-is-securityprotocoltypesystemdefault"></a>Значение по умолчанию ServicePointManager.SecurityProtocol — SecurityProtocolType.System.Default

|   |   |
|---|---|
|Подробные сведения|Начиная с приложений, ориентированных на .NET Framework 4.7, свойство <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> имеет значение <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType>. Это изменение позволяет сетевым API-интерфейсам .NET Framework на основе SslStream (таких как FTP, HTTPS и SMTP) наследовать протоколы безопасности по умолчанию из операционной системы вместо использования жестко запрограммированных значений, определенных в .NET Framework. Значение по умолчанию зависит от операционной системы и пользовательской настройки, выполненной системным администратором. Сведения о протоколе SChannel по умолчанию в каждой версии операционной системы Windows см. в разделе [Протоколы TLS/SSL (Schannel SSP)](https://msdn.microsoft.com/library/windows/desktop/mt808159.aspx). Для приложений, предназначенных для более ранней версии платформы .NET Framework, значение свойства <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> по умолчанию зависит от целевой версии платформы .NET Framework. Дополнительные сведения см. в разделе [Изменение целевой платформы для миграции с .NET Framework 4.5.2 на 4.6](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#networking).|
|Предложение|Это изменение затрагивает приложения, предназначенные для .NET Framework 4.7 или более поздней версии. Если вы предпочитаете использовать определенный протокол, а не полагаться на системный объект по умолчанию, можно явно задать значение свойства <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType>. Если это изменение нежелательно, его можно отключить, добавив параметр конфигурации в раздел [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) файла конфигурации приложения. В следующем примере показан как раздел <code>&lt;runtime&gt;</code>, так и параметр отключения <code>Switch.System.Net.DontEnableSystemDefaultTlsVersions</code>:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableSystemDefaultTlsVersions=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Область|Дополнительный номер|
|Версия|4.7|
|Тип|Изменение целевой платформы|
|Затронутые API|<ul><li><xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType></li></ul>|

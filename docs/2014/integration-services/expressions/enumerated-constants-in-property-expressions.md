---
title: Costanti enumerate in espressioni di proprietà | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- enumerators [Integration Services]
- packages [Integration Services], expressions
- dynamic properties
- updating package properties
- enumerated constants [Integration Services]
- property expressions [Integration Services]
ms.assetid: a4418315-38e2-4ad3-8784-576163b25d6f
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d000c77263a0448ff838bff42a5020b86a299a72
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37221831"
---
# <a name="enumerated-constants-in-property-expressions"></a>Costanti enumerate in espressioni di proprietà
  Nelle espressioni di proprietà che includono valori di un elenco di membri di un enumeratore è necessario utilizzare i valori numerici dei membri dell'enumeratore, anziché i relativi nomi descrittivi. Ad esempio, se un'espressione che imposta il `LoggingMode` proprietà, è necessario usare il valore numerico 2 anziché il nome descrittivo Disabled.  
  
 In questo argomento vengono elencati solo i valori numerici equivalenti ai nomi descrittivi degli enumeratori i cui membri vengono comunemente utilizzati nelle espressioni di proprietà. Nel modello a oggetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sono inclusi numerosi enumeratori aggiuntivi che è possibile usare durante la programmazione del modello a oggetti per la compilazione di pacchetti a livello di programmazione o per la creazione di elementi di pacchetto con codice personalizzato, quali attività e componenti dei flussi di dati.  
  
 Oltre alle proprietà personalizzate dei pacchetti e degli oggetti di pacchetto, nella finestra Proprietà di [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] è incluso un set di proprietà disponibili per pacchetti, attività e contenitori Ciclo Foreach, Ciclo For e Sequenza. Le proprietà comuni impostate tramite valori di enumeratori, ovvero `ForceExecutionResult`, `LoggingMode`, `IsolationLevel` e `Transaction Option`, sono elencate nella sezione Proprietà comuni.  
  
 Nelle sezioni seguenti vengono fornite informazioni sulle costanti enumerate:  
  
 [Pacchetto](#Package)  
  
 [Enumeratori per il ciclo Foreach](#Foreach)  
  
 [Attività](#Tasks)  
  
 [Attività Piano di manutenzione](#MaintenancePlanTasks)  
  
 [Proprietà comuni](#CommonProperties)  
  
##  <a name="Package"></a> Pacchetto  
 Nelle tabelle seguenti vengono elencati i nomi descrittivi e i valori numerici equivalenti per le proprietà dei pacchetti che è possibile impostare utilizzando i valori di un enumeratore.  
  
 `PackageType` proprietà: impostata usando i valori di `DTSPackageType` enumerazione.  
  
|Nome descrittivo in DTSPackageType|Valore numerico|  
|-------------------------------------|-------------------|  
|Default|0|  
|DTSWizard|1|  
|DTSDesigner|2|  
|SQLReplication|3|  
|DTSDesigner100|5|  
|SQLDBMaint|6|  
  
 `CheckpointUsage` proprietà: impostata usando i valori di `DTSCheckpointUsage` enumerazione.  
  
|Nome descrittivo in DTSCheckpointUsage|Valore numerico|  
|-----------------------------------------|-------------------|  
|Never|0|  
|IfExists|1|  
|Always|2|  
  
 `PackagePriorityClass` proprietà: impostata usando i valori di `DTSPriorityClass` enumerazione.  
  
|Nome descrittivo in DTSPriorityClass|Valore numerico|  
|---------------------------------------|-------------------|  
|Default|0|  
|AboveNormal|1|  
|Normal|2|  
|BelowNormal|3|  
|Idle|4|  
  
 `ProtectionLevel` proprietà: impostata usando i valori di `DTSProtectionLevel` enumerazione.  
  
|Nome descrittivo in DTSProtectionLevel|Valore numerico|  
|-----------------------------------------|-------------------|  
|DontSaveSensitive|0|  
|EncryptSensitiveWithUserKey|1|  
|EncryptSensitiveWithPassword|2|  
|EncryptAllWithPassword|3|  
|EncryptAllWithUserKey|4|  
|ServerStorage|5|  
  
##  <a name="PrecedenceConstraints"></a> Vincoli di precedenza  
 `EvalOp` proprietà: impostata usando i valori di `DTSPrecedenceEvalOp` enumerazione.  
  
|Nome descrittivo in DTSPrecedenceEvalOp|Valore numerico|  
|------------------------------------------|-------------------|  
|Espressione|1|  
|Vincolo|2|  
|ExpressionAndConstraint|3|  
|ExpressionOrConstraint|4|  
  
 `Value` proprietà: impostata usando i valori di `DTSExecResult` enumerazione.  
  
|Nome descrittivo|Valore numerico|  
|-------------------|-------------------|  
|Esito positivo|0|  
|Failure|1|  
|Completion|2|  
|Canceled|3|  
  
##  <a name="Foreach"></a> Enumeratori per il ciclo Foreach  
 Il ciclo Foreach include un set di enumeratori con proprietà che possono essere impostate tramite espressioni di proprietà.  
  
### <a name="foreach-ado-enumerator"></a>Foreach ADO Enumerator  
 `Type` proprietà: impostata usando i valori di `ADOEnumerationType` enumerazione.  
  
|Nome descrittivo in ADOEnumerationType|Valore numerico|  
|-----------------------------------------|-------------------|  
|EnumerateTables|0|  
|EnumerateAllRows|1|  
|EnumerateRowsInFirstTable|2|  
  
### <a name="foreach-nodelist-enumerator"></a>Enumeratore Foreach Nodelist  
 `SourceDocumentType`, `InnerXPathStringSourceType`, e **OuterXPathStringSourceType** delle proprietà: impostata usando i valori di `SourceType` enumerazione.  
  
|Nome descrittivo in SourceType|Valore numerico|  
|---------------------------------|-------------------|  
|FileConnection|0|  
|Variabile|1|  
|DirectInput|2|  
  
 `EnumerationType` proprietà: impostata usando i valori di `EnumerationType` enumerazione.  
  
|Nome descrittivo in EnumerationType|Valore numerico|  
|--------------------------------------|-------------------|  
|Navigator|0|  
|Node|1|  
|NodeText|2|  
|ElementCollection|3|  
  
 `InnerElementType` proprietà: impostata usando i valori di `InnerElementType` enumerazione.  
  
|Nome descrittivo in InnerElementType|Valore numerico|  
|---------------------------------------|-------------------|  
|Navigator|0|  
|Node|1|  
|NodeText|2|  
  
##  <a name="Tasks"></a> Attività  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] include numerose attività con proprietà che possono essere impostate tramite espressioni di proprietà.  
  
### <a name="analysis-services-execute-ddl-task"></a>Attività Esegui DDL Analysis Services  
 `SourceType` proprietà: impostata usando i valori di `DDLSourceType` enumerazione.  
  
|Nome descrittivo in DDLSourceType|Valore numerico|  
|------------------------------------|-------------------|  
|DirectInput|0|  
|FileConnection|1|  
|Variabile|2|  
  
### <a name="bulk-insert-task"></a>Inserimento bulk - attività  
 `DataFileType` proprietà: impostata usando i valori di `DTSBulkInsert_DataFileType` enumerazione.  
  
|Nome descrittivo in DTSBulkInsert_DataFileType|Valore numerico|  
|--------------------------------------------------|-------------------|  
|DTSBulkInsert_DataFileType_Char|0|  
|DTSBulkInsert_DataFileType_Native|1|  
|DTSBulkInsert_DataFileType_WideChar|2|  
|DTSBulkInsert_DataFileType_WideNative|3|  
  
### <a name="execute-sql-task"></a>Attività Esegui SQL  
 `ResultSetType` proprietà: impostata usando i valori di `ResultSetType` enumerazione.  
  
|Nome descrittivo in ResultSetType|Valore numerico|  
|------------------------------------|-------------------|  
|ResultSetType_None|1|  
|ResultSetType_SingleRow|2|  
|ResultSetType_Rowset|3|  
|ResultSetType_XML|4|  
  
 `SqlStatementSourceType` proprietà: impostata usando i valori di `SqlStatementSourceType` enumerazione.  
  
|Nome descrittivo in SqlStatementSourceType|Valore numerico|  
|---------------------------------------------|-------------------|  
|DirectInput|1|  
|FileConnection|2|  
|Variabile|3|  
  
### <a name="file-system-task"></a>Attività File system  
 `Operation` proprietà: impostata usando i valori di `DTSFileSystemOperation` enumerazione.  
  
|Nome descrittivo in DTSFileSystemOperation|Valore numerico|  
|---------------------------------------------|-------------------|  
|CopyFile|0|  
|MoveFile|1|  
|DeleteFile|2|  
|RenameFile|3|  
|SetAttributes|4|  
|CreateDirectory|5|  
|CopyDirectory|6|  
|MoveDirectory|7|  
|DeleteDirectory|8|  
|DeleteDirectoryContent|9|  
  
 `Attributes` proprietà: impostata usando i valori di `DTSFileSystemAttributes` enumerazione.  
  
|Nome descrittivo in DTSFileSystemAttributes|Valore numerico|  
|----------------------------------------------|-------------------|  
|Normale|0|  
|Archive|1|  
|Hidden|2|  
|ReadOnly|4|  
|Sistema|8|  
  
### <a name="ftp-task"></a>Attività FTP  
 `Operation` proprietà: impostata usando i valori di `DTSFTPOp` enumerazione.  
  
|Nome descrittivo in DTSFTPOp|Valore numerico|  
|-------------------------------|-------------------|  
|Send|0|  
|Receive|1|  
|DeleteLocal|2|  
|DeleteRemote|3|  
|MakeDirLocal|4|  
|MakeDirRemote|5|  
|RemoveDirLocal|6|  
|RemoveDirRemote|7|  
  
### <a name="message-queue-task"></a>Message Queue Task  
 `MessageType` proprietà: impostata usando i valori di `MQMessageType` enumerazione.  
  
|Nome descrittivo in MQMessageType|Valore numerico|  
|------------------------------------|-------------------|  
|DTSMQMessageType_String|0|  
|DTSMQMessageType_DataFile|1|  
|DTSMQMessageType_Variables|2|  
|DTSMQMessagType_StringMessageToVariable|3|  
  
 `StringCompareType` proprietà: impostata usando i valori di `MQStringMessageCompare` enumerazione.  
  
|Nome descrittivo in MQStringMessageCompare|Valore numerico|  
|---------------------------------------------|-------------------|  
|DTSMQStringMessageCompare_None|0|  
|DTSMQStringMessageCompare_Exact|1|  
|DTSMQStringMessageCompare_IgnoreCase|2|  
|DTSMQStringMessageCompare_Contains|3|  
  
 `TaskType` proprietà: impostata usando i valori di `MQType` enumerazione.  
  
|Nome descrittivo in MQType|Valore numerico|  
|-----------------------------|-------------------|  
|DTSMQType_Sender|0|  
|DTSMQType_Receiver|1|  
  
### <a name="send-mail-task"></a>Invia messaggi - attività  
 `MessageSourceType` proprietà: impostata usando i valori di `SendMailMessageSourceType` enumerazione.  
  
|Nome descrittivo in SendMailMessageSourceType|Valore numerico|  
|------------------------------------------------|-------------------|  
|DirectInput|0|  
|FileConnection|1|  
|Variabile|2|  
  
 `Priority` proprietà: impostata usando i valori di `MailPriority` enumerazione.  
  
|Nome descrittivo in MailPriority|Valore numerico|  
|-----------------------------------|-------------------|  
|Alto|1|  
|Normal|3|  
|Basso|5|  
  
### <a name="transfer-database-task"></a>Attività Trasferisci database  
 `Action` proprietà: impostata usando i valori di `TransferAction` enumerazione.  
  
|Nome descrittivo in TransferAction|Valore numerico|  
|-------------------------------------|-------------------|  
|Copia|0|  
|Visualizzazione Dettagli|1|  
  
 `Method` proprietà: impostata usando i valori di `TransferMethod` enumerazione.  
  
|Nome descrittivo in TransferMethod|Valore numerico|  
|-------------------------------------|-------------------|  
|DatabaseOffline|0|  
|DatabaseOnline|1|  
  
### <a name="transfer-error-messages-task"></a>Attività Trasferisci messaggi di errore  
 `IfObjectExists` proprietà: impostata usando i valori di `IfObjectExists` enumerazione.  
  
|Nome descrittivo in IfObjectExists|Valore numerico|  
|-------------------------------------|-------------------|  
|FailTask|0|  
|Overwrite|1|  
|Skip|2|  
  
### <a name="transfer-jobs-task"></a>Attività Trasferisci processi  
 `IfObjectExists` proprietà: impostata usando i valori di `IfObjectExists` enumerazione.  
  
|Nome descrittivo in IfObjectExists|Valore numerico|  
|-------------------------------------|-------------------|  
|FailTask|0|  
|Overwrite|1|  
|Skip|2|  
  
### <a name="transfer-logins-task"></a>Attività Trasferisci account di accesso  
 `IfObjectExists` proprietà: impostata usando i valori di `IfObjectExists` enumerazione.  
  
|Nome descrittivo in IfObjectExists|Valore numerico|  
|-------------------------------------|-------------------|  
|FailTask|0|  
|Overwrite|1|  
|Skip|2|  
  
 `LoginsToTransfer` proprietà: impostata usando i valori di `LoginsToTransfer` enumerazione.  
  
|Nome descrittivo in LoginsToTransfer|Valore numerico|  
|---------------------------------------|-------------------|  
|AllLogins|0|  
|SelectedLogins|1|  
|AllLoginsFromSelectedDatabases|2|  
  
### <a name="transfer-master-stored-procedures-task"></a>Attività Trasferisci stored procedure master  
 `IfObjectExists` proprietà: impostata usando i valori di `IfObjectExists` enumerazione.  
  
|Nome descrittivo in IfObjectExists|Valore numerico|  
|-------------------------------------|-------------------|  
|FailTask|0|  
|Overwrite|1|  
|Skip|2|  
  
### <a name="transfer-sql-server-objects-task"></a>Attività Trasferisci oggetti di SQL Server  
 `ExistingData` proprietà: impostata usando i valori di `ExistingData` enumerazione.  
  
|Nome descrittivo in ExistingData|Valore numerico|  
|-----------------------------------|-------------------|  
|Sostituisci|0|  
|Accoda|1|  
  
### <a name="web-service-task"></a>Attività Servizio Web  
 `OutputType` proprietà: impostata usando i valori di `DTSOutputType` enumerazione.  
  
|Nome descrittivo in DTSOutputType|Valore numerico|  
|------------------------------------|-------------------|  
|File|0|  
|Variabile|1|  
  
### <a name="wmi-data-reader-task"></a>Attività Lettore di dati WMI  
 `OverwriteDestination` proprietà: impostata usando i valori di `OverwriteDestination` enumerazione.  
  
|Nome descrittivo in OverwriteDestination|Valore numerico|  
|-------------------------------------------|-------------------|  
|OverwriteDestination|0|  
|AppendToDestination|1|  
|KeepOriginal|2|  
  
 `OutputType` proprietà: impostata usando i valori di `OutputType` enumerazione.  
  
|Nome descrittivo in OutputType|Valore numerico|  
|---------------------------------|-------------------|  
|DataTable|0|  
|PropertyValue|1|  
|PropertyNameAndValue|2|  
  
 `DestinationType` proprietà: impostata usando i valori di `DestinationType` enumerazione.  
  
|Nome descrittivo in DestinationType|Valore numerico|  
|--------------------------------------|-------------------|  
|FileConnection|0|  
|Variabile|1|  
  
 `WqlQuerySourceType` proprietà: impostata usando i valori di `QuerySourceType` enumerazione.  
  
|Nome descrittivo in QuerySourceType|Valore numerico|  
|--------------------------------------|-------------------|  
|FileConnection|0|  
|DirectInput|1|  
|Variabile|2|  
  
 Proprietà `ActionAtEvent` di Monitoraggio eventi WMI: impostata utilizzando i valori dell'enumerazione `ActionAtEvent`.  
  
|Nome descrittivo in ActionAtEvent|Valore numerico|  
|------------------------------------|-------------------|  
|LogTheEventAndFireDTSEvent|0|  
|LogTheEvent|1|  
  
 `ActionAtTimeout` proprietà: impostata usando i valori di `ActionAtTimeout` enumerazione.  
  
|Nome descrittivo in ActionAtTimeout|Valore numerico|  
|--------------------------------------|-------------------|  
|LogTimeoutAndFireDTSEvent|0|  
|LogTimeout|1|  
  
 `AfterEvent` proprietà: impostata usando i valori di `AfterEvent` enumerazione.  
  
|Nome descrittivo in AfterEvent|Valore numerico|  
|---------------------------------|-------------------|  
|ReturnWithSuccess|0|  
|ReturnWithFailure|1|  
|WatchfortheEventAgain|2|  
  
 `AfterTimeout` proprietà: impostata usando i valori di `AfterTimeout` enumerazione.  
  
|Nome descrittivo in AfterTimeout|Valore numerico|  
|-----------------------------------|-------------------|  
|ReturnWithSuccess|0|  
|ReturnWithFailure|1|  
|WatchfortheEventAgain|2|  
  
 `WqlQuerySourceType` proprietà: impostata usando i valori di `QuerySourceType` enumerazione.  
  
|Nome descrittivo in QuerySourceType|Valore numerico|  
|--------------------------------------|-------------------|  
|FileConnection|0|  
|DirectInput|1|  
|Variabile|2|  
  
### <a name="xml-task"></a>Attività XML  
 `OperationType` proprietà: impostata usando i valori di `DTSXMLOperation` enumerazione.  
  
|Nome descrittivo in DTSXMLOperation|Valore numerico|  
|--------------------------------------|-------------------|  
|Convalida|0|  
|XSLT|1|  
|XPATH|2|  
|Merge|3|  
|Diff|4|  
|Patch|5|  
  
 Proprietà `SourceType`, `SecondOperandType` e `XPathSourceType`: impostate utilizzando i valori dell'enumerazione `DTSXMLSourceType`.  
  
|Nome descrittivo in DTSXMLSourceType|Valore numerico|  
|---------------------------------------|-------------------|  
|FileConnection|0|  
|Variabile|1|  
|DirectInput|2|  
  
 `DestinationType` e **DiffGramDestinationType** delle proprietà: impostata usando i valori di `DTSXMLSaveResultTo` enumerazione.  
  
|Nome descrittivo in DTSXMLSaveResultTo|Valore numerico|  
|-----------------------------------------|-------------------|  
|FileConnection|0|  
|Variabile|1|  
  
 `ValidationType` proprietà: impostata usando i valori di `DTSXMLValidationType` enumerazione.  
  
|Nome descrittivo in DTSXMLValidationType|Valore numerico|  
|-------------------------------------------|-------------------|  
|DTD|0|  
|XSD|1|  
  
 `XPathOperation` proprietà: impostata usando i valori di `DTSXMLXPathOperation` enumerazione.  
  
|Nome descrittivo in DTSXMLXPathOperation|Valore numerico|  
|-------------------------------------------|-------------------|  
|Copia di valutazione|0|  
|Valori|1|  
|NodeList|2|  
  
 `DiffOptions` proprietà: impostata usando i valori di `DTSXMLDiffOptions` enumerazione. Le opzioni in questo enumeratore non si escludono a vicenda. Per utilizzare più opzioni, specificare le opzioni desiderate in un elenco delimitato da virgole.  
  
|Nome descrittivo in DTSXMLDiffOptions|Valore numerico|  
|----------------------------------------|-------------------|  
|None|0|  
|IgnoreChildOrder|1|  
|IgnoreComments|2|  
|IgnorePI|4|  
|IgnoreWhitespace|8|  
|IgnoreNamespaces|16|  
|IgnorePrefixes|32|  
|IgnoreXmlDecl|64|  
|IgnoreDtd|128|  
  
 `DiffAlgorithm` proprietà: impostata usando i valori di `DTSXMLDiffAlgorithm` enumerazione.  
  
|Nome descrittivo in DTSXMLDiffAlgorithm|Valore numerico|  
|------------------------------------------|-------------------|  
|Auto|0|  
|Veloce|1|  
|Preciso|2|  
  
##  <a name="MaintenancePlanTasks"></a> Attività Piano di manutenzione  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] include un set di attività che consentono di eseguire attività di SQL Server da usare in piani di manutenzione e pacchetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non supporta l'uso di queste attività a livello di codice e la documentazione di riferimento per la programmazione non include la documentazione dell'API di tali attività e dei relativi enumeratori.  
  
### <a name="all-maintenance-tasks"></a>Tutte le attività di manutenzione  
 Tutte le attività di manutenzione utilizzano le enumerazioni seguenti per impostare le proprietà specificate.  
  
 `DatabaseSelectionType` proprietà: impostata usando i valori di `DatabaseSelection` enumerazione.  
  
|Nome descrittivo in DatabaseSelection|Valore numerico|  
|----------------------------------------|-------------------|  
|None|0|  
|All|1|  
|Sistema|2|  
|Utente|3|  
|Specific|4|  
  
 `TableSelectionType` proprietà: impostata usando i valori di `TableSelection` enumerazione.  
  
|Nome descrittivo in TableSelection|Valore numerico|  
|-------------------------------------|-------------------|  
|None|0|  
|All|1|  
|Specific|2|  
  
 `ObjectTypeSelection` proprietà: impostata usando i valori di `ObjectType` enumerazione.  
  
|Nome descrittivo in ObjectType|Valore numerico|  
|---------------------------------|-------------------|  
|Tabella|0|  
|Vista|1|  
|TableView|2|  
  
### <a name="back-up-database-task"></a>Attività Backup database  
 `DestinationCreationType` proprietà: impostata usando i valori di `DestinationType` enumerazione.  
  
|Nome descrittivo in DestinationType|Valore numerico|  
|--------------------------------------|-------------------|  
|Auto|0|  
|Manual|1|  
  
 `ExistingBackupsAction` proprietà: impostata usando i valori di `ActionForExistingBackups` enumerazione.  
  
|Nome descrittivo in ActionForExistingBackups|Valore numerico|  
|-----------------------------------------------|-------------------|  
|Accoda|0|  
|Overwrite|1|  
  
 `BackupAction` proprietà: impostata usando i valori di `BackupTaskType` enumerazione. Questa proprietà viene utilizzata con la `BackupIsIncremental` proprietà per definire il tipo di backup eseguita dall'attività.  
  
|Nome descrittivo in BackupTaskType|Valore numerico|  
|-------------------------------------|-------------------|  
|Database|0|  
|File|1|  
|File di log|2|  
  
 Proprietà `BackupDevice`: impostata utilizzando i valori dell'enumerazione `DeviceType` di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO).  
  
|Nome descrittivo in DeviceType|Valore numerico|  
|---------------------------------|-------------------|  
|LogicalDevice|0|  
|Nastro|1|  
|File|2|  
|Pipe|3|  
|VirtualDevice|4|  
  
### <a name="maintenance-cleanup-task"></a>Attività Pulizia file manutenzione  
 `FileTypeSelected` proprietà: impostata usando i valori di `FileType` enumerazione.  
  
|Nome descrittivo in FileType|Valore numerico|  
|-------------------------------|-------------------|  
|FileBackup|0|  
|FileReport|1|  
  
 `OlderThanTimeUnitType` proprietà: impostata usando i valori di `TimeUnitType` enumerazione.  
  
|Nome descrittivo in TimeUnitType|Valore numerico|  
|-----------------------------------|-------------------|  
|Day|0|  
|Week|1|  
|Month|2|  
|Year|3|  
  
### <a name="update-statistics-task"></a>Attività Aggiorna statistiche  
 Proprietà `UpdateType`: impostata utilizzando i valori dell'enumerazione `StatisticsTarget` di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO).  
  
|Nome descrittivo in StatisticsTarget|Valore numerico|  
|---------------------------------------|-------------------|  
|colonna|1|  
|Indice|2|  
|All|3|  
  
##  <a name="CommonProperties"></a> Proprietà comuni  
 I pacchetti, le attività e i contenitori Ciclo Foreach, Ciclo For e Sequenza possono utilizzare le enumerazioni seguenti per impostare le proprietà specificate.  
  
 `ForceExecutionResult` proprietà: impostata usando i valori di `DTSForcedExecResult` enumerazione.  
  
|Nome descrittivo in DTSForcedExecResult|Valore numerico|  
|------------------------------------------|-------------------|  
|None|-1|  
|Esito positivo|0|  
|Failure|1|  
|Completion|2|  
  
 Proprietà `IsolationLevel`: impostata utilizzando i valori dell'enumerazione `IsolationLevel` di .NET Framework. Per altre informazioni, vedere la libreria di classi di Microsoft .NET Framework in [MSDN Library](http://go.microsoft.com/fwlink?LinkId=17313).  
  
 `LoggingMode` proprietà: impostata usando i valori di `DTSLoggingMode` enumerazione.  
  
|Nome descrittivo in DTSLoggingMode|Valore numerico|  
|-------------------------------------|-------------------|  
|UseParentSetting|0|  
|Abilitata|1|  
|Disabilitata|2|  
  
 `TransactionOption` proprietà: impostata usando i valori di `DTSTransactionOption` enumerazione.  
  
|Nome descrittivo in DTSTransactionOption|Valore numerico|  
|-------------------------------------------|-------------------|  
|NotSupported|0|  
|Supportato|1|  
|Obbligatorio|2|  
  
## <a name="related-tasks"></a>Related Tasks  
 [Aggiungere o modificare un'espressione di proprietà](add-or-change-a-property-expression.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo delle espressioni di proprietà nei pacchetti](use-property-expressions-in-packages.md)   
 [Integration Services &#40;SSIS&#41; i pacchetti](../integration-services-ssis-packages.md)   
 [Contenitori in Integration Services](../control-flow/integration-services-containers.md)   
 [Attività di Integration Services](../control-flow/integration-services-tasks.md)   
 [Vincoli di precedenza](../control-flow/precedence-constraints.md)  
  
  

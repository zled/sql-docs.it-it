---
title: "Membri di MSReportServer_ConfigurationSetting | Microsoft Docs"
ms.custom: ""
ms.date: "03/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "MSReportServer_ConfigurationSetting Members"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "provider WMI [Reporting Services], classe MSReportServer_ConfigurationSetting"
  - "classe MSReportServer_ConfigurationSetting"
ms.assetid: 5e21a53a-a2f8-4b35-a8d9-5483519e3857
caps.latest.revision: 46
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 46
---
# Membri di MSReportServer_ConfigurationSetting
  La classe MSReportServer_ConfigurationSetting contiene le proprietà e i metodi seguenti.  
  
## Proprietà pubbliche  
  
|||  
|-|-|  
|[ConnectionPoolSize](../../reporting-services/wmi-provider-library-reference/connectionpoolsize-property-wmi-msreportserver-configurationsetting.md)|Restituisce le dimensioni del pool di connessioni utilizzato dal server di report per comunicare con l'istanza del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] che ospita il database del server di report. Di sola lettura.|  
|[DatabaseLogonAccount](../../reporting-services/wmi-provider-library-reference/databaselogonaccount-property-wmi-msreportserver-configurationsetting.md)|Specifica l'account di accesso utilizzato dal server di report per connettersi all'istanza del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] che ospita il database del server di report. Di sola lettura.|  
|[DatabaseLogonTimeout](../../reporting-services/wmi-provider-library-reference/databaselogontimeout-property-wmi-msreportserver-configurationsetting.md)|Specifica il numero di secondi di attesa prima che un tentativo di accesso al database del server di report abbia esito negativo. Di sola lettura.|  
|[DatabaseLogonType](../../reporting-services/wmi-provider-library-reference/databaselogontype-property-wmi-msreportserver-configurationsetting.md)|Specifica se il server di report utilizza un account del servizio Windows, un account utente di Windows o un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per accedere al database del server di report. Di sola lettura.|  
|[DatabaseName](../../reporting-services/wmi-provider-library-reference/databasename-property-wmi-msreportserver-configurationsetting.md)|Specifica il nome dell'istanza del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che ospita il database del server di report.|  
|[DatabaseQueryTimeout](../../reporting-services/wmi-provider-library-reference/databasequerytimeout-property-wmi-msreportserver-configurationsetting.md)|Specifica il numero di secondi che devono trascorrere prima che il comando non riesca o che si verifichi il timeout. Il server di report calcola il tempo del processo rispetto al database del server di report e non rispetto a un'origine dati per il report.|  
|[DatabaseServerName](../../reporting-services/wmi-provider-library-reference/databaseservername-property-wmi-msreportserver-configurationsetting.md)|Specifica il nome del server in cui è installato il database del server di report.|  
|[Proprietà InstallationID](../../reporting-services/wmi-provider-library-reference/installationid-property-wmi-msreportserver-configurationsetting.md)|Restituisce un identificatore univoco per un'istanza del server di report specifica.|  
|[InstanceName](../../reporting-services/wmi-provider-library-reference/instancename-property-wmi-msreportserver-configurationsetting.md)|Specifica il nome di un'istanza del server di report in un determinato computer.|  
|[IsInitialized](../../reporting-services/wmi-provider-library-reference/isinitialized-property-wmi-msreportserver-configurationsetting.md)|Indica se l'istanza del server di report è inizializzata. Di sola lettura.|  
|[IsSharePointIntegrated](../../reporting-services/wmi-provider-library-reference/issharepointintegrated-property-wmi.md)|Indica se il server di report è configurato per la modalità integrata SharePoint.|  
|[IsWebServiceEnabled](../../reporting-services/wmi-provider-library-reference/iswebserviceenabled-property-wmi-msreportserver-configurationsetting.md)|Indica se il servizio Web ReportServer è abilitato. Di sola lettura.|  
|[IsWindowsServiceEnabled](../../reporting-services/wmi-provider-library-reference/iswindowsserviceenabled-property-wmi-msreportserver-configurationsetting.md)|Indica se il servizio Windows ReportServer è abilitato. Di sola lettura.|  
|[Proprietà MachineAccountIdentity &#40;WMI&#41;](../../reporting-services/wmi-provider-library-reference/machineaccountidentity-property-wmi.md)|Ottiene l'identità dell'account del computer in cui è installato il server di report.|  
|[PathName](../../reporting-services/wmi-provider-library-reference/pathname-property-wmi-msreportserver-configurationsetting.md)|Specifica il percorso di installazione per un'istanza del server di report.|  
|[SecureConnectionLevel](../../reporting-services/wmi-provider-library-reference/secureconnectionlevel-property-wmi-msreportserver-configurationsetting.md)|Restituisce il livello di connessione protetta specificato nel file RSReportServer.config.|  
|[SenderEmailAddress](../../reporting-services/wmi-provider-library-reference/senderemailaddress-property-wmi-msreportserver-configurationsetting.md)|Ottiene l'indirizzo utilizzato per inviare messaggi di posta elettronica dal server di report. Di sola lettura.|  
|[SendUsingSMTPServer](../../reporting-services/wmi-provider-library-reference/sendusingsmtpserver-property-wmi-msreportserver-configurationsetting.md)|Specifica se la proprietà SendUsing nella configurazione della posta elettronica è impostata su TRUE.|  
|[SMTPServer](../../reporting-services/wmi-provider-library-reference/smtpserver-property-wmi-msreportserver-configurationsetting.md)|Ottiene la proprietà del server SMTP dal file RSReportServer.config. Di sola lettura.|  
|[UnattendedExecutionAccount](../../reporting-services/wmi-provider-library-reference/unattendedexecutionaccount-property-wmi-msreportserver-configurationsetting.md)|Specifica l'account utente di accesso rappresentato dal server di report per l'esecuzione automatica dei report. Di sola lettura.|  
|[Version](../../reporting-services/wmi-provider-library-reference/version-property-wmi-msreportserver-configurationsetting.md)|Restituisce la versione del server di report.|  
|[Proprietà VirtualDirectoryReportManager &#40;MSReportServer_ConfigurationSetting WMI&#41;](../../reporting-services/wmi-provider-library-reference/virtualdirectoryreportmanager-property-wmi-msreportserver-configurationsetting.md)|Restituisce la directory virtuale per Gestione report.|  
|[Proprietà VirtualDirectoryReportServer &#40;MSReportServer_ConfigurationSetting WMI&#41;](../../reporting-services/wmi-provider-library-reference/virtualdirectoryreportserver-property-wmi-msreportserver-configurationsetting.md)|Restituisce la directory virtuale per il servizio Web ReportServer.|  
|[WindowsServiceIdentityActual](../../reporting-services/wmi-provider-library-reference/windowsserviceidentityactual-property-wmi-msreportserver-configurationsetting.md)|Restituisce l'identità con cui il servizio Windows ReportServer è effettivamente in esecuzione. Di sola lettura.|  
|[WindowsServiceIdentityConfigured](../../reporting-services/wmi-provider-library-reference/windowsserviceidentityconfigured-property.md)|Restituisce l'ultima identità con cui il servizio Windows ReportServer è stato configurato per l'esecuzione. Di sola lettura.|  
  
## Metodi pubblici  
  
|||  
|-|-|  
|[BackupEncryptionKey](../../reporting-services/wmi-provider-library-reference/backupencryptionkey-method-wmi-msreportserver-configurationsetting.md)|Esegue il backup della chiave di crittografia per l'istanza. Tale chiave viene archiviata crittografata con una password.|  
|[Metodo CreateSSLCertificateBinding &#40;MSReportServer_ConfigurationSetting WMI&#41;](../../reporting-services/wmi-provider-library-reference/createsslcertificatebinding-method-wmi-msreportserver-configurationsetting.md)|Crea un'associazione certificato SSL.|  
|[DeleteEncryptedInformation](../../reporting-services/wmi-provider-library-reference/deleteencryptedinformation-method-wmi-msreportserver-configurationsetting.md)|Elimina le informazioni crittografate dal database del server di report.|  
|[DeleteEncryptionKey](../../reporting-services/wmi-provider-library-reference/deleteencryptionkey-method-wmi-msreportserver-configurationsetting.md)|Elimina le chiavi di crittografia dal database del server di report.|  
|[GenerateDatabaseCreationScript](../../reporting-services/wmi-provider-library-reference/generatedatabasecreationscript-method-wmi-msreportserver-configurationsetting.md)|Genera uno script SQL che può essere utilizzato per creare il database del server di report.|  
|[GenerateDatabaseRightsScript](../../reporting-services/wmi-provider-library-reference/generatedatabaserightsscript-method-wmi-msreportserver-configurationsetting.md)|Genera uno script SQL che può essere utilizzato per concedere a un utente le autorizzazioni per il database del server di report.|  
|[GenerateDatabaseUpgradeScript](../../reporting-services/wmi-provider-library-reference/generatedatabaseupgradescript-method-wmi-msreportserver-configurationsetting.md)|Genera uno script SQL che può essere utilizzato per aggiornare un database del server di report.|  
|[Metodo GetAdminSiteUrl &#40;WMI&#41;](../../reporting-services/wmi-provider-library-reference/getadminsiteurl-method-wmi.md)|Ottiene l'URL assoluto del sito Web di Amministrazione centrale.|  
|[GetDatabaseVersionDisplayName](../../reporting-services/wmi-provider-library-reference/getdatabaseversiondisplayname-method-wmi.md)|Ottiene il nome visualizzato di una stringa di versione di un database del server di report specifico.|  
|[InitializeReportServer](../../reporting-services/wmi-provider-library-reference/initializereportserver-method-wmi-msreportserver-configurationsetting.md)|Inizializza l'istanza del server di report specificata.|  
|[Metodo ListInstalledSharePointVersions &#40;WMI&#41;](../../reporting-services/wmi-provider-library-reference/listinstalledsharepointversions-method-wmi.md)|Restituisce un set di token che rappresentano le versioni di [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]o [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] installate nello stesso computer del server di report.|  
|[Metodo ListIPAddresses &#40;MSReportServer_ConfigurationSetting WMI&#41;](../../reporting-services/wmi-provider-library-reference/listipaddresses-method-wmi-msreportserver-configurationsetting.md)|Elenca gli indirizzi IP per il computer.|  
|[ListReportServersInDatabase](../../reporting-services/wmi-provider-library-reference/listreportserversindatabase-method-wmi-msreportserver-configurationsetting.md)|Restituisce un elenco di installazioni del server di report presenti nel database del server di report, indipendentemente dal fatto che tali installazioni accedano o meno a informazioni protette.|  
|[Metodo ListReservedURLs &#40;MSReportServer_ConfigurationSetting WMI&#41;](../../reporting-services/wmi-provider-library-reference/listreservedurls-method-wmi-msreportserver-configurationsetting.md)|Elenca gli URL riservati per tutte le applicazioni presenti nel server di report.|  
|[Metodo ListSSLCertificateBindings &#40;MSReportServer_ConfigurationSetting WMI&#41;](../../reporting-services/wmi-provider-library-reference/listsslcertificatebindings-method-wmi-msreportserver-configurationsetting.md)|Elenca le associazioni certificato SSL presenti in HTTP.SYS e quelle previste da rsreportserver.config.|  
|[Metodo ListSSLCertificate &#40;MSReportServer_ConfigurationSetting WMI&#41;](../../reporting-services/wmi-provider-library-reference/listsslcertificates-method-wmi-msreportserver-configurationsetting.md)|Elenca i certificati SSL installati nel computer.|  
|[ReencryptSecureInformation](../../reporting-services/wmi-provider-library-reference/reencryptsecureinformation-method-wmi-msreportserver-configurationsetting.md)|Genera una nuova chiave di crittografia e la utilizza per crittografare nuovamente tutte le informazioni protette nel database del server di report.|  
|[Metodo RemoveSSLCertificateBindings &#40;MSReportServer_ConfigurationSetting WMI&#41;](../../reporting-services/wmi-provider-library-reference/removesslcertificatebindings-method-wmi-msreportserver-configurationsetting.md)|Rimuove un'associazione certificato SSL.|  
|[RemoveUnattendedExecutionAccount](../../reporting-services/wmi-provider-library-reference/removeunattendedexecutionaccount-method-wmi-msreportserver-configurationsetting.md)|Elimina la voce relativa all'account di esecuzione automatica dalla configurazione del server di report.|  
|[Metodo RemoveURL &#40;MSReportServer_ConfigurationSetting WMI&#41;](../../reporting-services/wmi-provider-library-reference/removeurl-method-wmi-msreportserver-configurationsetting.md)|Rimuove un URL riservato per il server di report.|  
|[Metodo ReserveURL &#40;MSReportServer_ConfigurationSetting WMI&#41;](../../reporting-services/wmi-provider-library-reference/reserveurl-method-wmi-msreportserver-configurationsetting.md)|Aggiunge una prenotazione URL per un'applicazione specifica.|  
|[RestoreEncryptionKey](../../reporting-services/wmi-provider-library-reference/restoreencryptionkey-method-wmi-msreportserver-configurationsetting.md)|Riapplica la chiave di crittografia specificata al database del server di report.|  
|[SetDatabaseConnection](../../reporting-services/wmi-provider-library-reference/setdatabaseconnection-method-wmi-msreportserver-configurationsetting.md)|Imposta la connessione al database del server di report su un database del server di report specifico.|  
|[SetDatabaseLogonTimeout](../../reporting-services/wmi-provider-library-reference/setdatabaselogontimeout-method-wmi-msreportserver-configurationsetting.md)|Specifica il valore di timeout predefinito per i tentativi di accesso al database del server di report.|  
|[SetDatabaseQueryTimeout](../../reporting-services/wmi-provider-library-reference/setdatabasequerytimeout-method-wmi-msreportserver-configurationsetting.md)|Specifica il valore di timeout predefinito per le connessione al database del server di report.|  
|[SetEmailConfiguration](../../reporting-services/wmi-provider-library-reference/setemailconfiguration-method-wmi-msreportserver-configurationsetting.md)|Configura l'estensione per il recapito tramite posta elettronica utilizzata dal server di report per l'invio di messaggi di posta elettronica.|  
|[SetSecureConnectionLevel](../../reporting-services/wmi-provider-library-reference/setsecureconnectionlevel-method-wmi-msreportserver-configurationsetting.md)|Imposta il livello di connessione protetta del server di report.|  
|[SetServiceState](../../reporting-services/wmi-provider-library-reference/setservicestate-method-wmi-msreportserver-configurationsetting.md)|Attiva e disattiva i servizi Windows ReportServer e Web ReportServer.|  
|[SetUnattendedExecutionAccount](../../reporting-services/wmi-provider-library-reference/setunattendedexecutionaccount-method-wmi-msreportserver-configurationsetting.md)|Specifica l'account utilizzato per l'esecuzione automatica dei report.|  
|[Metodo SetVirtualDirectory &#40;MSReportServer_ConfigurationSetting WMI&#41;](../../reporting-services/wmi-provider-library-reference/setvirtualdirectory-method-wmi-msreportserver-configurationsetting.md)|Imposta la directory virtuale per un'applicazione.|  
|[SetWindowsServiceIdentity](../../reporting-services/wmi-provider-library-reference/setwindowsserviceidentity-method-wmi-msreportserver-configurationsetting.md)|Consente l'esecuzione del servizio Windows ReportServer in base all'utente di Windows specificato e concede a tale account autorizzazioni per il file system sufficienti, in modo da consentire il funzionamento del server di report.|  
  
## Vedere anche  
 [Classe MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
  
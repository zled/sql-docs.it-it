---
title: "Metodi di MSReportServer_ConfigurationSetting | Microsoft Docs"
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
  - "MSReportServer_ConfigurationSetting Methods"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "provider WMI [Reporting Services], classe MSReportServer_ConfigurationSetting"
  - "classe MSReportServer_ConfigurationSetting"
ms.assetid: a08c2476-5b8e-4792-94da-1360fe231c6e
caps.latest.revision: 45
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 45
---
# Metodi di MSReportServer_ConfigurationSetting
  La classe MSReportServer_ConfigurationSetting del provider WMI del server di report fornisce i seguenti metodi pubblici.  
  
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
|[Metodo ListInstalledSharePointVersions &#40;WMI&#41;](../../reporting-services/wmi-provider-library-reference/listinstalledsharepointversions-method-wmi.md)|Restituisce un set di token che rappresentano le versioni di Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]o [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] installate nello stesso computer del server di report.|  
|[Metodo ListIPAddresses &#40;MSReportServer_ConfigurationSetting WMI&#41;](../../reporting-services/wmi-provider-library-reference/listipaddresses-method-wmi-msreportserver-configurationsetting.md)|Elenca gli indirizzi IP per il computer.|  
|[ListReportServersInDatabase](../../reporting-services/wmi-provider-library-reference/listreportserversindatabase-method-wmi-msreportserver-configurationsetting.md)|Restituisce un elenco di installazioni del server di report presenti nel database del server di report, indipendentemente dal fatto che tali installazioni accedano o meno a informazioni protette.|  
|[Metodo ListReservedURLs &#40;MSReportServer_ConfigurationSetting WMI&#41;](../../reporting-services/wmi-provider-library-reference/listreservedurls-method-wmi-msreportserver-configurationsetting.md)|Elenca gli URL riservati per tutte le applicazioni presenti nel server di report.|  
|[Metodo ListSSLCertificateBindings &#40;MSReportServer_ConfigurationSetting WMI&#41;](../../reporting-services/wmi-provider-library-reference/listsslcertificatebindings-method-wmi-msreportserver-configurationsetting.md)|Elenca le associazioni certificato SSL presenti in HTTP.SYS e quelle previste da RSReportServer.config.|  
|[Metodo ListSSLCertificate &#40;MSReportServer_ConfigurationSetting WMI&#41;](../../reporting-services/wmi-provider-library-reference/listsslcertificates-method-wmi-msreportserver-configurationsetting.md)|Elenca i certificati SSL installati nel computer.|  
|[ReencryptSecureInformation](../../reporting-services/wmi-provider-library-reference/reencryptsecureinformation-method-wmi-msreportserver-configurationsetting.md)|Genera una nuova chiave di crittografia e la utilizza per crittografare nuovamente tutte le informazioni protette nel database del server di report.|  
|[Metodo RemoveSSLCertificateBindings &#40;MSReportServer_ConfigurationSetting WMI&#41;](../../reporting-services/wmi-provider-library-reference/removesslcertificatebindings-method-wmi-msreportserver-configurationsetting.md)|Rimuove un'associazione certificato SSL.|  
|[RemoveUnattendedExecutionAccount](../../reporting-services/wmi-provider-library-reference/removeunattendedexecutionaccount-method-wmi-msreportserver-configurationsetting.md)|Elimina la voce relativa all'account di esecuzione automatica dalla configurazione del server di report.|  
|[Metodo RemoveURL &#40;MSReportServer_ConfigurationSetting WMI&#41;](../../reporting-services/wmi-provider-library-reference/removeurl-method-wmi-msreportserver-configurationsetting.md)|Rimuove un URL riservato per il server di report.|  
|[Metodo ReserveURL &#40;MSReportServer_ConfigurationSetting WMI&#41;](../../reporting-services/wmi-provider-library-reference/reserveurl-method-wmi-msreportserver-configurationsetting.md)|Aggiunge una prenotazione URL per un'applicazione specifica.|  
|[RestoreEncryptionKey](../../reporting-services/wmi-provider-library-reference/restoreencryptionkey-method-wmi-msreportserver-configurationsetting.md)|Riapplica la chiave di crittografia specificata al database del server di report.|  
|[SetDatabaseConnection](../../reporting-services/wmi-provider-library-reference/setdatabaseconnection-method-wmi-msreportserver-configurationsetting.md)|Imposta la connessione al database del server di report su un database del server di report specifico.|  
|[SetDatabaseLogonTimeout](../../reporting-services/wmi-provider-library-reference/setdatabaselogontimeout-method-wmi-msreportserver-configurationsetting.md)|Specifica il valore di timeout predefinito per i tentativi di accesso al database del server di report.|  
|[SetDatabaseQueryTimeout](../../reporting-services/wmi-provider-library-reference/setdatabasequerytimeout-method-wmi-msreportserver-configurationsetting.md)|Specifica il valore di timeout predefinito per le query sul database del server di report.|  
|[SetEmailConfiguration](../../reporting-services/wmi-provider-library-reference/setemailconfiguration-method-wmi-msreportserver-configurationsetting.md)|Configura l'estensione per il recapito tramite posta elettronica utilizzata dal server di report per l'invio di messaggi di posta elettronica.|  
|[SetSecureConnectionLevel](../../reporting-services/wmi-provider-library-reference/setsecureconnectionlevel-method-wmi-msreportserver-configurationsetting.md)|Imposta il livello di connessione protetta del server di report.|  
|[SetServiceState](../../reporting-services/wmi-provider-library-reference/setservicestate-method-wmi-msreportserver-configurationsetting.md)|Attiva e disattiva il servizio ReportServer.|  
|[SetUnattendedExecutionAccount](../../reporting-services/wmi-provider-library-reference/setunattendedexecutionaccount-method-wmi-msreportserver-configurationsetting.md)|Specifica l'account utilizzato per l'esecuzione automatica dei report.|  
|[Metodo SetVirtualDirectory &#40;MSReportServer_ConfigurationSetting WMI&#41;](../../reporting-services/wmi-provider-library-reference/setvirtualdirectory-method-wmi-msreportserver-configurationsetting.md)|Imposta la directory virtuale per un'applicazione.|  
|[SetWindowsServiceIdentity](../../reporting-services/wmi-provider-library-reference/setwindowsserviceidentity-method-wmi-msreportserver-configurationsetting.md)|Consente l'esecuzione del servizio ReportServer in base all'utente di Windows specificato e concede a tale account autorizzazioni per il file system sufficienti, in modo da consentire il funzionamento del server di report.|  
  
## Vedere anche  
 [Classe MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
  
---
title: Specificare le connessioni per estensioni personalizzate di elaborazione dati | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom data processing extensions [Reporting Services]
- IDbConnection interface, connection strings
- impersonation [Reporting Services]
- IDbConnectionExtension interface, connection strings
- data sources [Reporting Services], security
- connection strings [Reporting Services]
- credentials [Reporting Services]
- authentication [Reporting Services]
- external data sources [Reporting Services]
- data processing extensions [Reporting Services], connections
ms.assetid: 2cddc9ea-0e28-4350-80ae-332412908e47
caps.latest.revision: 20
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: fc98f8394e637ea9a627cffd8e40887484462df5
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="specify-connections-for-custom-data-processing-extensions"></a>Specificare le connessioni per le estensioni per l'elaborazione dati personalizzate
  È possibile creare o utilizzare estensioni per l'elaborazione dei dati personalizzate di terze parti in un server di report per migliorare la funzionalità di elaborazione dei dati delle origini dati supportate o per supportare ulteriori tipi di origini dati non disponibili in un'installazione predefinita di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Le connessioni vengono gestite in modo diverso a seconda dell'implementazione. Per le estensioni per l'elaborazione dati sono disponibili le implementazioni seguenti:  
  
-   Provider di dati [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] personalizzati (se l'accesso ai dati viene eseguito da origini dati DB2.NET, Oracle, ODP.NET o Teradata, è possibile che si stia usando un provider di dati .NET personalizzato)  
  
-   Estensioni per l'elaborazione dati personalizzate che supportano <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection>  
  
-   Estensioni per l'elaborazione dati personalizzate che supportano <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension>  
  
> [!NOTE]  
>  Per informazioni sulla modalità di implementazione dell'estensione per l'elaborazione dati personalizzata in uso, rivolgersi al provider di terze parti.  
  
## <a name="impersonation-and-custom-data-processing-extensions"></a>Rappresentazione ed estensioni per l'elaborazione dati personalizzate  
 Se l'estensione per l'elaborazione dati personalizzate si connette alle origini dati tramite la rappresentazione, è necessario utilizzare il metodo Open in entrambi i <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> o <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension> interfacce per eseguire la richiesta. In alternativa è possibile archiviare l'oggetto identità dell'utente (System.Security.Principal.WindowsIdentity), quindi riusarlo nelle altre API dell'estensione per l'elaborazione dati.  
  
 Nelle precedenti versioni di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], tutte le estensioni per l'elaborazione dei dati personalizzate vengono chiamate durante la rappresentazione utente. Nella presente versione, invece, solo il metodo Open viene chiamato durante tale rappresentazione. Se si dispone di un'estensione per l'elaborazione dati che richiede una sicurezza integrata, è necessario modificare il codice per usare il metodo Open o archiviare l'oggetto identità dell'utente.  
  
## <a name="connections-for-custom-net-framework-data-providers"></a>Connessioni per i provider di dati .NET Framework personalizzati  
 Quando si configura un report per l'utilizzo di una specifica origine dei dati, vengono impostate proprietà che determinano il tipo di origine dei dati, la stringa di connessione e le credenziali utilizzate per accedere all'origine dei dati. Nella tabella seguente vengono descritti i tipi di credenziali supportati per i provider di dati [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] . Per altre informazioni sulle proprietà dell'origine dati del report, vedere [Specificare le credenziali e le informazioni sulla connessione per le origini dati del report](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md).  
  
|Credenziali|Connessioni|  
|-----------------|-----------------|  
|sicurezza integrata|Se il provider di dati in uso la supporta, è possibile utilizzare la sicurezza integrata di Windows. La richiesta viene inviata utilizzando le credenziali dell'utente corrente.<br /><br /> Quando si definisce la stringa di connessione, assicurarsi di includere argomenti che specifichino la sicurezza integrata (ad esempio, una connessione a un'origine dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] potrebbe includere l'argomento **Integrated Security=SSPI** nella stringa di connessione).|  
|Autenticazione di Windows|Se il provider di dati in uso lo supporta, è possibile utilizzare un account utente di dominio di Windows. Il server di report rappresenta l'account utente prima che venga chiamata l'estensione per l'elaborazione dati.<br /><br /> Quando si definisce la stringa di connessione, assicurarsi di includere argomenti che specifichino la sicurezza integrata (ad esempio, una connessione a un'origine dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] potrebbe includere l'argomento **Integrated Security=SSPI** nella stringa di connessione).|  
|Credenziali di database|L'autenticazione del database non è supportata per le connessioni stabilite mediante un provider di dati .NET personalizzato. La connessione avrà esito negativo in tutti i casi.|  
|Nessuna credenziale|È possibile utilizzare l'opzione Nessuna credenziale con provider di dati .NET personalizzati. Se viene specificato l'account per l'esecuzione automatica, la stringa di connessione determina le credenziali che verranno utilizzate. Il server di report rappresenta l'account per l'esecuzione automatica per stabilire la connessione.<br /><br /> Se l'account per l'esecuzione automatica non è definito, la connessione avrà esito negativo. Per altre informazioni sulla definizione dell'account, vedere [Configurare l'account di esecuzione automatica &#40;Gestione configurazione SSRS&#41;](../../reporting-services/install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).|  
  
## <a name="connections-for-idbconnection"></a>Connessioni per IDbConnection  
 Se si utilizza un'estensione di elaborazione dati personalizzata che supporta solo <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection>, è necessario specificare la connessione nel modo seguente:  
  
1.  Configurazione dell'account di esecuzione automatica. La configurazione di questo account è necessaria per le connessioni stabilite utilizzando **IDbConnection**. Il server di report rappresenta l'account quando viene stabilita la connessione.  
  
2.  Configurare le proprietà dell'origine dei dati nel report per l'utilizzo dell'opzione **Nessuna credenziale**.  
  
3.  Inserire le credenziali utilizzate per connettersi all'origine dei dati nella stringa di connessione.  
  
 Quando si utilizza **IDbConnection**, i tipi di credenziali seguenti non sono supportati: sicurezza integrata, account utente di Windows e credenziali del database. Se in una connessione a un'origine dei dati vengono utilizzate queste opzioni, la connessione avrà esito negativo sul server di report.  
  
## <a name="connections-for-idbconnectionextension"></a>Connessioni per IDbConnectionExtension  
 Se si utilizza un'estensione che supporta per l'elaborazione di dati personalizzati <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension>, è possibile specificare la connessione nei modi seguenti:  
  
|Credenziali|Connessioni|  
|-----------------|-----------------|  
|sicurezza integrata|Se il provider di dati in uso la supporta, è possibile utilizzare la sicurezza integrata di Windows con estensioni per l'elaborazione dati personalizzate che utilizzano **IDbConnectionExtension**.<br /><br /> Quando si definisce la stringa di connessione, assicurarsi di includere argomenti che specifichino la sicurezza integrata (ad esempio, una connessione a un'origine dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] potrebbe includere l'argomento **Integrated Security=SSPI** nella stringa di connessione).|  
|Autenticazione di Windows|Se il provider di dati in uso lo supporta, è possibile utilizzare un account utente di dominio di Windows per estensioni per l'elaborazione dati personalizzate che utilizzano **IDbConnectionExtension**.<br /><br /> Il server di report rappresenta l'account utente prima che venga chiamata l'estensione per l'elaborazione dati. Quando si definisce la stringa di connessione, assicurarsi di includere argomenti che specifichino la sicurezza integrata (ad esempio, una connessione a un'origine dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] potrebbe includere l'argomento **Integrated Security=SSPI** nella stringa di connessione).|  
|Credenziali di database|È possibile utilizzare l'autenticazione del database per configurare connessioni per estensioni per l'elaborazione dati personalizzate che utilizzano **IDbConnectionExtension**.|  
|Nessuna credenziale|Se viene specificato l'account per l'esecuzione automatica, la stringa di connessione determina le credenziali che verranno utilizzate.<br /><br /> Se l'account per l'esecuzione automatica non è definito, la connessione avrà esito negativo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare l'account di esecuzione automatica &#40;Gestione configurazione SSRS&#41;](../../reporting-services/install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)   
 [Specificare le credenziali e le informazioni sulla connessione per le origini dati del report](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Connessioni dati, origini dati e stringhe di connessione &#40;Generatore report e SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)   
 [Implementazione di un'estensione per l'elaborazione dati](../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Gestione report &#40;modalità nativa SSRS&#41;](http://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)   
 [Creare, eliminare o modificare un'origine dei dati condivisa &#40;Gestione report&#41;](http://msdn.microsoft.com/library/cd7bace3-f8ec-4ee3-8a9f-2f217cdca9f2)   
 [Configurare le proprietà delle origini dati per un report &#40;Gestione report&#41;](../../reporting-services/report-data/configure-data-source-properties-for-a-report-report-manager.md)  
  
  

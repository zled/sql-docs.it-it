---
title: Amministrare un database del server di report (modalità nativa SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- report servers [Reporting Services], databases
- renaming databases
- report server database
- databases [Reporting Services], administering
- reportservertempdb
- reportserver database
ms.assetid: 97b2e1b5-3869-4766-97b9-9bf206b52262
caps.latest.revision: 63
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: ee0c8711727a4661a9f9ac7a75d9739d98afc1b4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055629"
---
# <a name="administer-a-report-server-database-ssrs-native-mode"></a>Amministrare un database del server di report (modalità nativa SSRS)
  In una distribuzione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] vengono utilizzati due database relazionali di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per l'archiviazione interna. Per impostazione predefinita, i database sono denominati ReportServer e ReportServerTempdb. ReportServerTempdb viene creato con il database primario del server di report e viene utilizzato per l'archiviazione di dati temporanei, informazioni sulla sessione e report memorizzati nella cache.  
  
 In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]l'amministrazione del database include le attività di backup e ripristino dei database del server di report e la gestione delle chiavi di crittografia utilizzate per crittografare e decrittografare i dati sensibili.  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono disponibili vari strumenti per l'amministrazione dei database del server di report.  
  
-   Per eseguire il backup o il ripristino del database del server di report, per spostare un database del server di report o per recuperare un database del server di report, è possibile usare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], i comandi [!INCLUDE[tsql](../../includes/tsql-md.md)] o le utilità della riga di comando del database. Per istruzioni, vedere [Spostamento di database del server di report in un altro computer &#40;modalità nativa SSRS&#41;](moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md) nella documentazione online di SQL Server.  
  
-   Per copiare il contenuto del database esistente in un altro database del server di report, è possibile collegare una copia di un database del server di report e utilizzarla con una diversa istanza del server di report. In alternativa, è possibile creare ed eseguire uno script che utilizza le chiamate SOAP per ricreare il contenuto del server di report in un nuovo database. È possibile usare l'utilità **rs** per eseguire lo script.  
  
-   Per gestire le connessioni tra il server di report e il database del server di report e per individuare il database utilizzato per una particolare istanza del server di report, è possibile utilizzare la pagina Impostazioni database dello strumento di configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Per ulteriori informazioni sulla connessione del server di report al database del server di report, vedere [configurare una connessione di Database Server di Report &#40;Gestione configurazione SSRS&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
## <a name="sql-server-login-and-database-permissions"></a>Autorizzazioni per l'accesso a SQL Server e per il database  
 I database del server di report vengono utilizzati internamente dal server di report. Le connessioni al database vengono eseguite dal servizio del server di report. È possibile usare lo strumento di configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] per configurare una connessione al database del server di report.  
  
 Le credenziali per la connessione del server di report al database possono essere l'account del servizio, un account utente locale o di dominio Windows o un utente del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Per stabilire una connessione, è necessario scegliere un account esistente poiché in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] gli account non vengono creati.  
  
 Viene creato automaticamente un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per il database del server di report per l'account specificato.  
  
 Anche le autorizzazioni al database vengono configurate automaticamente. Lo strumento di configurazione di Reporting Services assegnerà l'account o utente del database per il `Public` e `RSExecRole` ruoli per i database del server di report. Il `RSExecRole` fornisce le autorizzazioni per accedere alle tabelle del database e per l'esecuzione di stored procedure. Il `RSExecRole` viene creato nei database master e msdb quando si crea il database del server di report. Il `RSExecRole` è un membro del `db_owner` ruolo per i database del server report, consentendo al server di report aggiornare lo schema per supportare un processo di aggiornamento automatico.  
  
## <a name="naming-conventions-for-the-report-server-databases"></a>Convenzioni di denominazione per i database del server di report  
 Il nome del database primario deve essere conforme alle regole relative agli [Identificatori del database](../../relational-databases/databases/database-identifiers.md). Per il database temporaneo viene sempre utilizzato il nome del database primario del server di report, con il suffisso Tempdb. Non è possibile scegliere un nome diverso per il database temporaneo.  
  
 La ridenominazione di un database del server di report non è supportata, in quanto i database del server di report sono considerati componenti interni. La ridenominazione dei database del server di report genera errori. In particolare, se si rinomina il database primario, verrà visualizzato un messaggio di errore che indica che i nomi dei database non sono sincronizzati. Se si rinomina il database ReportServerTempdb, durante la successiva esecuzione di report verrà generato l'errore interno seguente:  
  
 "Errore interno nel server di report. Per altre informazioni, vedere il log degli errori. (rsInternalError)  
  
 Il nome di oggetto 'ReportServerTempDB.dbo.PersistedStream' non è valido."  
  
 Questo errore si verifica perché il nome ReportServerTempdb viene archiviato internamente e viene utilizzato dalle stored procedure per l'esecuzione di operazioni interne. Rinominare il database temporaneo impedisce pertanto il corretto funzionamento delle stored procedure.  
  
## <a name="enabling-snapshot-isolation-on-the-report-server-database"></a>Attivazione dell'isolamento dello snapshot nel database del server di report  
 Nel database del server di report non è possibile attivare l'isolamento dello snapshot. Se l'isolamento dello snapshot è attivato, verrà visualizzato l'errore seguente: "Il report selezionato non è pronto per la visualizzazione. Il rendering del report è ancora in corso oppure non è disponibile uno snapshot del report".  
  
 Se non si attiva intenzionalmente l'isolamento dello snapshot, è probabile che l'attributo sia stato impostato da un'altra applicazione o che per il database **modello** sia stato attivato l'isolamento dello snapshot, facendo in modo che tutti i nuovi database ereditino l'impostazione.  
  
 Per disattivare l'isolamento dello snapshot sul il database del server di report, avviare Management Studio, aprire una nuova finestra della query, incollare, quindi eseguire lo script seguente:  
  
```  
ALTER DATABASE ReportServer  
SET ALLOW_SNAPSHOT_ISOLATION OFF  
ALTER DATABASE ReportServerTempdb  
SET ALLOW_SNAPSHOT_ISOLATION OFF  
ALTER DATABASE ReportServer  
SET READ_COMMITTED_SNAPSHOT OFF  
ALTER DATABASE ReportServerTempDb  
SET READ_COMMITTED_SNAPSHOT OFF  
```  
  
## <a name="about-database-versions"></a>Informazioni sulle versioni del database  
 In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]non sono disponibili informazioni esplicite sulla versione del database. Tuttavia, poiché le versioni del database sono sempre sincronizzate con le versioni del prodotto, è possibile utilizzare le informazioni relative alla versione del prodotto per stabilire quando la versione del database è stata modificata. Informazioni sulla versione del prodotto [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] è indicata tramite le informazioni sulla versione di file che viene visualizzato nei file di log, nelle intestazioni di tutte le chiamate SOAP, e quando ci si connette all'URL del server di report (ad esempio, quando si apre un browser per http://localhost/reportserver).  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione configurazione Reporting Services &#40;modalità nativa&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)   
 [Creare un database del Server di Report in modalità nativa &#40;Gestione configurazione SSRS&#41;](../install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Configurare l'Account del servizio ReportServer &#40;Gestione configurazione SSRS&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Configurare una connessione di Database Server di Report &#40;Gestione configurazione SSRS&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Creare un database del Server di Report &#40;Gestione configurazione SSRS&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)   
 [Operazioni di backup e ripristino per Reporting Services](../install-windows/backup-and-restore-operations-for-reporting-services.md)   
 [Database del Server di report &#40;modalità nativa SSRS&#41;](report-server-database-ssrs-native-mode.md)   
 [Server di report di Reporting Services &#40;modalità nativa&#41;](reporting-services-report-server-native-mode.md)   
 [Archiviare i dati crittografati del server di report &#40;Gestione configurazione SSRS &#41;](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md)   
 [Configurare e gestire chiavi di crittografia &#40;Gestione configurazione SSRS&#41;](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md)  
  
  
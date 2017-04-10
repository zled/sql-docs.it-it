---
title: "Configurare e gestire Advanced Analytics Extensions | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "11/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8d73fd98-0c61-4a62-94bb-75658195f2a6
caps.latest.revision: 21
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 20
---
# Configurare e gestire Advanced Analytics Extensions
  Dopo aver installato [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], è possibile apportare piccole modifiche alla configurazione del runtime di R e di altri servizi associati con [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] .  
  
  
 **Contenuto dell'argomento**  
  
-   [Provisioning di account utente per SQL Server R Services](#bkmk_Provisioning)  
  
-   [Gestione dell'uso della memoria da parte dei processi R](#bkmk_ManagingMemory)  
  
-   [Modifica delle impostazioni predefinite del servizio mediante il file di configurazione](#bkmk_ChangingConfig) 

-   [Modifica l'Account del servizio di avvio](#bkmk_Launchpad) 
  
##  <a name="bkmk_Provisioning"></a> Provisioning di account utente per SQL Server R Services  
 R elaborati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eseguito nel contesto dell'account utente locale con privilegi limitati. Eseguire processi del runtime di R in account individuali con privilegi limitati presenta i seguenti vantaggi:  
  
-   Minori privilegi per i processi del runtime di R eseguiti sul computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
  
-   Isolamento fra le sessioni del runtime di R  
  
 Come parte del processo di installazione in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], un nuovo Windows *pool di account utente* viene creato che contiene gli account utente locali necessari per l'esecuzione del processo di runtime di R. È possibile modificare il numero di utenti, se necessario per supportare R. L'amministratore del database necessario anche assegnare questo gruppo l'autorizzazione per connettersi a qualsiasi istanza in cui è stato abilitato Servizi R. Per ulteriori informazioni, vedere [modificare il Pool degli Account utente per i servizi di SQL Server R](../../advanced-analytics/r-services/modify-the-user-account-pool-for-sql-server-r-services.md).  
  
 Tuttavia, un elenco di controllo di accesso (ACL) può essere definito per le risorse riservate nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per negare l'accesso a questo gruppo per impedire l'accesso alle risorse del processo di runtime di R.  
  
-   Il pool degli account utente è collegato a un'istanza specifica.  Gli account vengono creati per ogni istanza in cui R script è stato abilitato, un pool di lavoro separato. Gli account non possono essere condivisi tra le istanze.
  
-   I nomi degli account utente nel pool sono nel formato SQLInstanceName*nn*. Ad esempio, se si usa l'istanza predefinita come server R, il pool di account utente supporta nomi di account come MSSQLSERVER01, MSSQLSERVER02 e così via.  
  
-   La dimensione del pool di account utente è statica e il valore predefinito è 20. Il numero delle sessioni del runtime di R che possono essere avviate simultaneamente è limitato dalla dimensione di questo pool di account utente. Tuttavia, questo limite può essere modificato da un amministratore tramite Gestione configurazione SQL Server.  
  
  
 Per altre informazioni su come apportare modifiche al pool di account utente, vedere [Modify the User Account Pool for SQL Server R Services](../../advanced-analytics/r-services/modify-the-user-account-pool-for-sql-server-r-services.md).  
  
##  <a name="bkmk_ManagingMemory"></a> Gestione dell'uso della memoria da parte dei processi R  
 Per impostazione predefinita, i processi del runtime di R associati con [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] sono limitati all'uso di non più del 20% della memoria totale del computer. Se necessario, l'amministratore può aumentare il valore di questo limite.  
  
 In genere, questo valore sarà adeguato per le attività di R grave, ad esempio training del modello o stima sul numero di righe di dati. Potrebbe essere necessario ridurre la quantità di memoria riservata per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (o per altri servizi) e utilizzare Resource Governor per definire un pool di risorse esterni o i pool e allocare. Per ulteriori informazioni, vedere [governance delle risorse per i servizi di R](../../advanced-analytics/r-services/resource-governance-for-r-services.md).  
  
##  <a name="bkmk_ChangingConfig"></a> Modifica delle opzioni di servizio avanzate utilizzando il File di configurazione  
 
È possibile controllare alcune proprietà avanzate del [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] modificando il [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] file di configurazione. Questo file viene creato durante la configurazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e per impostazione predefinita viene salvato come file di solo testo nel seguente percorso:  
 
```  
<instance path>\binn\rlauncher.config  
```  
  
 Per poter apportare modifiche a questo file è necessario essere amministratore del computer su cui è eseguito [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Se si decide di modificare il file, si consiglia di crearne una copia di backup prima di salvare le modifiche.  
  
 Ad esempio, se si vuole usare Blocco note per aprire il file di configurazione per l'istanza predefinita (MSSQLSERVER), è possibile aprire un prompt dei comandi come amministratore e digitare il comando seguente:  
  
```  
C:\>Notepad.exe "%programfiles%\Microsoft SQL Server\MSSQL13.MSSQLSERVER\mssql\binn\rlauncher.config"  
  
```  
  
###  <a name="bkmk_properties"></a> Proprietà di configurazione  
 Tutte le impostazioni assumono la forma di coppie chiave-valore e ogni impostazione si trova su una riga diversa. Ad esempio, questa proprietà specifica che non più del 20% della memoria del sistema può essere usata dai processi R:  
  
 Impostazione predefinita: `MEMORY_LIMIT_PERCENT=20`  
  
 Nella tabella seguente sono elencati ognuna delle impostazioni supportate per [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], con i valori consentiti.  
  
|Nome impostazione|Tipo valore|Valore predefinito|Descrizione|  
|------------------|----------------|-------------|-----------------|  
|JOB_CLEANUP_ON_EXIT|Integer<br /><br /> 0 = Disabilitato<br /><br /> 1 = Attivato|1<br /><br /> I file di log sono rimossi all'uscita|Specifica se la cartella di lavoro temporanea creata per ciascuna sessione R deve essere eliminata dopo che la sessione R è terminata. L'impostazione è utile per il debug.<br /><br /> Nota: questa è un'impostazione esclusivamente interna, perciò questo valore non deve essere modificato.|  
|TRACE_LEVEL|Integer<br /><br /> 1 = Errore<br /><br /> 2 = prestazioni<br /><br /> 3 = avviso<br /><br /> 4 = informazioni|1<br /><br /> Solo avvisi di output|Configura il livello di dettaglio della traccia dell'utilità di avvio di R (MSSQLLAUNCHPAD) per scopi di debug. Questa impostazione influisce sul dettaglio delle tracce archiviate nei seguenti file di traccia, entrambi posizionati nel percorso specificato dall'impostazione LOG_DIRECTORY:<br /><br /> **rlauncher.log**: il file di traccia generato per le sessioni R avviate da query T-SQL.<br /><br /> Per ulteriori informazioni su questo scenario, vedere [Data Exploration and Predictive Modeling with R](../../advanced-analytics/r-services/data-exploration-and-predictive-modeling-with-r.md).|  

## <a name="bkmk_Launchpad"></a>Modifica l'Account del servizio di avvio

Un oggetto separato [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] servizio viene creato per ogni istanza in cui è stato configurato [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)]. 

Per impostazione predefinita, la finestra di avvio è configurato per essere eseguito utilizzando l'account NT Service\MSSQLLaunchpad, che viene eseguito il provisioning con tutte le autorizzazioni necessarie per eseguire gli script R. Tuttavia, se si modifica questo account, la finestra di avvio non potrebbe essere possibile avviare o per accedere all'istanza di SQL Server in cui eseguire gli script R.
 
  Se si modifica l'account del servizio, assicurarsi di utilizzare il **criteri di sicurezza locali** applicazione e aggiornamento per includere le autorizzazioni dell'account le autorizzazioni per ogni servizio:
  + Regolazione quote di memoria per un processo (SeIncreaseQuotaPrivilege)
  + Ignorare controllo incrociato (SeChangeNotifyPrivilege)
  + Accesso come servizio (SeServiceLogonRight)
  + Sostituzione di token a livello di processo (SeAssignPrimaryTokenPrivilege)

Per ulteriori informazioni sulle autorizzazioni necessarie per eseguire i servizi di SQL Server, vedere [Configura account di servizio Windows e le autorizzazioni](https://msdn.microsoft.com/library/ms143504.aspx#Windows).
   
## Vedere anche  
 [Introduzione a SQL Server R Services](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md)  
  
  
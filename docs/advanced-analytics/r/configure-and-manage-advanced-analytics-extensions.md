---
title: Configurazione opzioni avanzate per servizi di Machine Learning | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 11/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d73fd98-0c61-4a62-94bb-75658195f2a6
caps.latest.revision: 21
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 872acf107d72989b4623a9d5f4ccb85c44d1f2f9
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="advanced-configuration-options-for-machine-learning-services"></a>Configurazione opzioni avanzate per i servizi di Machine Learning

Questo articolo descrive le modifiche apportate dopo l'installazione, per modificare la configurazione del runtime di R e altri servizi associati con machine learning in SQL Server.

Si applica a: R Services SQL Server 2016, SQL Server 2017 di Machine Learning Services

##  <a name="bkmk_Provisioning"></a>E account utente di effettuare il provisioning per computer apprendimento

Processi di script esterni in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eseguiti nel contesto dell'account utente locale con privilegi limitati. Questi processi in esecuzione in singoli account con privilegi limitati presenta i vantaggi seguenti:

+ Consente di ridurre i privilegi dei processi di runtime dello script esterno nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer
+ Fornisce l'isolamento tra le sessioni di un runtime esterni, ad esempio R o Python.

Come parte del programma di installazione, una nuova finestra *pool di account utente* viene creato che contiene gli account utente locali necessari per l'esecuzione del processo di runtime di R. Se necessario, è possibile modificare il numero di utenti per supportare R. L'amministratore del database deve anche concedere a questo gruppo l'autorizzazione necessaria per connettersi a qualsiasi istanza in cui è stato abilitato R Services. Per altre informazioni, vedere [Modify the User Account Pool for SQL Server R Services](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md).

Tuttavia, è possibile definire un elenco di controllo di accesso (ACL) per le risorse sensibili in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per negare l'accesso a questo gruppo, in modo da impedire al processo di runtime R di ottenere l'accesso alle risorse.

+ Il pool di account utente è collegato a un'istanza specifica.  Per ogni istanza in cui è stato abilitato uno script R, viene creato un pool di account di lavoro separato. Gli account non possono essere condivisi tra istanze.

+ I nomi degli account utente nel pool sono nel formato SQLInstanceName*nn*. Ad esempio, se si usa l'istanza predefinita come server R, il pool di account utente supporta nomi di account come MSSQLSERVER01, MSSQLSERVER02 e così via.

+ La dimensione del pool di account utente è statica e il valore predefinito è 20. Il numero delle sessioni del runtime di R che possono essere avviate simultaneamente è limitato dalla dimensione di questo pool di account utente. Questo limite può tuttavia essere modificato da un amministratore tramite Gestione configurazione SQL Server.

Per altre informazioni su come apportare modifiche al pool di account utente, vedere [Modify the User Account Pool for SQL Server R Services](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md).

##  <a name="bkmk_ManagingMemory"></a>Gestire la memoria utilizzata dai processi di Script esterni

Per impostazione predefinita, i processi del runtime di R associati con [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] sono limitati all'uso di non più del 20% della memoria totale del computer. Se necessario, l'amministratore può aumentare il valore di questo limite.

In generale, questa quantità sarà inadeguata per attività R importanti, come il training di modelli o la stima su molte righe di dati. Potrebbe essere necessario ridurre la quantità di memoria riservata per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (o per altri servizi) e usare Resource Governor per definire uno o più pool di risorse esterne e allocarli. Per ulteriori informazioni, vedere [governance delle risorse per R](../../advanced-analytics/r/resource-governance-for-r-services.md).

##  <a name="bkmk_ChangingConfig"></a>Modifica servizio opzioni avanzate utilizzando il File di configurazione

È possibile controllare alcune proprietà avanzate di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] modificando il file di configurazione di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Questo file viene creato durante la configurazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e per impostazione predefinita viene salvato come file di solo testo nel seguente percorso:

`<instance path>\binn\rlauncher.config`

Per poter apportare modifiche a questo file è necessario essere amministratore del computer su cui è eseguito [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Se si decide di modificare il file, si consiglia di crearne una copia di backup prima di salvare le modifiche.

Ad esempio, per utilizzare Blocco note per aprire il file di configurazione per l'istanza predefinita, si potrebbe aprire un prompt dei comandi come amministratore e digitare il comando seguente:

```
C:\>Notepad.exe "%programfiles%\Microsoft SQL Server\MSSQL13.MSSQLSERVER\mssql\binn\rlauncher.config"  
```

##  <a name="bkmk_properties"></a>Modificare le proprietà di configurazione

La tabella seguente elenca tutte le impostazioni supportate per [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], con i valori consentiti.

Tutte le impostazioni assumono la forma di coppie chiave-valore e ogni impostazione si trova su una riga diversa. Ad esempio, questa proprietà specifica il livello di traccia per RLauncher:

Impostazione predefinita: TRACE_LEVEL=4


|**Nome impostazione**|**Tipo valore**|**Valore predefinito**|**Descrizione**|
|------------------|----------------|-------------|-----------------|
|JOB_CLEANUP_ON_EXIT|Integer<br /><br /> 0 = Disabilitato<br /><br /> 1 = Attivato|1<br /><br /> I file di log sono rimossi all'uscita|Specifica se la cartella di lavoro temporanea creata per ciascuna sessione R deve essere eliminata dopo che la sessione R è terminata. L'impostazione è utile per il debug.<br /><br /> Nota: questa è un'impostazione esclusivamente interna, perciò questo valore non deve essere modificato.|
|TRACE_LEVEL|Integer<br /><br /> 1 = Errore<br /><br /> 2 = Prestazioni<br /><br /> 3 = Avviso<br /><br /> 4 = Informazioni|1<br /><br /> Solo avvisi di output|Configura il livello di dettaglio della traccia dell'utilità di avvio di R (MSSQLLAUNCHPAD) per scopi di debug. Questa impostazione influisce sul dettaglio delle tracce archiviate nei seguenti file di traccia, entrambi posizionati nel percorso specificato dall'impostazione LOG_DIRECTORY:<br /><br /> **rlauncher.log**: il file di traccia generato per le sessioni R avviate da query T-SQL.<br /><br /> |

## <a name="bkmk_Launchpad"></a>Modificare l'Account del servizio Launchpad

Un oggetto separato [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] servizio viene creato per ogni istanza in cui è stato configurato di machine learning services.

Per impostazione predefinita, Launchpad è configurato per l'esecuzione con l'account NT Service\MSSQLLaunchpad, cui vengono concesse tutte le autorizzazioni necessarie per l'esecuzione di script R. Tuttavia, se si modifica questo account, la finestra di avvio potrebbe non essere in grado di avviare o per accedere all'istanza di SQL Server in cui eseguire gli script esterni.

Se si modifica l'account del servizio, assicurarsi di usare l'applicazione **Criteri di sicurezza locali** e di aggiornare le autorizzazioni per ogni account del servizio in modo da includere le seguenti:

+ Regolazione quote di memoria per un processo (SeIncreaseQuotaPrivilege)
+ Ignorare controllo incrociato (SeChangeNotifyPrivilege)
+ Accesso come servizio (SeServiceLogonRight)
+ Sostituzione di token a livello di processo (SeAssignPrimaryTokenPrivilege)

Per altre informazioni sulle autorizzazioni necessarie per l'esecuzione di servizi di SQL Server, vedere [Configurare account di servizio e autorizzazioni di Windows](https://msdn.microsoft.com/library/ms143504.aspx#Windows).

## <a name="see-also"></a>Vedere anche

[Considerazioni sulla sicurezza](security-considerations-for-the-r-runtime-in-sql-server.md)


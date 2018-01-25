---
title: Configurazione opzioni avanzate per servizi di Machine Learning | Documenti Microsoft
ms.custom: SQL2016_New_Updated
ms.date: 10/31/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d73fd98-0c61-4a62-94bb-75658195f2a6
caps.latest.revision: "21"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: f8a886e48067c80f112e86c9d7ba07da79502691
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="advanced-configuration-options-for-machine-learning-services"></a>Opzioni di configurazione avanzate per i servizi di Machine Learning

Questo articolo descrive le modifiche apportate dopo l'installazione, per modificare la configurazione di runtime dello script esterno e altri servizi associati con machine learning in SQL Server.

**Si applica a:** R Services SQL Server 2016, SQL Server 2017 di Machine Learning Services

##  <a name="bkmk_Provisioning"></a>Eseguire il provisioning aggiuntive gli account utente per la macchina apprendimento

Processi di script esterni in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eseguiti nel contesto dell'account utente locale con privilegi limitati. Questi processi in esecuzione in singoli account con privilegi limitati presenta i vantaggi seguenti:

+ Consente di ridurre i privilegi dei processi di runtime dello script esterno nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer
+ Fornisce l'isolamento tra le sessioni di un runtime esterni, ad esempio R o Python.

Come parte del programma di installazione, una nuova finestra *pool di account utente* viene creato che contiene gli account utente locali necessari per l'esecuzione di processi di runtime esterni, ad esempio R o Python. È possibile modificare il numero di utenti in base alle esigenze per supportare l'attività di machine learning. 

Inoltre, l'amministratore del database è necessario assegnare questo gruppo l'autorizzazione per connettersi a qualsiasi istanza in cui è stato attivato l'apprendimento. Per ulteriori informazioni, vedere [modificare il pool di account utente per i servizi di SQL Server Machine Learning](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md).

Alle risorse sensibili protext il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è possibile definire un elenco di controllo di accesso (ACL) per questo gruppo. Specificando le risorse che il gruppo viene negato l'accesso, è possibile impedire l'accesso da processi esterni, ad esempio i runtime R o Python.

+ Il pool di account utente è collegato a un'istanza specifica. Per ogni istanza del computer in cui è stata abilitata l'apprendimento, è necessario un pool separato di account di lavoro. Gli account non possono essere condivisi tra istanze.

+ I nomi degli account utente nel pool sono nel formato SQLInstanceName*nn*. Ad esempio, se si utilizza l'istanza predefinita per machine learning, il pool di account utente supporta nomi di account come MSSQLSERVER01, MSSQLSERVER02 e così via.

+ La dimensione del pool di account utente è statica e il valore predefinito è 20. Il numero di sessioni di runtime esterno che possono essere avviate simultaneamente è limitato dalle dimensioni del pool di account utente. Per modificare questo limite, un amministratore deve utilizzare Gestione configurazione SQL Server.

Per ulteriori informazioni su come apportare modifiche al pool di account utente, vedere [modificare il pool di account utente per i servizi di SQL Server Machine Learning](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md).

##  <a name="bkmk_ManagingMemory"></a>Gestire la memoria utilizzata dai processi di script esterni

Per impostazione predefinita, i runtime dello script esterno per machine learning sono limitati a non più del 20% della memoria totale del computer. Dipende dal sistema, ma in generale, si noterà questo limite non adeguato per le attività di apprendimento macchina grave, ad esempio training di un modello o stima su molte righe di dati. 

Per supportare l'apprendimento, un amministratore può aumentare questo limite. Quando si esegue questa operazione, potrebbe essere necessario ridurre la quantità di memoria riservata per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o per altri servizi. È consigliabile l'utilizzo di Resource Governor per definire un pool di risorse esterne o pool, in modo che è possibile allocare il pool di risorse specifiche per i processi R o Python.

Per ulteriori informazioni, vedere [governance delle risorse per machine learning](../../advanced-analytics/r/resource-governance-for-r-services.md).


## <a name="bkmk_Launchpad"></a>Modificare l'account del servizio Launchpad

Un oggetto separato [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] servizio viene creato per ogni istanza in cui è stato configurato di machine learning services.

Per impostazione predefinita, Launchpad è configurato per l'esecuzione con l'account NT Service\MSSQLLaunchpad, cui vengono concesse tutte le autorizzazioni necessarie per l'esecuzione di script R. Tuttavia, se si modifica questo account, la finestra di avvio potrebbe non essere in grado di avviare o per accedere all'istanza di SQL Server in cui eseguire gli script esterni.

Se si modifica l'account del servizio, assicurarsi di usare l'applicazione **Criteri di sicurezza locali** e di aggiornare le autorizzazioni per ogni account del servizio in modo da includere le seguenti:

+ Regolazione quote di memoria per un processo (SeIncreaseQuotaPrivilege)
+ Ignorare controllo incrociato (SeChangeNotifyPrivilege)
+ Accesso come servizio (SeServiceLogonRight)
+ Sostituzione di token a livello di processo (SeAssignPrimaryTokenPrivilege)

Per altre informazioni sulle autorizzazioni necessarie per l'esecuzione di servizi di SQL Server, vedere [Configurare account di servizio e autorizzazioni di Windows](https://msdn.microsoft.com/library/ms143504.aspx#Windows).

##  <a name="bkmk_ChangingConfig"></a>Modificare le opzioni avanzate del servizio

Nelle versioni precedenti di SQL Server 2016 R Services, è possibile modificare alcune proprietà del servizio modificando la [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] file di configurazione. 

Tuttavia, questo file non è più utilizzato per la modifica delle configurazioni. È consigliabile utilizzare Gestione configurazione SQL Server per le modifiche alla configurazione del servizio, ad esempio l'account del servizio e il numero di utenti.

**Per modificare la configurazione di avvio**

1. Aprire [Gestione configurazione SQL Server](../../relational-databases/sql-server-configuration-manager.md). 
2. Finestra di avvio di SQL Server e scegliere **proprietà**.

    + Per modificare l'account del servizio, scegliere il **accesso** scheda.

    + Per aumentare il numero di utenti, fare clic su di **avanzate** scheda.


**Per modificare le impostazioni di debug**

Proprietà alcuni possono essere modificate solo tramite la file di configurazione del finestra di avvio che potrebbe essere utili in alcuni casi, ad esempio il debug. Il file di configurazione viene creato durante [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] del programma di installazione e per impostazione predefinita viene salvato come file di testo normale nel percorso seguente:`<instance path>\binn\rlauncher.config`

Per poter apportare modifiche a questo file è necessario essere amministratore del computer su cui è eseguito [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Se si decide di modificare il file, si consiglia di crearne una copia di backup prima di salvare le modifiche.

La tabella seguente elenca le impostazioni avanzate per [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], con i valori consentiti. 

|**Nome impostazione**|**Tipo**|**Description**|
|----|----|----|
|PROCESSO\_PULIZIA\_ON\_USCITA|Integer |Questa è un'impostazione esclusivamente interna, non modificare questo valore. </br></br>Specifica se la cartella di lavoro temporanea creata per ogni sessione di runtime esterno deve essere pulita al termine della sessione. L'impostazione è utile per il debug. </br></br>Valori supportati sono **0** (disattivato) o **1** (abilitato). </br></br>Il valore predefinito è 1, i file di log di significato sono rimossi all'uscita.|
|TRACCIA\_LIVELLO|Integer |Consente di configurare il livello di dettaglio di traccia di MSSQLLAUNCHPAD a scopo di debug. Ciò influisce sui file di traccia nel percorso specificato dall'impostazione LOG_DIRECTORY. </br></br>Valori supportati sono: **1** (errore), **2** (prestazioni), **3** (avviso), **4** (informazioni). </br></br>Il valore predefinito è 1, vale a dire solo avvisi di output.|

Tutte le impostazioni assumono la forma di coppie chiave-valore e ogni impostazione si trova su una riga diversa. Ad esempio, per modificare il livello di traccia, aggiungere la riga `Default: TRACE_LEVEL=4`.

## <a name="see-also"></a>Vedere anche

[Considerazioni sulla sicurezza](security-considerations-for-the-r-runtime-in-sql-server.md)

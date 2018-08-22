---
title: Configurazione avanzata per servizi di SQL Server Machine Learning | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 8384773f6db4c0ced2fc68e52cd78100c98c52fd
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2018
ms.locfileid: "40396300"
---
# <a name="advanced-configuration-options-for-sql-server-machine-learning-services"></a>Opzioni di configurazione avanzate per SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo descrive le modifiche che è possibile apportare al termine dell'installazione, per modificare la configurazione di runtime dello script esterno e altri servizi associati con machine learning in SQL Server.

**Si applica a:** SQL Server 2016 R Services, SQL Server 2017 Machine Learning Services

##  <a name="bkmk_Provisioning"></a> E account utente aggiuntivi per machine learning

Processi di script esterni nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eseguiti nel contesto dell'account utente locali con privilegi limitati. Questi processi in esecuzione in account individuali con privilegi limitati presenta i vantaggi seguenti:

+ Consente di ridurre i privilegi dei processi di runtime dello script esterno nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer
+ Fornisce l'isolamento tra le sessioni di un runtime esterno, ad esempio R o Python.

Come parte del programma di installazione, un nuovo Windows *pool di account utente* creato che contiene gli account utente locali necessari per l'esecuzione di processi del runtime esterni, ad esempio R o Python. È possibile modificare il numero di utenti in base alle esigenze per supportare attività di machine learning. 

Inoltre, l'amministratore del database deve assegnare questo gruppo l'autorizzazione per connettersi a qualsiasi istanza in cui è stato attivato l'apprendimento automatico. Per altre informazioni, vedere [modificare il pool di account utente per SQL Server Machine Learning Services](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md).

Alle risorse sensibili protext il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è possibile definire un elenco di controllo di accesso (ACL) per questo gruppo. Specifica le risorse che il gruppo viene negato l'accesso, si può impedire l'accesso da processi esterni, ad esempio i runtime di R o Python.

+ Il pool di account utente è collegato a un'istanza specifica. Per ogni istanza del computer in cui è stata abilitata l'apprendimento, è necessario un pool separato di account di lavoro. Gli account non possono essere condivisi tra istanze.

+ I nomi degli account utente nel pool sono nel formato SQLInstanceName*nn*. Ad esempio, se si usa l'istanza predefinita per machine learning, il pool di account utente supporta nomi di account come MSSQLSERVER01, MSSQLSERVER02 e così via.

+ La dimensione del pool di account utente è statica e il valore predefinito è 20. Il numero di sessioni del runtime esterni che possono essere avviate simultaneamente è limitato dalle dimensioni del pool di account utente. Per modificare questo limite, un amministratore deve utilizzare Gestione configurazione SQL Server.

Per altre informazioni su come apportare modifiche al pool di account utente, vedere [modificare il pool di account utente per SQL Server Machine Learning Services](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md).

##  <a name="bkmk_ManagingMemory"></a> Gestire la memoria usata dai processi di script esterni

Per impostazione predefinita, i runtime dello script esterno per machine learning sono limitati a non più di 20% della memoria totale del computer. Dipende dal sistema, ma in generale, si potrà trovare questo limite inadeguata per attività di apprendimento automatico gravi, ad esempio un modello di training o la stima su molte righe di dati. 

Per supportare l'apprendimento automatico, un amministratore può aumentare questo limite. Quando si esegue questa operazione, potrebbe essere necessario ridurre la quantità di memoria riservata per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o per altri servizi. Considerare inoltre l'utilizzo di Resource Governor consente di definire un pool di risorse esterne o i pool, in modo che è possibile allocare pool di risorse specifico per i processi R o Python.

Per altre informazioni, vedere [governance delle risorse per machine learning](../../advanced-analytics/r/resource-governance-for-r-services.md).


## <a name="bkmk_Launchpad"></a>Modificare l'account del servizio Launchpad

Un oggetto separato [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] servizio viene creato per ogni istanza in cui è stato configurato i servizi di machine learning.

Per impostazione predefinita, Launchpad è configurato per l'esecuzione con l'account NT Service\MSSQLLaunchpad, cui vengono concesse tutte le autorizzazioni necessarie per l'esecuzione di script R. Tuttavia, se si modifica questo account, Launchpad potrebbe non essere in grado di avviare o per accedere all'istanza di SQL Server in cui gli script esterni devono essere eseguiti.

Se si modifica l'account del servizio, assicurarsi di usare l'applicazione **Criteri di sicurezza locali** e di aggiornare le autorizzazioni per ogni account del servizio in modo da includere le seguenti:

+ Regolazione quote di memoria per un processo (SeIncreaseQuotaPrivilege)
+ Ignorare controllo incrociato (SeChangeNotifyPrivilege)
+ Accesso come servizio (SeServiceLogonRight)
+ Sostituzione di token a livello di processo (SeAssignPrimaryTokenPrivilege)

Per altre informazioni sulle autorizzazioni necessarie per l'esecuzione di servizi di SQL Server, vedere [Configurare account di servizio e autorizzazioni di Windows](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).

##  <a name="bkmk_ChangingConfig"></a> Modificare le opzioni avanzate del servizio

Nelle prime versioni di SQL Server 2016 R Services, è possibile modificare alcune proprietà del servizio modificando il [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] file di configurazione. 

Tuttavia, questo file non è più viene usato per la modifica delle configurazioni. È consigliabile utilizzare Gestione configurazione SQL Server per le modifiche alla configurazione del servizio, ad esempio l'account del servizio e il numero di utenti.

**Per modificare la configurazione di Launchpad**

1. Aprire [Gestione configurazione SQL Server](../../relational-databases/sql-server-configuration-manager.md). 
2. Fare doppio clic su Launchpad di SQL Server e selezionare **proprietà**.

    + Per modificare l'account del servizio, scegliere il **Accedi** scheda.

    + Per aumentare il numero di utenti, selezionare la **avanzate** scheda.


**Per modificare le impostazioni di debug**

Alcune proprietà possono essere modificate solo tramite file di configurazione della finestra di avvio, che potrebbe essere utile in alcuni casi, ad esempio il debug. Il file di configurazione viene creato durante [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di installazione e per impostazione predefinita viene salvato come file di testo normale nel percorso seguente: `<instance path>\binn\rlauncher.config`

Per poter apportare modifiche a questo file è necessario essere amministratore del computer su cui è eseguito [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Se si decide di modificare il file, si consiglia di crearne una copia di backup prima di salvare le modifiche.

La tabella seguente elenca le impostazioni avanzate per [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], con i valori consentiti. 

|**Nome impostazione**|**Tipo**|**Descrizione**|
|----|----|----|
|PROCESSO\_PULIZIA\_VIA\_ESCI|Valore intero |Si tratta di un'impostazione esclusivamente interna: non modificare questo valore. </br></br>Specifica se la cartella di lavoro temporanea creata per ogni sessione runtime esterni deve essere pulita dopo il completamento della sessione. L'impostazione è utile per il debug. </br></br>I valori supportati sono **0** (disabilitato) o **1** (abilitato). </br></br>Il valore predefinito è 1, i file di log significato sono rimossi all'uscita.|
|TRACCIA\_LIVELLO|Valore intero |Consente di configurare il livello di dettaglio di traccia di MSSQLLAUNCHPAD a scopo di debug. Ciò influisce sui file di traccia nel percorso specificato dall'impostazione LOG_DIRECTORY. </br></br>I valori supportati sono: **1** (errore), **2** (prestazioni), **3** (avviso), **4** (informazioni). </br></br>Il valore predefinito è 1, vale a dire solo avvisi di output.|

Tutte le impostazioni assumono la forma di coppie chiave-valore e ogni impostazione si trova su una riga diversa. Per modificare il livello di traccia, ad esempio, si potrebbe aggiungere la riga `Default: TRACE_LEVEL=4`.

## <a name="see-also"></a>Vedere anche

[Considerazioni sulla sicurezza](security-considerations-for-the-r-runtime-in-sql-server.md)

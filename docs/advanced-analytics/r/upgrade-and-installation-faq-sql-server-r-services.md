---
title: Domande frequenti sull'installazione e aggiornamento per SQL Server Machine Learning | Documenti Microsoft
ms.date: 10/31/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 001e66b9-6c3f-41b3-81b7-46541e15f9ea
caps.latest.revision: "59"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: f0c6aac38001506b51ff7d14307f23b461334eb7
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2017
---
# <a name="upgrade-and-installation-faq-for-sql-server-machine-learning"></a>Domande frequenti sull'installazione e aggiornamento per l'apprendimento automatico di SQL Server

In questo argomento fornisce le risposte ad alcune domande comuni sull'installazione di machine learning funzionalità in SQL Server. Vengono inoltre illustrate le domande frequenti sugli aggiornamenti.

+ Alcuni problemi si verificano solo con gli aggiornamenti da versioni non definitive. È pertanto consigliabile identificare la versione ed edizione innanzitutto prima di leggere le note.
+ Aggiornare la versione più recente o di un service release appena possibile, per risolvere eventuali problemi che sono stati risolti nelle versioni recenti.

**Si applica a:** R Services SQL Server 2016, SQL Server 2017 di Machine Learning Services (In-Database)

## <a name="performing-setup-for-the-first-time"></a>Eseguire il programma di installazione per la prima volta

Seguire le procedure per l'impostazione [!INCLUDE[sscurrent_md](../../includes/sscurrent_md.md)] e i componenti di R, come descritto di seguito: 

+ [Configurare SQL Server R Services o di Machine Learning Services nel Database](../r/set-up-sql-server-r-services-in-database.md)
+ [Configurare SQL Server 2017 con Python](../python/setup-python-machine-learning-services.md)
+ [Creare un Server R autonomo](../r/create-a-standalone-r-server.md)

> [!IMPORTANT]
> 
> Dopo aver installato SQL Server e machine learning funzionalità, prima di poter usare gli script R o Python, è necessario completare alcuni passaggi di configurazione aggiuntive. Ciò avviene perché la funzionalità di esecuzione dello script esterno non è abilitata per impostazione predefinita.

### <a name="requirements-and-restrictions"></a>Requisiti e restrizioni

A seconda della compilazione di SQL Server che si sta installando, potrebbe applicare limitazioni seguenti:

- Nelle versioni precedenti di SQL Server 2016 R Services, è necessaria la notazione 8dot3 sull'unità contenente la directory di lavoro. Se è installata una versione non definitiva, l'aggiornamento a SQL Server 2016 Service Pack 1 dovrebbe risolvere il problema. Questo requisito non si applica alle versioni dopo SP1.

- Attualmente, non è possibile installare [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] in un cluster di failover. 

- In una macchina virtuale di Azure, alcune configurazioni aggiuntive potrebbero essere necessario. È ad esempio, potrebbe essere necessario creare un'eccezione del firewall per supportare l'accesso remoto.

- Installazione side-by-side con un'altra versione di R, o con altre versioni di Revolution Analitica, non è supportata.

- La nuova installazione di una versione non definitiva di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] non è più supportata. Se si utilizza una versione non definitiva, eseguire l'aggiornamento appena possibile.

- Disabilitare antivirus prima di iniziare l'installazione. Al termine dell'installazione, si consiglia di sospendere la ricerca dei virus nelle cartelle utilizzate da [!INCLUDE[ssnoversion](../../includes/ssnoversion.md)]. Preferibilmente, sospendere l'analisi dell'intero [!INCLUDE[ssnoversion](../../includes/ssnoversion.md)] struttura ad albero.

### <a name="licensing-agreements-for-unattended-installs"></a>Contratti di licenza per le installazioni automatiche

Se si utilizza la riga di comando per aggiornare un'istanza di SQL Server, assicurarsi che la riga di comando include sia il [!INCLUDE[ssnoversion](../../includes/ssnoversion.md)] le licenze di parametro del contratto e i nuovi parametri di contratto di licenza di R e Python.

### <a name="offline-installation-of-machine-learning-components-for-a-localized-version-of-sql-server"></a>Installazione offline di componenti di machine learning per una versione localizzata di SQL Server

Quando si installa [!INCLUDE[ssnoversion](../../includes/ssnoversion.md)] componenti di machine learning in un computer che non dispone dell'accesso a internet, è necessario eseguire alcuni passaggi aggiuntivi:

+ Scaricare i programmi di installazione di componenti R o Python in una cartella locale prima di eseguire il programma di installazione di SQL Server.
+ In alcuni casi, potrebbe essere necessario modificare il file di programma di installazione per verificare che sia installata nella lingua corretta.
+ L'identificatore della lingua utilizzata per il machine learning componenti deve essere lo stesso come lingua di installazione di SQL Server o è Impossibile completare l'installazione.

Per ulteriori informazioni, vedere [l'installazione dei componenti di machine learning senza accesso a internet](../r/installing-ml-components-without-internet-access.md).

## <a name="post-installation-configuration"></a>Configurazione post-installazione

Per utilizzare l'apprendimento con R o Python, è necessario un'ulteriore configurazione dopo l'installazione di SQL Server. La procedura dettagliata è necessario dipende dal livello di protezione del server e come sono stati configurati per l'istanza di SQL Server e un database.

Esaminare tutte le opzioni nell'elenco di istruzioni di post-installazione per verificare quali passaggi aggiuntivi potrebbero essere necessario nell'ambiente in uso.

+ [Configurare il computer SQL Server nel database di apprendimento](set-up-sql-server-r-services-in-database.md) 

## <a name="upgrades-or-uninstallation"></a>Gli aggiornamenti o la disinstallazione

In questa sezione contiene istruzioni dettagliate per scenari di aggiornamento specifici.

### <a name="how-to-upgrade-sql-server"></a>Come eseguire l'aggiornamento di SQL Server

È possibile aggiornare la versione di SQL Server eseguendo di nuovo l'installazione guidata.

+ [Eseguire l'aggiornamento di SQL Server](../../database-engine/install-windows/upgrade-sql-server.md)
+ [Aggiornamento di SQL Server tramite l'installazione guidata](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)

È possibile aggiornare solo di machine learning componenti tramite un processo denominato associazione: 
+ [Utilizzare SqlBindR per l'aggiornamento dei componenti di machine learning](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)

### <a name="end-of-support-for-in-place-upgrades-from-prerelease-versions"></a>Fine del supporto per gli aggiornamenti sul posto da versioni non definitive

Gli aggiornamenti da versioni non definitive di SQL Server 2016 non sono più supportati. Ciò include SQL Server 2016 CTP3, CTP 3.1, CTP 3.2, RC0 o RC1.

Le versioni seguenti sono state installate con le versioni non definitive di SQL Server 2016.

| Versione | Compilazione         |
|---------|---------------|
| CTP 3.0 | 13.0.xxx      |
| CTP 3.1 | 13.0.801.12   |
| CTP 3.2 | 13.0.900.73   |
| CTP 3.3 | 13.0.1000.281 |
| RC1     | 13.0.1200.242 |
| RC2     | 13.0.1300.275 |
| RC3     | 13.0.1400.361 |

Se si hanno dubbi sulla versione in uso, eseguire `@@VERSION` in una query da SQL Server Management Studio.

In generale, il processo per l'aggiornamento è come segue:

1. Eseguire il backup di dati e script.
2. Disinstallare la versione non definitiva.
3. Installare una versione di rilascio.

I componenti di machine learning la disinstallazione di una versione non definitiva di SQL Server possono essere complessi e potrebbero richiedere l'esecuzione di uno script speciale. Contattare il supporto tecnico.

### <a name="support-for-slipstream-upgrades"></a>Supporto per gli aggiornamenti integrati

L'installazione integrata si riferisce alla possibilità di applicare una patch a un'installazione di istanza non riuscita o di aggiornare tale installazione per risolvere i problemi esistenti. Il vantaggio di questo metodo è che SQL Server viene aggiornata allo stesso tempo eseguire il programma di installazione, di evitare un riavvio separato in un secondo momento.

Se il server non ha accesso a internet, assicurarsi di scaricare il programma di installazione di SQL Server. È anche necessario scaricare separatamente versioni corrispondenti dei programmi di installazione dei componenti R *prima* di avviare il processo di aggiornamento. 

Per i percorsi di download, vedere [l'installazione dei componenti di machine learning senza accesso a internet](installing-ml-components-without-internet-access.md).

Dopo aver copiato tutti i file di installazione in una directory locale, avviare l'utilità di installazione digitando SETUP.EXE nella riga di comando.

- Utilizzare il */UPDATESOURCE* argomento per specificare il percorso di un file locale che contiene l'aggiornamento di SQL Server, ad esempio un aggiornamento cumulativo o una versione del service pack.

- Utilizzare il */MRCACHEDIRECTORY* argomento per specificare la cartella che contiene i file CAB componenti di R.

Per ulteriori informazioni, vedere il blog dal team di supporto: [la distribuzione di R Services in computer senza accesso a internet](https://blogs.msdn.microsoft.com/sqlcat/2016/10/20/do-it-right-deploying-sql-server-r-services-on-computers-without-internet-access/).

### <a name="get-machine-learning-components-for-offline-installs"></a>Ottenere i componenti di machine learning per le installazioni non in linea

Se si installa o aggiornare i server che non sono connessi a internet, è necessario scaricare una versione aggiornata di machine learning manualmente i componenti prima di iniziare l'aggiornamento. 

+ [Installazione dei componenti di machine learning senza accesso a internet](../../advanced-analytics/r/installing-ml-components-without-internet-access.md).

### <a name="support-policy-and-schedule-for-update-of-machine-learning-components"></a>Supporto di criteri e la pianificazione per l'aggiornamento dei componenti di machine learning

Man mano che vengono rilasciati aggiornamenti rapidi o miglioramenti a SQL Server, i componenti di machine learning sono automaticamente aggiornati o aggiornati, se l'istanza include già la funzionalità.

A partire dal 2016 dicembre, è possibile aggiornare i componenti di machine learning a un ritmo più veloce rispetto a sul ciclo di rilascio di SQL Server. A tale scopo, *associazione* un'istanza di SQL Server per i criteri del ciclo di vita di Software più recenti. Ogni volta che viene rilasciata una nuova versione degli strumenti di apprendimento da di machine learning team di sviluppo, è possibile scaricare la versione più recente e applicarlo a un'istanza di SQL Server che viene usata per machine learning.

Per altre informazioni, vedere:

+ [Sequenza temporale del supporto per Microsoft R Server e Server di Machine Learning](https://docs.microsoft.com/machine-learning-server/resources-servicing-support)
+ [Per aggiornare un'istanza di SQL Server, utilizzare SqlBindR](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

## <a name="r-server-standalone"></a>R Server (Standalone)

In questa sezione vengono descritti i problemi specifici per le installazioni di Microsoft R Server (Standalone) che utilizzano il programma di installazione di SQL Server 2016. 

Per informazioni correlate agli aggiornamenti da R Server per Server di Machine Learning, vedere [installare Machine Learning per Windows ReportServer](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install).

### <a name="problems-when-r-services-and-r-server-standalone-are-installed-on-the-same-computer"></a>Problemi quando nello stesso computer sono installati servizi R e R Server autonomo

Nelle versioni precedenti di SQL Server 2016, l'installazione di R Server (Standalone) sia R Services (In-Database) nello stesso momento talvolta causato installazione abbia esito negativo con un messaggio "accesso negato". Questo problema è stato risolto in Service Pack 1 per SQL Server 2016.

Se si ha rilevato l'errore, è necessario aggiornare queste funzionalità, eseguire un'installazione integrata di SQL Server 2016 con SP1. Esistono due modi per risolvere il problema, che richiedono la disinstallazione e reinstallazione.

1. Disinstallare R Services (In-Database) e assicurarsi che gli account utente per SQLRUserGroup vengono rimossi.

2. Riavviare il server e quindi reinstallare R Server (Standalone).

3. Esecuzione di SQL Server del programma di installazione una volta più e questa volta selezionare **aggiungere funzionalità a SQL Server esistente**.

4. Scegliere l'istanza e quindi selezionare il **R Services (In-Database)** opzione da aggiungere.

Se questa procedura non riesce a risolvere il problema, provare a eseguire la soluzione alternativa:

1. Disinstallare R Services (In-Database) e R Server (Standalone) nello stesso momento.

2. Rimuovere gli account utente locale (SQLRUserGroup).

3. Riavviare il server.

4. Eseguire l'installazione di SQL Server e aggiungere solo la funzionalità di R Services (In-Database). Non selezionare **R Server (Standalone)**.

In genere, è consigliabile non installare R Services (In-Database) sia R Server (Standalone) nello stesso computer. Supponendo che il server dispone di sufficiente capacità, tuttavia, potrebbero risultare che r Server autonomo potrebbe essere utile come strumento di sviluppo. Un altro possibile scenario è necessario utilizzare le funzionalità di rendere operativo il di R Server, ma è anche possibile accedere ai dati di SQL Server senza lo spostamento dei dati.

## <a name="see-also"></a>Vedere anche

 [Introduzione a SQL Server R Services](../r/getting-started-with-sql-server-r-services.md)

 [Introduzione a Microsoft R Server autonomo](../r/getting-started-with-microsoft-r-server-standalone.md)

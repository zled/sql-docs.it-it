---
title: Domande frequenti sull'installazione e sull'aggiornamento (SQL Server R Services) | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 06/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 001e66b9-6c3f-41b3-81b7-46541e15f9ea
caps.latest.revision: 59
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fa3cf5a36af30be655286a2e883d2408a6a3de90
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="upgrade-and-installation-faq-sql-server-r-services"></a>Domande frequenti sull'installazione e sull'aggiornamento (SQL Server R Services)

In questo argomento fornisce le risposte ad alcune domande comuni sull'installazione di machine learning services in SQL Server. Vengono inoltre illustrate le domande frequenti sugli aggiornamenti. Alcuni problemi si verificano solo con gli aggiornamenti da versioni non definitive. Pertanto, è consigliabile identificare quanto prima della versione e dell'edizione, primo e l'aggiornamento alla versione più recente o la versione del servizio.

**Si applica a:** R Services SQL Server 2016, SQL Server 2017 di Machine Learning Services (In-Database)

## <a name="performing-setup-for-the-first-time"></a>Eseguire il programma di installazione per la prima volta

Seguire le procedure per la configurazione di [! INCLUDEssCurrent] e i componenti di R, come descritto di seguito: 

+ [Configurare SQL Server R Services o di Machine Learning Services nel Database](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)
+ [Configurare SQL Server 2017 con Python](../python/setup-python-machine-learning-services.md)
+ [Creare un server R autonomo](create-a-standalone-r-server.md)

Dopo aver installato SQL Server, per l'utilizzo di script R o Python esterni, è necessario eseguire alcuni passaggi di configurazione aggiuntive. Ciò avviene perché la funzionalità di esecuzione dello script esterno non è abilitata per impostazione predefinita, per ridurre la superficie di attacco.

> [!NOTE]
> Non utilizzare le istruzioni che sono state pubblicate prima del rilascio pubblico di SQL Server 2016. Il processo di installazione modificato completamente tra prime versioni e la versione di rilascio ufficiale. 

### <a name="requirements-and-restrictions"></a>Requisiti e restrizioni

A seconda della compilazione di R Services si sta installando, potrebbe applicare alcune delle limitazioni seguenti.

- Nelle versioni precedenti di SQL Server 2016 R Services, è necessaria la notazione 8dot3 sull'unità contenente la directory di lavoro. Se è installata una versione non definitiva, l'aggiornamento a SQL Server 2016 Service Pack 1 deve rimuovere il requisito.

- Non è possibile installare [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] in un cluster di failover, 

- In una macchina virtuale di Azure, alcune configurazioni aggiuntive potrebbero essere necessario. È ad esempio, potrebbe essere necessario creare un'eccezione del firewall per supportare l'accesso remoto.

- Installazione side-by-side con un'altra versione di R, o con altre versioni di Revolution Analitica, non è supportata.

- La nuova installazione di una versione non definitiva di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] non è più supportata. Se si utilizza una versione non definitiva, eseguire l'aggiornamento appena possibile.

- Disabilitare antivirus prima di iniziare l'installazione. Al termine dell'installazione, si consiglia di sospendere ricerca virus per le cartelle utilizzate da SQL Server, preferibilmente l'intera struttura ad albero.

### <a name="licensing-agreements-for-unattended-installs"></a>Contratti di licenza per le installazioni automatiche

Se si utilizza la riga di comando per aggiornare un'istanza di SQL Server, assicurarsi che la riga di comando include il nuovo parametro di contratto di licenza, */IACCEPTROPENLICENSEAGREEMENT*. Mancato uso dell'argomento corretto può causare l'installazione abbia esito negativo.

### <a name="offline-installation-of-r-components-for-localized-version-of-sql-server"></a>Installazione offline dei componenti R per la versione localizzata di SQL Server

Quando si installa R Services in un computer che non dispone dell'accesso a Internet, è necessario eseguire due passaggi aggiuntivi: è necessario scaricare il programma di installazione di componenti di R in una cartella locale prima di eseguire installazione di SQL Server, sarà quindi necessario modificare il file di programma di installazione per assicurarsi che il corretto l anguage è installato.

L'identificatore della lingua utilizzata per i componenti di R deve essere lo stesso come lingua di installazione di SQL Server, o **Avanti** pulsante sarà disabilitato e non è possibile completare l'installazione.

Per altre informazioni, vedere [Installazione dei componenti R senza accesso a Internet](../../advanced-analytics/r-services/installing-ml-components-without-internet-access.md).

## <a name="post-installation-configuration"></a>Configurazione post-installazione

Per utilizzare l'apprendimento con R o Python, è necessario un'ulteriore configurazione dopo l'installazione di SQL Server. Passaggi aggiuntivi potrebbero essere necessari a seconda del livello di sicurezza del server e l'istanza di SQL Server e database. Esaminare i passaggi dalle istruzioni per determinare se potrebbero essere necessarie ulteriori attività di configurazione.

[Set di backup di Database Sql Server R Services In-](set-up-sql-server-r-services-in-database.md)

- La funzionalità che supporta l'esecuzione di script esterni, ad esempio R o Python, è disabilitata per impostazione predefinita per la protezione del database e deve essere abilitata.

- Verificare che gli account di lavoro che vengono utilizzati dalla finestra di avvio per eseguire R o Python abbiano accesso all'istanza. Vedere [abilitare l'autenticazione implicita per il gruppo di account di avvio]

- Potrebbe essere necessario abilitare l'accesso remoto nel server o creare una regola del firewall che consente le comunicazioni in ingresso con SQL Server.

- A seconda del carico di lavoro pianificato, potrebbe essere necessario ottimizzare il server per le attività di apprendimento automatico. 

## <a name="upgrades-or-uninstallation"></a>Gli aggiornamenti o la disinstallazione

In questa sezione contiene istruzioni dettagliate per scenari di aggiornamento specifici.

Gli aggiornamenti dalla versione provvisoria di SQL Server 2016 R Services non sono più supportati. È consigliabile disinstallare e quindi installare una versione più breve possibile.

### <a name="support-for-slipstream-upgrades"></a>Supporto per gli aggiornamenti integrati

L'installazione integrata si riferisce alla possibilità di applicare una patch a un'installazione di istanza non riuscita o di aggiornare tale installazione per risolvere i problemi esistenti. Il vantaggio di questo metodo è che SQL Server viene aggiornato mentre si esegue l'installazione, evitando il riavvio separato in un secondo momento.

Se il server non ha accesso a Internet, assicurarsi di scaricare il programma di installazione di SQL Server. È anche necessario scaricare separatamente versioni corrispondenti dei programmi di installazione dei componenti R **prima** di avviare il processo di aggiornamento. 

Per i collegamenti di download, vedere [Installazione dei componenti R senza accesso a Internet](installing-ml-components-without-internet-access.md).

Dopo aver copiato tutti i file di installazione in una directory locale, avviare l'utilità di installazione digitando SETUP.EXE nella riga di comando.

- Usare l'argomento */UPDATESOURCE* per specificare il percorso di un file locale contenente l'aggiornamento di SQL Server, ad esempio una versione di un aggiornamento cumulativo o di un Service Pack.

- Usare l'argomento */MRCACHEDIRECTORY* per specificare la cartella contenente i file CAB dei componenti R.

Per ulteriori informazioni, vedere il blog dal team di supporto: [la distribuzione di R Services in computer senza accesso a Internet](https://blogs.msdn.microsoft.com/sqlcat/2016/10/20/do-it-right-deploying-sql-server-r-services-on-computers-without-internet-access/)

### <a name="upgrading-r-components-offline"></a>L'aggiornamento dei componenti di R non in linea

Se si installano o aggiornano server non connessi a Internet, è necessario scaricare manualmente una versione aggiornata dei componenti R prima di avviare l'aggiornamento. Per altre informazioni, vedere [Installazione dei componenti R senza accesso a Internet](../../advanced-analytics/r-services/installing-ml-components-without-internet-access.md).

### <a name="schedule-for-update-of-r-components"></a>Pianificazione per l'aggiornamento dei componenti di R

Man mano che vengono rilasciati aggiornamenti rapidi o miglioramenti a SQL Server 2016, componenti di R aggiornati oppure aggiornati, anche se l'istanza include già la funzionalità di R Services.

Se si utilizza SQL Server 2017, vengono installati automaticamente gli aggiornamenti ai componenti di R.

A partire dal 2016 dicembre, è anche possibile eseguire l'aggiornamento dei componenti di R a un ritmo più veloce rispetto a ciclo di rilascio di SQL Server, da *associazione* un'istanza di R Services per i criteri del ciclo di vita di Software più recenti. Attualmente sono supportate solo per l'aggiornamento di istanze 2016. Tuttavia, quando viene rilasciata una nuova versione del Server di R, sarà in grado anche le istanze di 2017 aggiornate.

Per altre informazioni, vedere [Usare sqlBindR.exe per aggiornare un'istanza di R Services](../../advanced-analytics/r-services/use-sqlbindr-exe-to-upgrade-an-instance-of-r-services.md)

### <a name="upgrading-from-a-pre-release-version-of-sql-server-2016"></a>L'aggiornamento da una versione non definitiva di SQL Server 2016

In generale, per tutte le versioni non definitive non sono supportati gli aggiornamenti sul posto.

Per installare correttamente R Services, è necessario disinstallare le versioni precedenti di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] e ai componenti di R correlati, inclusi SQL Server 2016 CTP3, CTP 3.1, CTP 3.2, RC0 o RC1.

La disinstallazione di una versione non definitiva possono essere complessi e richiedono l'esecuzione di uno script speciale; si consiglia di contattare il supporto tecnico per assistenza.

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

Se si hanno dubbi sulla versione in uso, eseguire `@@VERSION` da SQL Server Management Studio.

### <a name="problems-with-setup-of-r-server-standalone"></a>Problemi di installazione di R Server (Standalone)

In questa sezione vengono descritti i problemi specifici di installazione di Microsoft R Server (Standalone) utilizzando il programma di installazione di SQL Server 2016. Per informazioni più generali correlate agli aggiornamenti di R Server, vedere il sito MSDN per [Microsoft R Server](https://msdn.microsoft.com/microsoft-r/).

#### <a name="failure-to-install-localized-versions"></a>Se non si installano le versioni localizzate

Quando si esegue un offline installare R Server, le versioni non definitive non consentono di utilizzare le lingue localizzate.

In genere, quando il server non dispone di accesso a Internet, prima di eseguire il programma di installazione è necessario scaricare tutti i pacchetti di installazione per il Server di R e quindi specificare il percorso dei file durante l'installazione.

Tuttavia, se l'identificatore di lingua è associato il pacchetto di installazione non è lo stesso come lingua di installazione di SQL Server, quando si raggiunge la pagina per l'installazione di componenti di R, il **Avanti** pulsante è disabilitato e non è possibile procedere con il installazione. In alternativa, è possibile rinominare il pacchetto per l'utilizzo di un identificatore corrispondente.

Ad esempio, il nome dei pacchetti di installazione sia `SRO_3.2.2.0_1031.cab`.
Per installare il linguaggio 104 in SQL Server, rinominare il file come `SRO_3.2.2.0_1041.cab`.

#### <a name="installing-r-services-and-r-server-standalone-on-the-same-computer"></a>L'installazione di R Services e R Server autonomo nello stesso computer

In genere, è consigliabile non installare R Services (In-Database) sia R Server (Standalone) nello stesso computer. Tuttavia, se il server dispone di sufficiente capacità, R Server autonomo potrebbe essere utile come strumento di sviluppo. Potrebbe anche essere necessario utilizzare le funzionalità di rendere operativo il di R Server e accedere ai dati di SQL Server da R Server senza lo spostamento dei dati.

Si noti che se si installa R Server sia R Services nello stesso computer, vengono installati due set distinti delle stesse librerie R: una per l'utilizzo da istanza di SQL server e una per lo sviluppo di utilizzare o come Server R.

Nelle versioni precedenti di SQL Server 2016, l'installazione di R Server (Standalone) sia R Services (In-Database) nello stesso momento potrebbe causare l'installazione con un messaggio "accesso negato". Questo problema è stato risolto in Service Pack 1 per SQL Server 2016.

Se si ha rilevato l'errore e necessario effettuare l'aggiornamento di queste funzionalità, è consigliabile eseguire un'installazione integrata di SQL Server 2016 con SP1. Esistono due modi per risolvere il problema, sia che richiedono la disinstallazione e reinstallazione.

1. Disinstallare R Services (In-Database) e verificare che gli account utente per SQLRUserGroup vengono rimossi.

2. Riavviare il server e quindi reinstallare R Server (Standalone).

3. Esecuzione di SQL Server del programma di installazione una volta più e questa volta selezionare **aggiungere funzionalità a SQL Server esistente**.

4. Scegliere l'istanza e quindi selezionare il **R Services (In-Database)** opzione da aggiungere.

In alcuni casi, questa procedura avrà esito negativo cancellare l'installazione non riuscita in precedenza. In tal caso, è necessario disinstallare e reinstallare come indicato di seguito:

1. Disinstallare R Services (In-Database) e R Server (Standalone) nello stesso momento.

2. Rimuovere gli account utente locale (SQLRUserGroup).

3. Riavviare il server.

4. Eseguire l'installazione di SQL Server e aggiungere solo la funzionalità di R Services (In-Database). Non selezionare **R Server (Standalone)**.

## <a name="see-also"></a>Vedere anche

 [Introduzione a SQL Server R Services](../r/getting-started-with-sql-server-r-services.md)

 [Introduzione a Microsoft R Server autonomo](../r/getting-started-with-microsoft-r-server-standalone.md)

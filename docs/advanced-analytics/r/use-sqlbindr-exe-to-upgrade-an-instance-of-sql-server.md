---
title: Associare i componenti di machine learning in SQL Server a Microsoft Machine Learning Server | Documenti Microsoft
ms.custom: ''
ms.date: 03/15/2018
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server (starting with 2016 CTP3)
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: On Demand
ms.openlocfilehash: c82a1788f7c2c5cf4bca43c4fb03ff5c9eba0e28
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2018
---
# <a name="bind-machine-learning-components-on-sql-server-to-microsoft-machine-learning-server"></a>Associare i componenti di machine learning in SQL Server a Microsoft Machine Learning Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo articolo viene illustrato il processo di _associazione_, che è possibile utilizzare per eseguire l'aggiornamento di machine learning componenti utilizzati in SQL Server. Il processo di associazione blocca il server in un ritmo di aggiornamento sulla base delle versioni di Machine Learning Server, invece di usare SQL Server versione e aggiornare la pianificazione.

> [!IMPORTANT]
> Non è necessario utilizzare questo processo di aggiornamento se si desidera ottenere gli aggiornamenti come parte degli aggiornamenti di SQL Server. Ogni volta che si installa un nuovo service pack o una versione del servizio, i componenti di machine learning sempre automaticamente vengono aggiornati alla versione più recente. Utilizzare solo il _associazione_ elaborare se si desidera aggiornare i componenti a un ritmo più veloce rispetto a offerte dalle versioni del servizio SQL Server.

Se in qualsiasi momento si desidera interrompere l'aggiornamento in base alla pianificazione di Machine Learning Server, è necessario _disassociare_ l'istanza come descritto in [in questa sezione](#bkmk_Unbind)e disinstallare il Server di Machine Learning.

**Si applica a:** R Services SQL Server 2016, SQL Server 2017 di Machine Learning Services

## <a name="binding-vs-upgrading"></a>Associazione e l'aggiornamento

Il processo di aggiornamento di machine learning componenti è detto **associazione**, poiché il modello di supporto per i componenti di apprendimento macchina di SQL Server da usare i nuovi criteri di ciclo di vita del Software più recenti viene modificato. 

In generale, il passaggio al nuovo modello di manutenzione garantisce che il data Scientist può utilizzare sempre la versione più recente di R o Python. Per ulteriori informazioni sulle condizioni dei criteri del ciclo di vita moderna, vedere [sequenza temporale del supporto per Microsoft R Server](https://docs.microsoft.com/machine-learning-server/resources-servicing-support).

> [!NOTE]
> L'aggiornamento non modifica il modello di supporto per il database di SQL Server e non cambia la versione di SQL Server.

Quando si associa un'istanza, vengono eseguite diverse operazioni:

+ Il modello di supporto viene modificato. Anziché affidarsi le versioni del servizio SQL Server, supporto basa il nuovo criterio del ciclo di vita moderna.
+ I componenti di apprendimento computer associati all'istanza vengono aggiornati automaticamente con ogni versione, nel passaggio di blocco con la versione corrente in base ai criteri del ciclo di vita moderna nuovo. 
+ Potrebbero essere aggiunti nuovi pacchetti R o Python. Ad esempio, gli aggiornamenti precedenti in base a Microsoft R Server 9.1 aggiunti nuovi pacchetti di R, ad esempio [MicrosoftML](../using-the-microsoftml-package.md), [olapR](../r/how-to-create-mdx-queries-using-olapr.md), e [sqlrutils](../r/how-to-create-a-stored-procedure-using-sqlrutils.md).
+ L'istanza non può più essere aggiornata manualmente, se non per aggiungere nuovi pacchetti.
+ Viene visualizzata l'opzione per installare i modelli con training preliminare forniti da Microsoft.

## <a name="bkmk_prereqs"></a>Prerequisites

Iniziare identificando le istanze che sono candidati per un aggiornamento. Se si esegue il programma di installazione e selezionare l'opzione di associazione, restituirà un elenco di istanze che sono compatibili con l'aggiornamento.

Fare riferimento alla tabella seguente per un elenco di aggiornamenti supportati e i requisiti.

| Versione di SQL Server| Aggiornamento supportati| Note|
|-----|-----|------|
| SQL Server 2016| Machine Learning Server 9.2.1| Richiede almeno Service Pack 1 plus CU3. R Services deve essere installato e abilitato.|
| SQL Server 2017| Machine Learning Server 9.2.1| Machine Learning Services (In-Database) deve essere installato e abilitato. |

## <a name="bind-or-upgrade-an-instance"></a>Associare o aggiornare un'istanza

Machine Learning per Windows Server include uno strumento che è possibile utilizzare per eseguire l'aggiornamento di machine learning linguaggi e strumenti associati a un'istanza di SQL Server. Sono disponibili due versioni dello strumento: una procedura guidata e un'utilità della riga di comando.

Prima di eseguire la procedura guidata o lo strumento da riga di comando, è necessario scaricare la versione più recente del programma di installazione autonomo per i componenti di apprendimento automatico.

+ [Installare Server 9.2.1 di apprendimento per Windows](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)

+ [Scaricare i componenti necessari per l'installazione offline](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-offline)

### <a name="bkmk_BindWizard"></a>Eseguire l'aggiornamento utilizzando la nuova installazione guidata

1. Avviare il programma di installazione nuovo Server di Machine Learning. Assicurarsi di eseguire il programma di installazione nel computer che dispone dell'istanza da aggiornare.

    ![Configurazione guidata Server di Microsoft Machine Learning](media/mls-921-installer-start.PNG)

2. Nella pagina **configurare l'installazione**confermare i componenti da aggiornare e rivedere l'elenco delle istanze compatibile. Se nessuna istanza viene visualizzata, controllare la [prerequisiti](#bkmk_prereqs).

    Per aggiornare un'istanza, selezionare la casella di controllo accanto al nome di istanza. Se non si seleziona un'istanza, viene creata un'installazione separata di Machine Learning Server e le librerie di SQL Server non sono cambiate.

    ![Configurazione guidata Server di Microsoft Machine Learning](media/configure-the-installation.PNG)

3. Nel **contratto di licenza** pagina, selezionare **accettare questi termini** per accettare le condizioni di licenza per Machine Learning Server. 

4. Nelle pagine successive, fornire il consenso a condizioni di licenza aggiuntivi per tutti i componenti Apri origine che è stato selezionato, ad esempio Microsoft R Open o la distribuzione Anaconda Python.

5. Nel **quasi completata** pagina, prendere nota della cartella di installazione. La cartella predefinita è `~\Program Files\Microsoft\ML Server`.

    Se si desidera modificare la cartella di installazione, fare clic su **avanzate** per tornare alla prima pagina della procedura guidata. Tuttavia, è necessario ripetere tutte le selezioni precedenti.

6. Se si siano installando i componenti offline, potrebbe essere richiesto per il percorso dei componenti di apprendimento macchina richiesta, ad esempio Microsoft R Open, il Server di Python e Python aperto.

Durante il processo di installazione, vengono sostituite tutte le librerie R o Python utilizzate da SQL Server e finestra di avvio viene aggiornato per utilizzare i componenti più recenti. Di conseguenza, se l'istanza utilizzata in precedenza librerie nella cartella R_SERVICES predefinita, dopo l'aggiornamento queste librerie vengono rimossi e vengono modificate le proprietà per il servizio Launchpad, usino le librerie nella nuova posizione.

### <a name="bkmk_BindCmd"></a>Eseguire l'aggiornamento dalla riga di comando

Se non si desidera utilizzare la procedura guidata, è possibile installare Server di Machine Learning e quindi eseguire lo strumento SqlBindR.exe dalla riga di comando per aggiornare l'istanza.

> [!TIP]
> 
> Impossibile trovare SqlBindR.exe? Non sono probabilmente scaricati i componenti elencati sopra. Questa utilità è disponibile solo con Windows installer per Machine Learning Server.

1. Aprire un prompt dei comandi come amministratore e passare alla cartella che contiene sqlbindr.exe. Il percorso predefinito è `C:\Program Files\Microsoft\MLServer\Setup`

2. Digitare il comando seguente per visualizzare un elenco delle istanze disponibili: `SqlBindR.exe /list`
  
   Annotare il nome completo dell'istanza indicato. Ad esempio, potrebbe essere il nome dell'istanza `MSSQL14.MSSQLSERVER` per un'istanza predefinita o simile `SERVERNAME.MYNAMEDINSTANCE`.

3. Eseguire la **SqlBindR.exe** comando con il */associare* argomento e specificare il nome dell'istanza da aggiornare, utilizzando il nome dell'istanza che è stato restituito nel passaggio precedente.

   Ad esempio, per aggiornare l'istanza predefinita, digitare:  `SqlBindR.exe /bind MSSQL14.MSSQLSERVER`

4. Quando l'aggiornamento è stata completata, riavviare il servizio Launchpad associato a un'istanza in cui è stata modificata.

## <a name="bkmk_Unbind"></a>Ripristinare o separare un'istanza

Se si decide che non è più eseguire l'aggiornamento di machine learning componenti tramite Machine Learning Server, è necessario innanzitutto _disassociare_ dell'istanza, quindi disinstallare Server Machine Learning.

+ Annullamento del binding dell'istanza

    È possibile separare l'istanza e ripristinare le librerie originale installate tramite SQL Server, utilizzando uno di questi due metodi:

    + [Utilizzare l'installazione guidata](#bkmk_wizunbind) per Machine Learning Server, deselezionare tutte le funzionalità nell'istanza
    + [Utilizzare l'utilità SqlBindR](#bkmk_cmdunbind) con il `/unbind` argomento, seguito dal nome dell'istanza.

    Una volta completato il processo di annullamento dell'associazione, non è più future apprendimento aggiornamenti basati su Machine Learning Server verrà applicata all'istanza.

+ Disinstallazione di Machine Learning Server

    Per istruzioni, vedere [disinstallare Machine Learning per Windows Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-uninstall). 

### <a name="bkmk_wizunbind"></a> Annullamento del binding utilizzando la procedura guidata

1. Individuare il programma di installazione per il Server di Machine Learning. Se è stato rimosso il programma di installazione, potrebbe essere necessario scaricarlo nuovamente o copiarlo da un altro computer.
2. Assicurarsi di eseguire il programma di installazione nel computer che dispone dell'istanza che si desidera disassociare.
2. Il programma di installazione identifica le istanze locali che sono candidati per l'annullamento dell'associazione.
3. Deselezionare la casella di controllo accanto all'istanza che si desidera ripristinare la configurazione originale.
4. Accettare il contratto di licenza. È necessario indicare l'accettazione delle condizioni di licenza anche durante l'installazione.
5. Fare clic su **Fine**. Il processo richiede un po' di tempo.

### <a name="bkmk_cmdunbind"></a> Annullamento del binding utilizzando la riga di comando

1. Aprire un prompt dei comandi e passare alla cartella contenente **sqlbindr.exe**, come descritto nella sezione precedente.

2. Eseguire il comando **SqlBindR.exe** con l'argomento */unbind* e specificare l'istanza.

   Ad esempio, il comando seguente ripristina l'istanza predefinita:
   
    `SqlBindR.exe /unbind MSSQL14.MSSQLSERVER`

## <a name="known-issues"></a>Problemi noti

Questa sezione elenca i problemi noti specifici utilizzo dell'utilità SqlBindR.exe o agli aggiornamenti di Machine Learning Server che potrebbe influire sui istanze di SQL Server.

### <a name="restoring-packages-that-were-previously-installed"></a>Ripristino dei pacchetti che sono stati installati in precedenza

Nell'utilità di aggiornamento che è stato incluso con Microsoft R Server 9.0.1, l'utilità non è stato ripristinato dei pacchetti originali o componenti di R completamente, che richiedono che l'utente eseguire Ripristina nell'istanza, si applicano a tutte le versioni di servizio e quindi riavviare l'istanza.

Tuttavia, la versione più recente dell'utilità di aggiornamento consente di ripristinare automaticamente le funzionalità di R originale. Pertanto, non è necessario reinstallare i componenti di R o patch nuovamente il server. Tuttavia, è necessario installare tutti i pacchetti R che potrebbero essere state aggiunte dopo l'installazione iniziale.

Se si usa i ruoli di gestione pacchetti per installare e condividere pacchetto, questa attività è molto più semplice: è possibile utilizzare i comandi di R per sincronizzare i pacchetti installati nel file System tramite i record nel database di e viceversa. Per altre informazioni, vedere [gestione dei pacchetti R per SQL Server](r-package-management-for-sql-server-r-services.md).

### <a name="problems-with-multiple-upgrades-from-sql-server"></a>Problemi con più aggiornamenti da SQL Server

Se è stato aggiornato in precedenza un'istanza di SQL Server 2016 R Services a 9.0.1, quando si esegue di nuovo il programma di installazione per Microsoft R Server 9.1.0, viene visualizzato un elenco di tutte le istanze valide e quindi per impostazione predefinita consente di selezionare le istanze in precedenza associate. Se si continua, le istanze associate in precedenza sono non associate. Di conseguenza, 9.0.1 precedente viene rimossa l'installazione, inclusi quelli dei relativi pacchetti, ma non è installata la nuova versione di Microsoft R Server (9.1.0).

In alternativa, è possibile modificare l'installazione di R Server esistente come indicato di seguito:
1. Nel Pannello di controllo, aprire **Aggiungi / Rimuovi programmi**.
2. Microsoft R Server fare clic su **modifica/modifica**.
3. Quando viene avviato il programma di installazione, selezionare le istanze in cui che si desidera associare a 9.1.0.

### <a name="binding-or-unbinding-leaves-multiple-temporary-folders"></a>L'associazione o dissociazione lascia più cartelle temporanee

Talvolta l'associazione e le operazioni di annullamento dell'associazione non riesce pulire le cartelle temporanee.
Se si ritiene cartelle con un nome simile al seguente, è possibile rimuoverlo al termine dell'installazione: `R_SERVICES_<guid>`

> [!NOTE]
> Assicurarsi di attendere che l'installazione è stata completata. Può richiedere molto tempo per rimuovere le librerie di R associate con una versione e quindi aggiungere le nuove librerie di R. Al termine dell'operazione, le cartelle temporanee vengono rimosse.

## <a name="sqlbindrexe-command-syntax"></a>Sintassi del comando sqlbindr.exe

### <a name="usage"></a>Utilizzo

`sqlbindr [/list] [/bind <SQL_instance_ID>] [/unbind <SQL_instance_ID>]`

### <a name="parameters"></a>Parametri

|Nome|Description|
|------|------|
|*list*| Visualizza un elenco di tutti gli ID delle istanze di database SQL nel computer corrente|
|*bind*| Aggiorna l'istanza di database SQL specificata alla versione più recente di R Server e assicura che all'istanza vengano applicati automaticamente gli aggiornamenti successivi di R Server|
|*unbind*|Disinstalla la versione più recente di R Server dall'istanza di database SQL specificata e impedisce l'applicazione degli aggiornamenti successivi di R Server|

### <a name="errors"></a>Errori

La query restituisce i messaggi di errore seguenti:

|Errore|Soluzione|
|------|------|
|An error occurred while binding the instance (Si è verificato un errore durante l'associazione dell'istanza)| Non è stato possibile associare l'istanza. Contattare il supporto tecnico.|
|The instance is already bound (L'istanza è già associata)| È stato eseguito il comando *bind* , ma l'istanza specificata è già associata. Scegliere un'istanza diversa.|
|The instance is not bound (L'istanza non è associata)| È stato eseguito il comando *unbind* , ma l'istanza specificata non è associata. Scegliere un'altra istanza compatibile.|
|Not a valid SQL instance ID (L'ID dell'istanza SQL non è valido)| È possibile che il nome di istanza digitato non sia corretto. Eseguire nuovamente il comando con l'argomento *list* per visualizzare gli ID di istanza disponibili.|
|No instances found (Non è stata trovata alcuna istanza)| In questo computer non è presente un'istanza di SQL Server R Services.|
|Nell'istanza deve essere installata una versione compatibile di SQL R Services (In-Database).| Per informazioni dettagliate, vedere i requisiti di compatibilità in questo argomento.|
|An error occurred while unbinding the instance (Si è verificato un errore durante l'annullamento dell'associazione dell'istanza)| Non è stato possibile disassociare l'istanza. Contattare il supporto tecnico.|
|An unexpected error has occurred (Si è verificato un errore imprevisto)| Si sono verificati altri errori. Contattare il supporto tecnico.  |
|No SQL instances found (Non è stata trovata alcuna istanza di SQL)| In questo computer non è presente un'istanza di SQL Server. |

Per altre informazioni, vedere le note sulla versione per Microsoft R Server:

+ [Problemi noti in Machine Learning Server](https://docs.microsoft.com/machine-learning-server/resources-known-issues)

+ [Annunci di funzionalità dalla versione precedente di R Server](https://docs.microsoft.com/r-server/whats-new-in-r-server)

+ [Funzionalità deprecate, funzionalità o modificate](https://docs.microsoft.com/machine-learning-server/resources-deprecated-features)

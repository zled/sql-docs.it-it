---
title: L'aggiornamento dei componenti di machine learning in un'istanza di SQL Server | Documenti Microsoft
ms.custom: 
ms.date: 07/31/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server (starting with 2016 CTP3)
ms.assetid: 4da80998-f929-4fad-a86f-87d09c1a79ef
caps.latest.revision: 15
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2d9d7ddd95bdbcf6efca98ed94bc305924902b98
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="upgrade-machine-learning-components-in-a-sql-server-instance"></a>L'aggiornamento dei componenti di machine learning in un'istanza di SQL Server

Microsoft Machine Learning Server per Windows include uno strumento che consente di aggiornare i componenti di R associati a un'istanza di SQL Server. Sono disponibili due versioni dello strumento: una procedura guidata e un'utilità della riga di comando.

In questo articolo viene illustrato come utilizzare questi strumenti per aggiornare un'istanza di SQL Server compatibile e come ripristinare un'istanza che è stata aggiornata in precedenza.

Non è necessario utilizzare questo processo di aggiornamento, se si desidera ottenere gli aggiornamenti come parte degli aggiornamenti di SQL Server. Quando si installa un nuovo service pack o una versione di servizio, i componenti di machine learning vengono aggiornati automaticamente alla versione più recente. Utilizzare questo proess solo se si desidera aggiornare i componenti a un ritmo più veloce rispetto a quelle affored da SQL Server service release.

**Si applica a:** R Services SQL Server 2016, SQL Server 2017 di Machine Learning Services

> [!NOTE]
> Al momento della redazione del presente documento, gli aggiornamenti si applicano solo alle istanze di SQL Server 2016 compatibile.  Anche se l'aggiornamento è supportato per SQL Server 2017, una nuova versione di Microsoft Machine Learning Server da utilizzare per gli aggiornamenti non è stata rilasciata.

## <a name="upgrade-an-instance"></a>Aggiornare un'istanza

Il processo di aggiornamento è detto **associazione**, perché il modello di supporto per i componenti di SQL Server machine learning usare i nuovi criteri del ciclo di vita moderna viene modificato. Tuttavia, l'aggiornamento non modifica il modello di supporto per il database di SQL Server.

In generale, questo sistema di licenza permette ai data scientist di usare sempre la versione più recente di R. Per altre informazioni sulle condizioni dei criteri relativi al ciclo di vita, vedere [Support Timeline for Microsoft R Server](https://msdn.microsoft.com/microsoft-r/rserver-servicing-support)(Sequenza temporale del supporto per Microsoft R Server).

Quando si associa un'istanza, vengono eseguite diverse operazioni:

+ Il modello di supporto viene modificato. Anziché basarsi su versioni di servizio SQL Server, supporto si basa sul nuovo criterio del ciclo di vita moderna.
+ Di machine learning i componenti associati all'istanza verrà aggiornato automaticamente con ogni versione, nel passaggio di blocco con la versione corrente in base ai nuovi criteri del ciclo di vita moderna. 
+ È potrebbero aggiungervi nuovi pacchetti R o Python. Ad esempio, i precedenti aggiornamenti da Microsoft R Server aggiunti nuovi pacchetti di R, ad esempio [MicrosoftML](../using-the-microsoftml-package.md), [olapR](../r/how-to-create-mdx-queries-using-olapr.md), e [sqlrutils](../r/how-to-create-a-stored-procedure-using-sqlrutils.md).
+ L'istanza non può più essere aggiornata manualmente, se non per aggiungere nuovi pacchetti.
+ È possibile aggiungere modelli di training preliminare.

Se successivamente si decide che si desidera interrompere l'aggiornamento dell'istanza a ogni rilascio, è necessario **disassociare** l'istanza come descritto in [in questa sezione](#bkmk_Unbind), quindi disinstallare di machine learning gli aggiornamenti, come descritto In questo articolo: [eseguire Microsoft R Server per Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows). Una volta completato il processo, non è più future machine learning aggiornamenti basati su Machine Learning Server verrà applicate all'istanza.

### <a name="bkmk_prereqs"></a>Prerequisiti per l'aggiornamento

1. Identificare le istanze che possono essere aggiornate.
    + SQL Server 2016 con R Services installato
    + Oltre a almeno al Service Pack 1 CU3

2. Ottenere **Microsoft R Server**, scaricando il programma di installazione di Windows separato.

    [How to install R Server 9.0.1 on Windows using the standalone Windows Installer](https://msdn.microsoft.com/microsoft-r/rserver-install-windows#howtoinstall) (Come installare R Server 9.0.1 in Windows tramite il programma di installazione di Windows autonomo)

> [!TIP]
> 
> Impossibile trovare SqlBindR.exe? Probabilmente non è stato scaricato R Server ancora. Questa utilità è disponibile solo con il programma di installazione di Windows per Microsoft R Server.

### <a name="bkmk_BindWizard"></a>Eseguire l'aggiornamento utilizzando la nuova installazione guidata

1. Avviare il programma di installazione nuovo Server R nel computer che dispone dell'istanza che si desidera aggiornare.
  ![Installazione guidata di Microsoft R Server](media/r-server-installer-01.PNG)
2. Accettare il contratto di licenza per Microsoft R Server 9.1.0 e fare clic su **Avanti**.
3. Accettare le condizioni di licenza per i componenti di origine aprire R e fare clic su **Avanti**.
4. In **Selezione cartella di installazione**, accettare le impostazioni predefinite o specificare un percorso diverso in cui verranno installate librerie R. 
5. Il programma di installazione identificherà tutte le istanze locali che sono candidati per l'associazione. Se nessuna istanza viene visualizzata, significa che sono state trovate istanze non valide. Potrebbe essere necessario patch per il server oppure verificare se è stato installato R Services.
6. Selezionare la casella di controllo accanto a tutte le istanze che si desidera aggiornare, quindi fare clic su **Avanti**.
7. Il processo può richiedere un po' di tempo.
    
    Durante l'installazione, le librerie di R utilizzate da SQL Server R Services vengono sostituite con le librerie per Microsoft R Server 9.1.0.
    
    Finestra di avvio non è interessato dal processo, ma le librerie nella cartella R_SERVICES verranno rimossa e verrà modificata la proprietà per il servizio, per utilizzare le librerie in `C:\Program Files\Microsoft\R Server\R_SERVER`.

### <a name="bkmk_BindCmd"></a>Eseguire l'aggiornamento dalla riga di comando

Dopo aver installato Microsoft R Server, è possibile eseguire lo strumento di SqlBindR.exe dalla riga di comando.

1. Aprire un prompt dei comandi come amministratore e passare alla cartella che contiene sqlbindr.exe. Il percorso predefinito è`C:\Program Files\Microsoft\R Server\Setup`
2. Digitare il comando seguente per visualizzare un elenco delle istanze disponibili: `SqlBindR.exe /list`
  
   Annotare il nome completo dell'istanza indicato. Ad esempio, in cui potrebbe essere il nome dell'istanza `MSSQL13.MSSQLSERVER` per l'istanza predefinita o simile `SERVERNAME.MYNAMEDINSTANCE`.
3. Eseguire il comando **SqlBindR.exe** con l'argomento */bind* e specificare il nome dell'istanza da aggiornare, restituito nel passaggio precedente.

   Ad esempio, per aggiornare l'istanza predefinita, digitare:`SqlBindR.exe /bind MSSQL13.MSSQLSERVER`
4. Al termine dell'aggiornamento, riavviare il servizio Launchpad associato a qualsiasi istanza che è stata modificata.


## <a name="bkmk_Unbind"></a>Ripristinare o eliminare il binding di un'istanza

Per ripristinare un'istanza di SQL Server per utilizzare le librerie originale installate tramite SQL Server, è necessario eseguire un **disassociare** operazione. È possibile farlo eseguendo di nuovo l'installazione guidata di Microsoft R Server oppure eseguendo l'utilità SqlBindR dalla riga di comando.

Quando l'annullamento dell'associazione è completata, vengono rimosse le librerie per Microsoft R Server 9.1.0 e librerie R originale utilizzate da SQL Server R Services vengono ripristinate.

Le proprietà della finestra di avvio di SQL Server vengono modificate per utilizzare le librerie R nella cartella predefinita per R_SERVICES, nel `C:\Program Files\Microsoft\R Server\R_SERVER`.

### <a name="unbind-using-the-wizard"></a>Annullamento del binding utilizzando la procedura guidata

1. Scaricare di nuovo il programma di installazione per Microsoft R Server 9.1.0.
2. Eseguire il programma di installazione nel computer che dispone dell'istanza che si desidera separare.
2. Il programma di installazione identificherà le istanze locali che sono candidati per l'annullamento dell'associazione.
3. Deselezionare la casella di controllo accanto all'istanza che si desidera ripristinare la configurazione originale di SQL Server R Services.
4. Accettare il contratto di licenza per Microsoft R Server 9.1.0. Anche se si sta rimuovendo R Server, è necessario accettare il contratto di licenza.
5. Fare clic su **Fine**. Il processo richiede un po' di tempo.

### <a name="unbind-using-the-command-line"></a>Annullamento del binding utilizzando la riga di comando

1. Aprire un prompt dei comandi e passare alla cartella contenente **sqlbindr.exe**, come descritto nella sezione precedente.

2. Eseguire il comando **SqlBindR.exe** con l'argomento */unbind* e specificare l'istanza.

   Ad esempio, il comando seguente ripristina l'istanza predefinita:
   
    `SqlBindR.exe /unbind MSSQL13.MSSQLSERVER`

## <a name="known-issues"></a>Problemi noti

In questa sezione sono elencati i problemi noti specifici utilizzo dell'utilità SqlBindR.exe o agli aggiornamenti utilizzando l'utilità di installazione di Microsoft R Server che influiscono sulle istanze di SQL Server.

### <a name="restoring-packages-that-were-previously-installed"></a>Ripristino dei pacchetti che sono stati installati in precedenza

Nell'utilità di aggiornamento che è stato incluso in Microsoft R Server 9.0.1, l'utilità non è stato ripristinato dei pacchetti originali o componenti di R completamente, che richiedono l'esecuzione all'utente che Ripristina nell'istanza, si applicano a tutte le versioni del servizio e quindi riavviare l'istanza.

Tuttavia, la versione più recente dell'utilità di aggiornamento per Microsoft R Server 9.1.0, verrà automaticamente ripristinata la funzionalità di R originale. Pertanto, non è necessario reinstallare i componenti di R o patch nuovamente il server. Tuttavia, è necessario comunque installare tutti i pacchetti R che potrebbero essere state aggiunte dopo l'installazione iniziale.

Se i ruoli di gestione del pacchetto è stato usato per installare e condividere package, questa attività è molto più semplice: è possibile utilizzare i comandi di R per sincronizzare i pacchetti installati nel file System che utilizza i record nel database e viceversa. Per ulteriori informazioni, vedere [installazione e la gestione dei pacchetti R](installing-and-managing-r-packages.md)

### <a name="cannot-perform-upgrade-from-901"></a>Non è possibile eseguire l'aggiornamento da 9.0.1

Se un'istanza di SQL Server 2016 R Services avere precedentemente aggiornato a 9.0.1, quando si esegue di nuovo il programma di installazione per Microsoft R Server 9.1.0, verrà visualizzare un elenco di tutte le istanze valide e quindi selezionare le istanze associate in precedenza per impostazione predefinita. Se si continua, le istanze associate in precedenza sono non associate. Di conseguenza, il precedente 9.0.1 viene rimosso l'installazione, inclusi quelli relativi a pacchetti, ma la nuova versione di Microsoft R Server (9.1.0) non è installata.

In alternativa, è possibile modificare l'installazione di R Server esistente come indicato di seguito:
1. Nel Pannello di controllo aprire **Aggiungi / Rimuovi programmi**.
2. Microsoft R Server fare clic su **modifica/modifica**.
3. Quando viene avviato il programma di installazione, selezionare le istanze in cui che si desidera associare a 9.1.0.

### <a name="binding-or-unbinding-leaves-multiple-temporary-folders"></a>L'associazione o dissociazione lascia più cartelle temporanee

Talvolta l'associazione e le operazioni di annullamento dell'associazione non riesce a eseguire la pulizia delle cartelle temporanee.
Se si ritiene di cartelle con un nome simile al seguente, è possibile rimuoverlo al termine dell'installazione:`R_SERVICES_<guid>`

> [!NOTE]
> Assicurarsi di attendere che l'installazione è stata completata. Può richiedere molto tempo per rimuovere le librerie R associate a una versione e quindi aggiungere le nuove librerie di R. Al termine dell'operazione, le cartelle temporanee vengono rimosse.

## <a name="sqlbindrexe-command-syntax"></a>Sintassi del comando sqlbindr.exe

### <a name="usage"></a>Utilizzo

`sqlbindr [/list] [/bind <SQL_instance_ID>] [/unbind <SQL_instance_ID>]`

### <a name="parameters"></a>Parametri

|Nome|Descrizione|
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

Per ulteriori informazioni, vedere le note sulla versione per Microsoft R Server:

+ [Novità di R Server](https://docs.microsoft.com/r-server/whats-new-in-r-server)

+ [Problemi noti di R Server](https://docs.microsoft.com/r-server/resources-known-issues)


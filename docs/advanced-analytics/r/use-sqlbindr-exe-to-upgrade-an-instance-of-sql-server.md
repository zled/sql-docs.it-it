---
title: L'aggiornamento dei componenti di R e Python nelle istanze di SQL Server R (servizi di Machine Learning) | Documenti Microsoft
description: Eseguire l'aggiornamento R e Python in SQL Server 2016 R Services o SQL Server 2017 Machine Learning Services mediante sqlbindr.exe da associare al Server di Machine Learning.
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/05/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 140d84717f7343f52b1c553964cce8f0c40e2c7c
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/08/2018
---
# <a name="upgrade-machine-learning-r-and-python-components-in-sql-server-instances"></a>L'aggiornamento dei componenti della macchina di apprendimento (R e Python) in istanze di SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Integrazione di R e Python in SQL Server include i pacchetti open source e Microsoft proprietaria. Sotto la manutenzione standard di SQL Server, i pacchetti R e Python vengono aggiornati in base al ciclo di rilascio di SQL Server, con correzioni di bug per i pacchetti esistenti nella versione corrente. 

La maggior parte degli esperti di dati sono abituati a lavorare con i pacchetti più recenti appena diventano disponibili. Per SQL Server 2017 Machine Learning Services (In-Database) e SQL Server 2016 R Services (In-Database), è possibile ottenere versioni più recenti di R e Python modificando il *associazione* dalla manutenzione di SQL Server [Microsoft Computer Server Learning](https://docs.microsoft.com/en-us/machine-learning-server/index) e il [criteri di supporto del ciclo di vita moderna](https://support.microsoft.com/help/30881/modern-lifecycle-policy).

Associazione non modifica le nozioni di base dell'installazione: integrazione di R e Python è comunque parte di un'istanza di motore di database, gestione delle licenze non è stata modificata (senza costi aggiuntivi associati all'associazione) e i criteri di supporto di SQL Server contengono ancora per il database motore. Ma durata del REBINDING del modo in cui vengono gestiti i pacchetti R e Python. Il resto di questo articolo viene illustrato il meccanismo di associazione e il relativo funzionamento per ogni versione di SQL Server.

> [!NOTE]
> Associazione si applica alle istanze (In-Database) solo. Associazione non è pertinente per l'installazione (autonomo).

**SQL Server 2017**

Per SQL Server 2017 Machine Learning Services, considerare l'associazione solo quando Microsoft Machine Learning Server inizia a offrire altri pacchetti o le versioni più recenti su ciò che esiste già.

**SQL Server 2016**

Per i clienti di SQL Server 2016 R Services, sono presenti due percorsi per ottenere nuovi e aggiornati i pacchetti R. Una di queste prevede l'aggiornamento a SQL Server 2017; il secondo, l'associazione a Server di Microsoft Machine Learning.

È l'aggiornamento a SQL Server 2017 Ottiene i pacchetti R in corrispondenza le versioni incluse in tale versione, oltre alle funzionalità di Python. In alternativa, associazione ottiene aggiornamento pacchetti R, che possono essere aggiornati ulteriormente in ogni nuova versione principale e secondaria del Server di Microsoft Machine Learning. Associazione non offrono supporto Python, che è una funzionalità di SQL Server 2017. 

**Aggiornamenti dei componenti disponibili tramite Microsoft Machine Learning Server**

Nella tabella seguente è una mappa di versione, con la versione installata con SQL Server, con eventuali aggiornamenti quando si associa a Microsoft Machine Learning Server (precedentemente noto come Server R prima dell'aggiunta del supporto Python a partire da MLS 9.2.1). 

Si noti che l'associazione non garantisce la versione più recente di R o Anaconda. Quando si associa al Server di Microsoft Machine Learning, recupero della versione di Python o R installata tramite l'installazione, che potrebbe non essere la versione più recente disponibile sul web.

[**SQL Server 2016 R Services**](../install/sql-r-services-windows-install.md)

Componente |Versione iniziale | R Server 9.0.1 | R Server 9.1 | MLS 9.2.1 | MLS 9.3 |
----------|----------------|----------------|--------------|---------|-------|
Microsoft R Open (MRO) su R | R 3.2.2     | R 3.3.2   |R 3.3.3   | R 3.4.1  | LA VERSIONE 3.4.3 R |
[RevoScaleR](https://docs.microsoft.com/achine-learning-server/r-reference/revoscaler/revoscaler) | 9.0 | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)| n.a. | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[modelli con training preliminare](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models)| n.a. | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)| n.a. | 1,0 |  1,0 |  1,0 |  1,0 |
[olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | n.a. | 1,0 |  1,0 |  1,0 |  1,0 |


[**SQL Server 2017 macchina Learning Services**](../install/sql-machine-learning-services-windows-install.md)

Componente |Versione iniziale | MLS 9.3 | | | |
----------|----------------|---------|-|-|-|-|
Microsoft R Open (MRO) su R | R 3.4.1 | LA VERSIONE 3.4.3 R | | | |
[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) |   9.3 |  9.3 | | | |
[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) | 9.3  | 9.3| | | |
[sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)| 1,0 |  1,0 | | | |
[olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | 1,0 |  1,0 | | | |
Anaconda 4.2 su Python 3.5  | 4.2/3.5.2 | 4.2/3.5.2 | | | |
[revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | 9.3  | 9.3| | | |
 [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 9.3  | 9.3| | | |
[modelli con training preliminare](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models) | 9.3 | 9.3| | | |

## <a name="how-component-upgrade-works"></a>Funzionamento dell'aggiornamento di componenti

Aggiornamento del componente è attraverso *associazione* un'istanza di SQL Server 2016 R Services (o un'istanza di servizi di SQL Server 2017 Machine Learning) al Server di Microsoft Machine Learning. [Server di Microsoft Machine Learning](https://docs.microsoft.com/machine-learning-server/index) è un prodotto server in locale separati da SQL Server, ma con lo stesso interpreti e pacchetti. Associazione swap out il meccanismo di aggiornamento del servizio SQL Server in modo che è possibile usare i pacchetti R e Python shipping con Microsoft Machine Learning Server, che spesso sono più recenti rispetto a quelli forniti da SQL Server per la manutenzione. Criteri di cambio di supporto è un'opzione attraente per team di analisi scientifica dei dati che richiedono la generazione più recente di R e i moduli Python per le relative soluzioni. 

Associazione viene eseguita tramite il [installer MLS](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install). Il programma di installazione aggiorna pacchetti R e Python specifici, ma non sostituisce l'istanza nel database di SQL Server con un autonomo, un'installazione server disconnesso.

+ Senza l'associazione, i pacchetti R e Python sono corretti per le correzioni di bug quando si installa un service pack SQL Server o l'aggiornamento cumulativo (CU). 
+ Con l'associazione, le versioni più recenti del pacchetto possono essere applicate all'istanza, in modo indipendente dalla pianificazione del rilascio CU, sotto il [moderna criteri del ciclo di vita](https://support.microsoft.com/help/30881/modern-lifecycle-policy) e le versioni di Microsoft Machine Learning Server. I criteri di supporto del ciclo di vita moderna offre aggiornamenti più frequenti su una durata più breve, un anno. 

Associazione si applica alle funzionalità R e Python. Vale a dire, pacchetti open source per le funzionalità di R e Python (Microsoft R Open, Anaconda) e il proprietari pacchetti RevoScaleR, revoscalepy e così via. Associazione non modifica il modello di supporto per l'istanza del motore di database e non cambia la versione di SQL Server.

L'associazione è reversibile. È possibile ripristinare la gestione di SQL Server tramite [disassociazione istanza](#bkmk_Unbind) e ripristino in corso l'istanza di motore di database di SQL Server.

Passaggi per l'associazione ha sommato, sono i seguenti:

+ Iniziare con un'installazione esistente, configurata di SQL Server 2016 R Services (o servizi di SQL Server 2017 Machine Learning).
+ Determinare quale versione di Microsoft Machine Learning Server include i componenti aggiornati da usare.
+ Scaricare ed eseguire il programma di installazione per tale versione. Il programma di installazione rileva l'istanza esistente, aggiunge un'opzione di associazione e restituisce un elenco di istanze compatibile.
+ Scegliere l'istanza che si desidera associare e quindi completare l'installazione per eseguire l'associazione.

In termini di esperienza utente, la tecnologia e modalità di utilizzo è rimasto invariato. L'unica differenza è la presenza di pacchetti più recente-con controllo delle versioni e altri pacchetti non originariamente disponibili tramite SQL Server (ad esempio MicrosoftML per i clienti di SQL Server 2016 R Services).

## <a name="bkmk_BindWizard"></a>Eseguire l'aggiornamento utilizzando il programma di installazione

Il programma di installazione di Microsoft Machine Learning rileva la versione di SQL Server e le funzionalità esistenti e richiama un'utilità denominata SqlBindR.exe per modificare l'associazione. Internamente, SqlBindR è concatenato al programma di installazione e utilizzato indirettamente. In un secondo momento, è possibile eseguire SqlBindR direttamente dalla riga di comando per esercitare opzioni specifiche.

1. Controllare la versione di R e RevoScaleR per verificare che siano inferiori rispetto a ciò che si intende sostituirle con le versioni esistenti. Per altre informazioni, vedere [Python e R ottenere informazioni sul pacchetto](determine-which-packages-are-installed-on-sql-server.md).

1. [Scaricare Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install#download-machine-learning-server-installer) al computer che dispone dell'istanza da aggiornare. 

1. Decomprimere la cartella e avviare l'installazione.

    ![Configurazione guidata Server di Microsoft Machine Learning](media/mls-921-installer-start.PNG)

1. Nel **configurare l'installazione**confermare i componenti da aggiornare e rivedere l'elenco delle istanze compatibile. 

   A sinistra, scegliere tutte le funzionalità che si desidera mantenere o l'aggiornamento. Non è possibile aggiornare alcune funzionalità e non altri. Una casella di controllo vuota indica che le funzionalità rimosse presupponendo che sia attualmente installato. Nella schermata, è selezionata un'istanza di SQL Server 2017 Machine Learning Services (MSSQL14) con R e Python. Questa configurazione è supportata perché SQL Server 2017 è R e Python.

   A destra, selezionare la casella di controllo accanto al nome di istanza. Se nessuna istanza non è elencata, è una combinazione incompatibile. Se non si seleziona un'istanza, viene creata una nuova installazione autonoma di Machine Learning Server e le librerie di SQL Server non sono cambiate.

    ![Configurazione guidata Server di Microsoft Machine Learning](media/configure-the-installation.PNG)

1. Nel **contratto di licenza** selezionare **accetto le condizioni** per accettare le condizioni di licenza per il Server di Machine Learning. 

1. Nelle pagine successive, fornire il consenso a condizioni di licenza aggiuntivi per tutti i componenti open source che è stato selezionato, ad esempio Microsoft R Open o la distribuzione Anaconda Python.

1. Nel **quasi completata** pagina, prendere nota della cartella di installazione. La cartella predefinita è \Program Files\Microsoft\ML Server.

    Se si desidera modificare la cartella di installazione, fare clic su **avanzate** per tornare alla prima pagina della procedura guidata. Tuttavia, è necessario ripetere tutte le selezioni precedenti.

1. Se si [installazione dei componenti non in linea](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-offline), potrebbero essere richieste per il percorso dei componenti di apprendimento macchina richiesta, ad esempio Microsoft R Open, il Server di Python e Python aperto.

Durante il processo di installazione, vengono sostituite tutte le librerie di R o Python utilizzate da SQL Server e finestra di avvio viene aggiornato per utilizzare i componenti più recenti. Di conseguenza, se l'istanza viene utilizzata in precedenza librerie nella cartella R_SERVICES predefinita, dopo l'aggiornamento queste librerie vengono rimossi e vengono modificate le proprietà per il servizio Launchpad, per utilizzare le librerie nella nuova posizione.

Associazione influisce sul contenuto di queste cartelle: C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\library viene sostituito con il contenuto di c:\Programmi\Microsoft Files\Microsoft\ML Server\R_SERVER. La seconda cartella e il relativo contenuto viene creati dal programma di installazione di Microsoft Machine Learning Server. 

## <a name="confirm-binding"></a>Verificare associazione

Controlla di nuovo la versione di R e RevoScaleR per confermare di che avere le versioni più recenti. Per altre informazioni, vedere [Python e R ottenere informazioni sul pacchetto](determine-which-packages-are-installed-on-sql-server.md). I clienti di SQL Server 2016 R Services devono anche avere MicrosoftML.

## <a name="bkmk_BindCmd"></a>Operazioni dalla riga di comando

Dopo aver eseguito Microsoft Machine Learning Server, un'utilità della riga di comando denominata SqlBindR.exe diventa disponibile che è possibile utilizzare per le operazioni di associazione ulteriormente. Ad esempio, se si decide di annullare un'associazione, è possibile eseguire nuovamente l'installazione o utilizzare l'utilità della riga di comando. Inoltre, è possibile utilizzare questo strumento per verificare, ad esempio compatibilità e la disponibilità.

> [!TIP]
> Impossibile trovare SqlBindR? Probabilmente non è stato eseguito il programma di installazione. SqlBindR è disponibile solo dopo aver eseguito il programma di installazione di Machine Learning Server.

1. Aprire un prompt dei comandi come amministratore e passare alla cartella che contiene sqlbindr.exe. Il percorso predefinito è c:\Programmi\Microsoft Files\Microsoft\MLServer\Setup

2. Digitare il comando seguente per visualizzare un elenco delle istanze disponibili: `SqlBindR.exe /list`
  
   Annotare il nome completo dell'istanza indicato. Il nome dell'istanza, ad esempio, potrebbe essere MSSQL14. MSSQLSERVER per un'istanza predefinita o simile SERVERNAME. ISTANZADENOMINATAUTENTE.

3. Eseguire il **SqlBindR.exe** comando con il */Bind* argomento e specificare il nome dell'istanza da aggiornare, utilizzando il nome di istanza che è stato restituito nel passaggio precedente.

   Ad esempio, per aggiornare l'istanza predefinita, digitare:  `SqlBindR.exe /bind MSSQL14.MSSQLSERVER`

4. Al termine dell'aggiornamento, riavviare il servizio Launchpad associato a un'istanza in cui è stata modificata.

## <a name="bkmk_Unbind"></a>Ripristinare o separare un'istanza

È possibile ripristinare un'istanza associata a un'installazione iniziale dei componenti R e Python, stabilite dal programma di installazione di SQL Server. Esistono tre parti per eseguendo il ripristino di SQL Server per la manutenzione.

+ [Passaggio 1: Annullare l'associazione a Microsoft di Machine Learning Server](#step-1-unbind)
+ [Passaggio 2: Ripristinare l'istanza allo stato originale](#step-2-restore)
+ [Passaggio 3: Reinstallare tutti i pacchetti che è stato aggiunto all'installazione](#step-3-reinstall-packages)

<a name="step-1-unbind"></a> 

### <a name="step-1-unbind"></a>Passaggio 1: rimuovere il binding

Si dispone di due opzioni per eseguire il rollback dell'associazione: nuovamente eseguire nuovamente l'installazione oppure utilizzare l'utilità della riga di comando SqlBindR.

#### <a name="bkmk_wizunbind"></a> Annullamento del binding utilizzando il programma di installazione

1. Individuare il programma di installazione per il Server di Machine Learning. Se è stato rimosso il programma di installazione, è necessario scaricarlo di nuovo oppure copiarlo da un altro computer.
2. Assicurarsi di eseguire il programma di installazione nel computer che dispone dell'istanza che si desidera separare.
2. Il programma di installazione identifica le istanze locali che sono candidati per l'annullamento dell'associazione.
3. Deselezionare la casella di controllo accanto all'istanza che si desidera ripristinare la configurazione originale.
4. Accettare il contratto di licenza. È necessario indicare l'accettazione delle condizioni di licenza anche durante l'installazione.
5. Fare clic su **Fine**. Il processo richiede un po' di tempo.

#### <a name="bkmk_cmdunbind"></a> Annullamento del binding utilizzando la riga di comando

1. Aprire un prompt dei comandi e passare alla cartella contenente **sqlbindr.exe**, come descritto nella sezione precedente.

2. Eseguire il comando **SqlBindR.exe** con l'argomento */unbind* e specificare l'istanza.

   Ad esempio, il comando seguente ripristina l'istanza predefinita:
   
    `SqlBindR.exe /unbind MSSQL14.MSSQLSERVER`

<a name="step-2-restore"></a> 

###  <a name="step-2-repair-the-sql-server-instance"></a>Passaggio 2: Ripristinare l'istanza di SQL Server

Eseguire il programma di installazione di SQL Server per ripristinare l'istanza del motore di database con le funzionalità di R e Python. Aggiornamenti esistenti vengono mantenuti, ma se si perde eventuali aggiornamenti ai pacchetti R e Python di manutenzione di SQL Server, questo passaggio si applica le patch.

In alternativa, si tratta di altro lavoro, ma è possibile disinstallare completamente e reinstallare l'istanza del motore di database e quindi applicare tutti gli aggiornamenti del servizio.

<a name="step-3-reinstall-packages"></a> 

### <a name="step-3-add-any-third-party-packages"></a>Passaggio 3: Aggiungere tutti i pacchetti di terze parti

Potrebbero essere aggiunte altri pacchetti open source o di terze parti nella libreria del pacchetto. Poiché l'associazione di inversione passa il percorso della libreria di pacchetto predefinito, è necessario reinstallare i pacchetti per la libreria R e Python in uso. Per altre informazioni, vedere [predefinito pacchetti](installing-and-managing-r-packages.md), [installare i nuovi pacchetti R](install-additional-r-packages-on-sql-server.md), e [installare i nuovi pacchetti Python](../python/install-additional-python-packages-on-sql-server.md).

## <a name="known-issues"></a>Problemi noti

In questa sezione sono elencati i problemi noti specifici utilizzo dell'utilità SqlBindR.exe o agli aggiornamenti del Server di Machine Learning che potrebbe influire sulle istanze di SQL Server.

### <a name="restoring-packages-that-were-previously-installed"></a>Ripristino dei pacchetti che sono stati installati in precedenza

Se è stata aggiornata a Microsoft R Server 9.0.1, la versione di SqlBindR.exe per la versione non è stato possibile ripristinare i pacchetti originali o componenti di R completamente, che richiedono che l'utente eseguire il ripristino di SQL Server nell'istanza, si applicano a tutte le versioni di servizio e quindi riavviare l'istanza.

Versione più recente di SqlBindR automaticamente ripristinare le funzionalità originali di R, eliminando la necessità di reinstallazione di componenti di R o patch nuovamente il server. Tuttavia, è necessario installare eventuali aggiornamenti pacchetto R che potrebbero essere state aggiunte dopo l'installazione iniziale.

Se i ruoli di gestione del pacchetto è stato usato per installare e condividere package, questa attività è molto più semplice: è possibile utilizzare i comandi di R per sincronizzare i pacchetti installati nel file System che utilizza i record nel database e viceversa. Per ulteriori informazioni, vedere [gestione dei pacchetti R per SQL Server](r-package-management-for-sql-server-r-services.md).

### <a name="problems-with-multiple-upgrades-from-sql-server"></a>Problemi con più aggiornamenti da SQL Server

Se un'istanza di SQL Server 2016 R Services avere precedentemente aggiornato a 9.0.1, quando si esegue di nuovo il programma di installazione per Microsoft R Server 9.1.0, viene visualizzato un elenco di tutte le istanze valide e quindi Seleziona istanze precedentemente associate per impostazione predefinita. Se si continua, le istanze associate in precedenza sono non associate. Di conseguenza, il precedente 9.0.1 viene rimosso l'installazione, inclusi quelli relativi a pacchetti, ma la nuova versione di Microsoft R Server (9.1.0) non è installata.

In alternativa, è possibile modificare l'installazione di R Server esistente come indicato di seguito:
1. Nel Pannello di controllo aprire **Aggiungi / Rimuovi programmi**.
2. Microsoft R Server fare clic su **modifica/modifica**.
3. Quando viene avviato il programma di installazione, selezionare le istanze in cui che si desidera associare a 9.1.0.

Microsoft Machine Learning Server 9.2.1 e 9.3 non presenta questo problema.

### <a name="binding-or-unbinding-leaves-multiple-temporary-folders"></a>L'associazione o dissociazione lascia più cartelle temporanee

Talvolta l'associazione e le operazioni di annullamento dell'associazione non riesce a eseguire la pulizia delle cartelle temporanee.
Se si ritiene cartelle con un nome simile al seguente, è possibile rimuoverlo al termine dell'installazione: R_SERVICES_<guid>

> [!NOTE]
> Assicurarsi di attendere che l'installazione è stata completata. Può richiedere molto tempo per rimuovere le librerie R associate a una versione e quindi aggiungere le nuove librerie di R. Al termine dell'operazione, le cartelle temporanee vengono rimosse.

## <a name="sqlbindrexe-command-syntax"></a>Sintassi del comando SqlBindR.exe

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

## <a name="see-also"></a>Vedere anche

+ [Installare Machine Learning per Windows Server (connesso a Internet)](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
+ [Installare Machine Learning per Windows Server (offline)](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-offline)
+ [Problemi noti in Machine Learning Server](https://docs.microsoft.com/machine-learning-server/resources-known-issues)
+ [Annunci di funzionalità dalla versione precedente di R Server](https://docs.microsoft.com/r-server/whats-new-in-r-server)
+ [Funzionalità deprecate, funzionalità o modificate](https://docs.microsoft.com/machine-learning-server/resources-deprecated-features)
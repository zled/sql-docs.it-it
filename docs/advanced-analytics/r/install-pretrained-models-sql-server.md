---
title: Installare i modelli di training preliminare machine learning in SQL Server | Documenti Microsoft
ms.date: 03/14/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21456462-e58a-44c3-9d3a-68b4263575d7
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: fd02766e4020e6f522d50bbd471c5f84c66a998b
ms.sourcegitcommit: 0d904c23663cebafc48609671156c5ccd8521315
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2018
---
# <a name="install-pretrained-machine-learning-models-on-sql-server"></a>Installare training preliminare di machine learning i modelli in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo descrive come aggiungere i modelli con training preliminare a un'istanza di SQL Server che già dispone di R Services o installati i servizi di Machine Learning.

I modelli con training preliminare inclusi in MicrosoftML sono stati creati per aiutare i clienti che necessitano di eseguire attività, ad esempio sentiment analysis o immagine featurization, ma non dispongono di risorse per ottenere il set di dati di grandi dimensioni o eseguire il training di un modello complesso. Il team di Machine Learning Server creato e sottoposto a training questi modelli sono utili per iniziare in testo e immagine in modo efficiente l'elaborazione. Per altre informazioni, vedere la [risorse](#bkmk_resources) sezione di questo articolo.

Per un esempio di come utilizzare i modelli con training preliminare dei dati di SQL Server, vedere questo post di blog dal team di SQL Server Machine Learning:

+ [Analisi del sentiment con Python in servizi di SQL Server Machine Learning](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/11/01/sentiment-analysis-with-python-in-sql-server-machine-learning-services/)

## <a name="install-the-pre-trained-models"></a>Installare i modelli con training preliminare

È possibile utilizzare i modelli con training preliminare con i prodotti seguenti:

+ SQL Server 2016 R Services (In-Database)
+ SQL Server 2017 Machine Learning Services (In-Database)
+ Machine Learning Server (Standalone)

Il processo di installazione è leggermente diverso a seconda della versione di SQL Server. Vedere le sezioni seguenti per le istruzioni per ogni versione.

> [!NOTE]
> Non è possibile leggere o modificare i modelli con training preliminare, perché queste vengono compresse utilizzando un formato nativo, per migliorare le prestazioni.

### <a name="obtain-files-for-an-offline-installation"></a>Ottenere i file per un'installazione offline

Per installare i modelli con training preliminare in un server che non dispone dell'accesso a internet, è necessario scaricare i programmi di installazione appropriati in anticipo e copiare il programma di installazione in una cartella locale nel server. 

Per tutti i programmi di installazione di R Server e Server di Machine Learning, vedere questa pagina per i collegamenti di download: [installazione Offline](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-offline)

### <a name="install-pretrained-models-with-sql-server-2016-r-services"></a>Installare i modelli con training preliminare con SQL Server 2016 R Services

Con SQL Server 2016, è possibile installare e utilizzare i modelli R con training preliminare solo se si aggiorna innanzitutto di machine learning componenti, in un processo denominato **associazione**. 

Questo caso eseguendo il programma di installazione di Windows separato per Machine Learning Server o Microsoft R Server e selezionando una o più istanze di **associare**. Un metodo di istanza che i criteri di supporto associato all'istanza di associazione viene modificata per consentire gli aggiornamenti più frequenti per R. 

1. Avviare il programma basato su Windows separato per uno [R Server](https://docs.microsoft.com/machine-learning-server/rebranding-microsoft-r-server) oppure [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install).

2. Selezionare l'istanza da aggiornare e quindi selezionare l'opzione per ottenere i modelli con training preliminare.

    Per altre informazioni, vedere [l'aggiornamento dei componenti di apprendimento di computer utilizzati da SQL Server](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

    Se in precedenza è stata eseguita l'associazione per aggiornare i componenti di R ed è sufficiente aggiungere i modelli con training preliminare, lasciare tutte le selezioni precedenti **come**, quindi selezionare l'opzione di modelli con training preliminare. 
    
    Non deselezionare le opzioni selezionate in precedenza; Se si esegue questa operazione, il programma di installazione rimuove i componenti.

3. Si consiglia di accettare le impostazioni predefinite per i percorsi di modello.

4. Accettare tutte le altre richieste, inclusi i contratti di licenza.

Al termine dell'associazione, la versione di R e librerie associate all'istanza vengono sostituite con le versioni più recenti disponibili in Machine Learning Server o R Server. 

Con SQL Server 2016, è necessario eseguire alcuni passaggi aggiuntivi per registrare i modelli con la libreria di istanza di SQL Server 2016. Ripetere questi passaggi per ogni istanza in cui è installato i modelli con training preliminare.

1. Aprire un prompt dei comandi di Windows **come amministratore**.

2. Passare alla cartella bootstrap il programma di installazione per SQL Server, che contiene anche il programma di installazione di Microsoft R. In un'istanza predefinita di SQL Server 2016, la cartella sarebbe:
    
    `C:\Program Files\Microsoft SQL Server\130\Setup Bootstrap\SQL2017\x64\`

3. Eseguire `RSetup.exe` e indicare il componente per l'installazione, la versione e la cartella contenente i file di origine del modello, utilizzando questa sintassi:

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir "<SQL_DB_instance_folder>\R_SERVICES\library\MicrosoftML\mxLibs\x64"`. 

    I valori seguenti sono supportati per il parametro version:

    + Versione finale candidata 0: **9.1.0.0**
    + Versione finale candidata 1: **9.2.0.22**
    + RTM: **9.2.0.100**
    + Aggiornamento cumulativo 1: **9.2.0.24**
    + Aggiornamento cumulativo 4: **9.3.0**

    > [!NOTE]
    > Versioni di SQL Server corrispondente sono elencate per dare un'idea del tempo che l'aggiornamento è stato pubblicato. Se non è certi della versione installata con SQL Server, aprire la cartella R_SERVICES per l'istanza e aprire RGui (`~\R_SERVICES\bin\x64`). La schermata inizia sono elencate le versioni per la versione Microsoft R Open e Machine Learning Server. 

    Ad esempio, usare il linguaggio R con training preliminare di modelli con un'istanza predefinita di **R_SERVICES**, sarà necessario eseguire questo comando:

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library\MicrosoftML\mxLibs\x64"`

    In un'istanza denominata, il comando sarebbe simile al seguente:

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL13.MyInstanceName\R_SERVICES\library\MicrosoftML\mxLibs\x64"`

4. Se l'installazione ha esito positivo, i modelli seguenti devono essere aggiunti al `R_SERVICES` cartella:

    + AlexNet\_Updated.model
    + ImageNet1K\_mean.xml
    + pretrained.model
    + ResNet\_101\_Updated.model
    + ResNet\_18\_Updated.model
    + ResNet\_50\_Updated.model

### <a name="install-pretrained-models-on-sql-server-2017"></a>Installare i modelli con training preliminare in SQL Server 2017

Se è già stato installato SQL Server 2017, è possibile ottenere i modelli con training preliminare in due modi:

+ Aggiornare i componenti di Python e R utilizzando l'associazione e installare i modelli con training preliminare allo stesso tempo
+ Installare solo i modelli con training preliminare

Le istruzioni seguenti descrivono il processo per aggiornare i componenti di machine learning e ottenere i modelli con training preliminare nello stesso momento.

1. Eseguire il programma di installazione basati su Windows per il Server di Machine Learning. È possibile scaricare il programma di installazione dai collegamenti in questa pagina: [installare machine Learning Server per Windows](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install).

2. Se si siano installando i modelli a un server che non dispone dell'accesso a internet, assicurarsi di scaricare anche il programma di installazione per i modelli con training preliminare da questa pagina: [installazione Offline per Machine Learning Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-offline).

3. Eseguire il programma di installazione.

4. Per aggiornare i componenti di R o Python nello stesso momento, selezionare la lingua (R, Python o entrambi) che si desidera aggiornare.

    Se precedentemente installato Machine Learning Server e dei componenti di R o Python utilizzando l'opzione di associazione aggiornati, lasciare tutte le selezioni precedenti **come**, quindi selezionare le opzioni di modelli con training preliminare. Non deselezionare le opzioni selezionate in precedenza; Se si esegue questa operazione, il programma di installazione rimuove i componenti.

5. Accettare tutte le altre richieste, inclusi i contratti di licenza.

Con SQL Server 2017, non è richiesta alcuna configurazione aggiuntiva.

> [!NOTE]
> 
> Per i modelli di Python, è possibile che venga visualizzato un errore quando si chiama il file del modello dal codice Python. Si tratta di una limitazione nell'implementazione corrente di Python, che limita la lunghezza del percorso del file di modello. Questo problema è stato risolto e sarà disponibile in una prossima service release.

### <a name="installing-pretrained-models-with-r-server-standalone"></a>L'installazione di modelli con training preliminare con R Server (Standalone)

Se è installata una versione precedente di R Server (Standalone) utilizzando il programma di installazione di SQL Server 2016, è possibile aggiungere la possibilità di utilizzare i modelli con training preliminare eseguendo l'aggiornamento Server di R usando il programma di installazione basati su Windows più recente. 

I modelli con training preliminare sono diventati disponibili come opzione con [Microsoft R Server 9.1](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/introducing-microsoft-r-server-9-1-release/), ma gli aggiornamenti sono stati aggiunti a ogni versione. Si consiglia di ottenere la versione più recente possibile, ma le versioni precedenti sono elencate qui [rilascia R Server](https://docs.microsoft.com/machine-learning-server/install/r-server-install)

Le istruzioni seguenti descrivono come aggiornare i componenti di R e aggiungere i modelli con training preliminare nello stesso momento.

1. Avviare il programma basato su Windows separato per uno [R Server](https://docs.microsoft.com/machine-learning-server/rebranding-microsoft-r-server) oppure [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install).

2. Selezionare le lingue che si desiderano aggiornare e scegliere il **Pre-trained modelli** opzione.

    > [!TIP]
    > Se in precedenza è stato eseguito il programma di installazione per aggiornare R Server (Standalone), è sufficiente aggiungere i modelli con training preliminare, lasciare tutte le selezioni precedenti **come**, selezionare semplicemente Pre**-Training modelli di** opzione . **Non** deselezionate le opzioni selezionate in precedenza, se in tal modo, il programma di installazione rimuove i componenti.

    Si consiglia di accettare le impostazioni predefinite per i percorsi di modello.

3. Fare clic su **Continua**. 

4. Accettare tutte le altre richieste, inclusi i contratti di licenza.

Al termine dell'installazione, è necessario eseguire alcuni passaggi aggiuntivi per registrare i modelli con training preliminare.

1. Aprire un prompt dei comandi di Windows **come amministratore**.

2. Passare alla cartella setup bootstrap per R Server (Standalone), che contiene anche il programma di installazione di Microsoft R. 

3. Eseguire `RSetup.exe` e indicare il componente per l'installazione, la versione e la cartella contenente i file di origine del modello, utilizzando questa sintassi:

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir "~\R_SERVER\library\MicrosoftML\mxLibs\x64"`

    I valori seguenti sono supportati per il parametro version:

    + Versione finale candidata 0: **9.1.0.0**
    + Versione finale candidata 1: **9.2.0.22**
    + RTM: **9.2.0.100**
    + Aggiornamento cumulativo 1: **9.2.0.24**
    + Aggiornamento cumulativo 4: **9.3.0**

    Per abilitare l'utilizzo della versione più recente dei modelli con training preliminare per R, in un'installazione predefinita di R Server (Standalone), ad esempio, è necessario eseguire questa istruzione:

    `RSetup.exe /install /component MLM /version 9.3.0 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\130\R_SERVER\library\MicrosoftML\mxLibs\"`

### <a name="installing-pretrained-models-with-machine-learning-server-standalone"></a>L'installazione di modelli con training preliminare con Machine Learning Server (Standalone)

Se è stato installato Machine Learning Server tramite l'installazione di SQL Server 2017, aggiungere i modelli con training preliminare eseguendo il programma di installazione basati su Windows. È possibile selezionare l'opzione per aggiornare i componenti di R o Python e aggiungere i modelli con training preliminare nello stesso momento. 

Al termine dell'installazione, è richiesta alcuna configurazione aggiuntiva.

## <a name="bkmk_resources"></a> Ricerca e risorse

Attualmente i modelli disponibili sono i modelli di rete neurali profonde (DNN) per la classificazione di analisi e l'immagine di valutazione. Tutti i modelli con training preliminare sono stati eseguito il training utilizzando Microsoft [calcolo rete Toolkit](https://cntk.ai/Features/Index.html), o **CNTK**.

La configurazione di ciascuna rete è stato in base alle implementazioni di riferimento seguente:

+ ResNet-18
+ ResNet-50
+ ResNet-101
+ AlexNet

Per ulteriori informazioni sugli algoritmi usati in questi deep learning i modelli, e come ere implementato e il training usando CNTK, vedere i seguenti articoli:

+ [Algoritmo i ricercatori Microsoft imposta Challenge ImageNet attività cardine](https://www.microsoft.com/research/blog/microsoft-researchers-algorithm-sets-imagenet-challenge-milestone/)

+ [Microsoft calcolo rete Toolkit offre più efficiente distribuite deep learning le prestazioni di calcolo](https://www.microsoft.com/research/blog/microsoft-computational-network-toolkit-offers-most-efficient-distributed-deep-learning-computational-performance/)

### <a name="how-to-use-pre-trained-models-for-text-analysis"></a>Come utilizzare i modelli con training preliminare per l'analisi di testo

Vedere l'esempio seguente per una dimostrazione di come utilizzare il modello di testo training preliminare featurization classificazione del testo:

[Analisi del sentiment usando testo Featurizer](https://github.com/Microsoft/microsoft-r/tree/master/microsoft-ml/Samples/101/BinaryClassification/SimpleSentimentAnalysis)

### <a name="how-to-use-pretrained-models-for-image-detection"></a>Come utilizzare i modelli con training preliminare per il rilevamento dell'immagine

Il modello con training preliminare per le immagini supporta featurization delle immagini fornite. Per utilizzare il modello, si chiama il **featurizeImage** trasformare. L'immagine viene caricata, ridimensionare e trasformato dal modello con training. L'output dell'utilità di DNN viene quindi utilizzato per il training di un modello lineare per la classificazione delle immagini.

Per usare questo modello, tutte le immagini devono essere ridimensionate per soddisfare i requisiti del modello con training. Ad esempio, se si utilizza un modello AlexNet, l'immagine deve essere ridimensionato per 227 x 227 px.

Per altre informazioni, vedere [modelli con training preliminare per il rilevamento di sentiment analysis e immagine](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models)

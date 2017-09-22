---
title: Installare i modelli di training preliminare machine learning in SQL Server | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 07/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21456462-e58a-44c3-9d3a-68b4263575d7
caps.latest.revision: 1
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c6ea46c5187f00190cb39ba9a502b3ecb6a28bc6
ms.openlocfilehash: b52fcc1e4ac77df2968a4ea6cbd6e546ff1b74ac
ms.contentlocale: it-it
ms.lasthandoff: 09/19/2017

---
# <a name="install-pretrained-machine-learning-models-on-sql-server"></a>Installare training preliminare di machine learning i modelli in SQL Server

Questo argomento descrive come aggiungere i modelli di training preliminare a un'istanza di SQL Server che già dispone di R Services o installato Servizi di Machine Learning.

I modelli di training preliminare vengono forniti con l'aggiornamento a Microsoft R Server (o l'aggiornamento al Server di Microsoft Machine Learning). Per informazioni su come aggiornare l'istanza e di ottenere la versione più recente di Microsoft R, vedere [l'aggiornamento dei componenti R in un'istanza di R Services](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

È possibile installare questi modelli solo eseguendo l'installazione basata su Windows separato per R Server.
Tuttavia, esistono alcuni passaggi aggiuntivi da utilizzare quando si installa i modelli in SQL Server. In questo argomento viene descritto il processo.

## <a name="benefits-of-using-pretrained-models"></a>Vantaggi dell'utilizzo di modelli di training preliminare

I modelli con training preliminare sono state rese disponibili per supportare i clienti che è necessario eseguire attività quali l'analisi del sentiment o immagine featurization, ma non dispone di risorse per ottenere il set di dati di grandi dimensioni o eseguire il training di un modello complesso. Utilizzo di modelli con training preliminare consente un'introduzione a testo e immagine in modo più efficiente l'elaborazione.

Attualmente i modelli disponibili sono i modelli di rete neurali profonde (DNN) per la classificazione di analisi e l'immagine di valutazione. Tutti e quattro i modelli di training preliminare erano sottoposto a training sui CNTK. La configurazione di ciascuna rete è stato in base alle implementazioni di riferimento seguente:

+ ResNet-18
+ ResNet 50
+ ResNet 101
+ AlexNet

Per ulteriori informazioni sulle reti deep residue e la relativa implementazione utilizzando CNTK, vedere i seguenti articoli:

+ [Algoritmo i ricercatori Microsoft imposta attività cardine ImageNet richiesta](https://www.microsoft.com/research/blog/microsoft-researchers-algorithm-sets-imagenet-challenge-milestone/)

+ [Microsoft calcolo rete Toolkit offre più efficiente deep distribuite le prestazioni di calcolo di apprendimento](https://www.microsoft.com/research/blog/microsoft-computational-network-toolkit-offers-most-efficient-distributed-deep-learning-computational-performance/)

## <a name="how-to-install-the-models-on-sql-server"></a>Come installare i modelli in SQL Server

   > [!NOTE]
   > 
   > Se si utilizza il programma di installazione basati su Windows separato per installare Microsoft R Server o per aggiornare l'istanza di SQL Server, i modelli con training preliminare sono disponibili dal programma di installazione. Vedere [installare R Server per Windows](https://docs.microsoft.com/en-us/r-server/install/r-server-install-windows).
   > 
   > Potrebbero essere necessari ulteriori passaggi per usare i modelli con Microsoft R Server. Per ulteriori informazioni, vedere [come installare e distribuire pre-Training modelli di machine learning con MicrosoftML](https://docs.microsoft.com/r-server/install/microsoftml-install-pretrained-models)

1. I modelli con training preliminare non sono installati per impostazione predefinita quando si installa SQL Server. è necessario aggiungerli tramite l'esecuzione di un'utilità della riga di comando di installazione al termine dell'installazione di SQL Server.

2. Aprire un prompt dei comandi con privilegi elevati e passare alla cartella bootstrap il programma di installazione per SQL Server, che contiene anche il programma di installazione di Microsoft R.

    In un'istanza predefinita di SQL Server 2017 RC 1, il risultato sarà:
    
    `C:\Program Files\Microsoft SQL Server\140\Setup Bootstrap\SQL2017RC1\x64\`

3. Specificare il componente per l'installazione e la cartella in cui devono essere aggiunti i modelli con training preliminare, utilizzando gli argomenti seguenti:

  + Per utilizzare i modelli con **R_SERVICES**

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir <SQL_DB_instance_folder>\R_SERVICES`

    Per abilitare l'utilizzo dei modelli di training preliminare usando R in un'istanza predefinita di SQL Server 2017, ad esempio, eseguire l'istruzione seguente:

    `RSetup.exe /install /component MLM /version 9.2.0.22 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES"`

  + Per utilizzare i modelli con **PYTHON_SERVICES**

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir <SQL_DB_instance_folder>\PYTHON_SERVICES`

    Per abilitare l'utilizzo dei modelli di training preliminare usando Python, per un'istanza predefinita di SQL Server 2017, ad esempio, eseguire l'istruzione seguente:

    `RSetup.exe /install /component MLM /version 9.2.0.22 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES"`

4. Per il parametro di versione, sono supportati i seguenti valori:

    + Versione finale candidata 0: **9.1.0.0**
    + Versione finale candidata 1: **9.2.0.22**
    + Numero della versione finale (non rilasciata): **9.2.0.100**

5. Se l'installazione ha esito positivo, i modelli seguenti devono essere aggiunti al R\_servizi o PYTHON\_cartelle SERVICES:

    - AlexNet_Updated.model
    - ImageNet1K_mean.xml
    - pretrained.Model
    - ResNet_101_Updated.model
    - ResNet_18_Updated.model
    - ResNet_50_Updated.model

## <a name="examples"></a>Esempi

Dopo aver installato i modelli, è possibile utilizzare i modelli tramite chiamata da codice R.

### <a name="image-featurization-example"></a>Esempio di immagine featurization

Il modello con training preliminare per le immagini supporta featurization delle immagini fornite. Per utilizzare il modello, si chiama il **featurizeImage** trasformare.

+ [featurizeImage: trasformare Featurization immagine di Machine Learning](https://docs.microsoft.com/r-server/r-reference/microsoftml/featurizeimage)

In questo esempio, vedere il secondo blocco di codice. L'immagine viene caricata, ridimensionamento e trasformato dal modello DNN convolutional training preliminare. L'output dell'utilità di DNN viene quindi utilizzato per il training di un modello lineare per la classificazione delle immagini.

L'immagine deve essere ridimensionato per soddisfare i requisiti del modello con Training: le immagini utilizzate per il training sono stati 224 x 224 px. Se si utilizza un modello AlexNet, l'immagine verrà ridimensionata a 227 x 227 px.

```R
 model <- rxFastLinear(
     Label ~ Features,
     data = train,
     mlTransforms = list(
         loadImage(vars = list(Features = "Path")),
         resizeImage(vars = "Features", width = 224, height = 224), 
         extractPixels(vars = "Features"),
         featurizeImage(var = "Features")
         ),
     mlTransformVars = "Path")
```

> [!NOTE]
> 
> Non è possibile leggere o modificare il modello con training preliminare stesso. Questo particolare modello è basato su [CNTK](https://docs.microsoft.com/cognitive-toolkit/) del modello, ma è stata compressa con un formato nativo per motivi di prestazioni.

### <a name="text-analysis-example"></a>Esempio di analisi di testo

Questo esempio viene illustrato l'utilizzo del modello con training preliminare per la classificazione:

[Analisi del sentiment utilizzando l'utilità di testo](https://github.com/Microsoft/microsoft-r/tree/master/microsoft-ml/Samples/101/BinaryClassification/SimpleSentimentAnalysis)


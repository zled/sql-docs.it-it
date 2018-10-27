---
title: Analitica di Python nel database per sviluppatori SQL | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 26703f73312b5531490afc7d01319d4ac290bebe
ms.sourcegitcommit: 70e47a008b713ea30182aa22b575b5484375b041
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49806761"
---
# <a name="in-database-python-analytics-for-sql-developers"></a>Analitica di Python nel Database per sviluppatori SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

L'obiettivo di questa procedura dettagliata è offrire ai programmatori SQL con esperienza pratica nella creazione di una soluzione di machine learning tramite Python che viene eseguito in SQL Server. In questa procedura dettagliata, si apprenderà come aggiungere codice Python alle stored procedure ed eseguire stored procedure per compilare e stimare dai modelli.

> [!NOTE]
> Se si preferisce R, Visualizzare [in questa esercitazione](sqldev-in-database-r-for-sql-developers.md), che offre una soluzione simile, ma Usa R e può essere eseguito in SQL Server 2016 o SQL Server 2017.

## <a name="overview"></a>Panoramica

Il processo di creazione di una soluzione di apprendimento è complessa può includere più strumenti e il coordinamento di esperti in materia in diverse fasi:

+ acquisizione e pulizia dei dati
+ esaminando i dati e creazione di funzionalità utili per la modellazione
+ set di training e il modello di ottimizzazione
+ distribuzione nell'ambiente di produzione

**L'obiettivo di questa procedura dettagliata è sulla compilazione e distribuzione di una soluzione usando SQL Server.**

I dati provengono dal noto set di dati dei Taxi di NYC. Per rendere questa procedura dettagliata facile e veloce, verranno campionati i dati. Si creerà un modello di classificazione binaria che consente di prevedere se una corsa specifica è tassista riceverà una Mancia o No, in base alle colonne come ora del giorno, distanza e località di partenza.

Tutte le attività possono essere eseguite usando [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure nell'ambiente familiare di [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]


- [Esplorare e visualizzare i dati usando Python](sqldev-py3-explore-and-visualize-the-data.md)

    Eseguire l'esplorazione dei dati di base e la visualizzazione, dal chiamante Python da [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure.

- [Creare funzionalità di dati usando Python in T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

    Creare nuove funzionalità di dati usando funzioni personalizzate di SQL.
  
- [Eseguire il training e salvataggio di un modello Python con T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

    Creare e salvare il modello di machine learning, l'uso di Python nelle stored procedure.
  
    Questa procedura dettagliata viene illustrato come eseguire un'attività di classificazione binaria. è anche possibile usare i dati per compilare modelli di regressione o classificazione multiclasse.

  
-  [ Rendere operativo il modello di Python](sqldev-py6-operationalize-the-model.md)

    Dopo aver salvato il modello al database, chiamare il modello per l'uso di stima [!INCLUDE[tsql](../../includes/tsql-md.md)].

## <a name="requirements"></a>Requisiti

### <a name="prerequisites"></a>Prerequisiti

+ Installare un'istanza di SQL Server 2017 con servizi di Machine Learning e Python abilitata. Per altre informazioni, vedere [installare SQL Server 2017 Machine Learning Services (In-Database)](../install/sql-machine-learning-services-windows-install.md).
+ L'account di accesso usato per questa procedura deve avere le autorizzazioni necessarie per creare database e altri oggetti, per caricare i dati, selezionare i dati ed eseguire le stored procedure.

### <a name="experience-level"></a>Livello di esperienza

È necessario avere familiarità con le operazioni di database fondamentali, quali la creazione di tabelle e database, l'importazione di dati in tabelle e creazione di query SQL.

Un programmatore SQL esperto deve essere in grado di completare questa procedura dettagliata usando [!INCLUDE[tsql](../../includes/tsql-md.md)] in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o eseguendo gli script di PowerShell disponibili.

Python: Knowledge base è utile ma non obbligatoria. Viene fornito tutto il codice Python.

È utile una discreta conoscenza di PowerShell.

### <a name="tools"></a>Strumenti

Per questa esercitazione si presuppone che hai raggiunto la fase di distribuzione. È assegnato pulire i dati, completare il codice T-SQL per la funzionalità di progettazione e l'utilizzo di codice Python. Pertanto, è possibile completare questa esercitazione usando SQL Server Management Studio o qualsiasi altro strumento che supporta le istruzioni SQL in esecuzione.

+ [Panoramica degli strumenti di SQL Server](https://docs.microsoft.com/sql/tools/overview-sql-tools) 

Se si desidera sviluppare e testare il proprio codice Python o il debug di una soluzione di Python, è consigliabile usare un ambiente di sviluppo dedicato:

+ **Visual Studio 2017** supporta sia R e [Python](https://blogs.msdn.microsoft.com/visualstudio/2017/05/12/a-lap-around-python-in-visual-studio-2017/). È consigliabile la [carico di lavoro di analisi scientifica dei dati](https://blogs.msdn.microsoft.com/visualstudio/2016/11/18/data-science-workloads-in-visual-studio-2017-rc/), che supporta anche R e F #.
+ Se si dispone di una versione precedente di Visual Studio [estensioni Python per Visual Studio](https://docs.microsoft.com/visualstudio/python/python-in-visual-studio) rende più semplice gestire più ambienti Python.
+ PyCharm è un IDE molto diffuso tra gli sviluppatori di Python.

    > [!NOTE]
    > In generale, evitare la scrittura o testa nuovo codice Python in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Se il codice che viene incorporato in una stored procedure è presenti eventuali problemi, le informazioni restituite dalla stored procedure sono in genere sufficienti per comprendere la causa dell'errore.

Usare le risorse seguenti che consentono di pianificare ed eseguire un progetto ha esito positivo di apprendimento:

+ [Team Data Science Process](https://docs.microsoft.com/azure/machine-learning/team-data-science-process/overview)

### <a name="estimated-time-required"></a>Tempo stimato necessario

|Passaggio| Tempo (ore)|
|----|----|
|Scaricare i dati di esempio| 0:15|
|Importare i dati in SQL Server usando PowerShell|0:15|
|Esplorare e visualizzare i dati|0:20|
|Creare funzionalità di dati mediante T-SQL|0:30|
|Eseguire il training e salvataggio di un modello usando T-SQL|0:15|
|Rendere operativo il modello|0:40|

## <a name="get-started"></a>Introduzione

  [Passaggio 1: Scaricare i dati di esempio](demo-data-nyctaxi-in-sql.md)

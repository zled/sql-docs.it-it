---
title: Analitica Python nel database per gli sviluppatori SQL | Documenti Microsoft
ms.custom: ''
ms.date: 10/13/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: tutorial
applies_to:
- SQL Server 2017
dev_langs:
- Python
- TSQL
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.openlocfilehash: 3dac546d3396915932241c08c5e51afa09bf3d75
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2018
---
# <a name="in-database-python-analytics-for-sql-developers"></a>Analitica Python nel Database per gli sviluppatori SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

L'obiettivo di questa procedura dettagliata consiste nello specificare i programmatori SQL con esperienza pratica la creazione di un di machine learning soluzione usando Python che viene eseguito in SQL Server. In questa procedura dettagliata, si apprenderà come aggiungere codice Python alle stored procedure ed eseguire le stored procedure per compilare e stimare dai modelli.

> [!NOTE]
> Preferisce R? Vedere [in questa esercitazione](sqldev-in-database-r-for-sql-developers.md), fornisce una soluzione simile, ma Usa R che può essere eseguito in SQL Server 2016 o SQL Server 2017.

## <a name="overview"></a>Panoramica

Il processo di compilazione di una soluzione di apprendimento automatico è una complessa che può implicare più strumenti e il coordinamento di esperti in materia attraverso diverse fasi del processo:

+ acquisizione e pulizia dei dati
+ esplorazione dei dati e le funzionalità utili per la modellazione di compilazione
+ set di training e il modello di ottimizzazione
+ distribuzione nell'ambiente di produzione

**L'obiettivo di questa procedura dettagliata è sulla compilazione e distribuzione di una soluzione utilizzando SQL Server.**

I dati provengono dal set di dati NYC Taxi noto. Per rendere questa procedura dettagliata semplice e rapido, i dati verranno campionati. Si creerà un modello di classificazione binaria che consente di stimare se un particolare trip è probabile che ottenere un suggerimento oppure No, in base alle colonne, ad esempio l'ora del giorno, distanza e posizione ritiro.

Tutte le attività possono essere eseguite utilizzando [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure nell'ambiente familiare di [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]

- [Passaggio 1: Scaricare i dati di esempio](sqldev-py1-download-the-sample-data.md)

    Scaricare il set di dati di esempio e tutti i file di script in un computer locale.

- [Passaggio 2: Importare i dati in SQL Server usando PowerShell](sqldev-py2-import-data-to-sql-server-using-powershell.md)

    Eseguire uno script di PowerShell che crea un database e una tabella nell'istanza specificata e carica i dati di esempio per la tabella.

- [Passaggio 3: Esplorare e visualizzare i dati usando Python](sqldev-py3-explore-and-visualize-the-data.md)

    Eseguire l'esplorazione dei dati di base e la visualizzazione, dal chiamante Python da [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure.

- [Passaggio 4: Creare le funzionalità di dati usando Python in T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

    Creare nuove funzionalità di dati usando funzioni personalizzate di SQL.
  
- [Passaggio 5: Eseguire il training e salvare un modello di Python utilizzando T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

    Creare e salvare il modello di machine learning, usando Python nelle stored procedure.
  
    Questa procedura dettagliata viene illustrato come eseguire un'attività di classificazione binaria. è inoltre possibile utilizzare i dati per compilare modelli di regressione o classificazione multiclasse.

  
-  [Passaggio 6: Rendere operativo il modello di Python](sqldev-py6-operationalize-the-model.md)

    Dopo aver salvato il modello al database, chiamare il modello per l'utilizzo di stima [!INCLUDE[tsql](../../includes/tsql-md.md)].

## <a name="requirements"></a>Requisiti

### <a name="prerequisites"></a>Prerequisiti

+ Installare un'istanza di SQL Server 2017 con servizi di Machine Learning e Python abilitato. Per altre informazioni, vedere [installare SQL Server 2017 Machine Learning Services (In-Database)](../install/sql-machine-learning-services-windows-install.md).
+ L'account di accesso usato per questa procedura deve avere le autorizzazioni necessarie per creare database e altri oggetti, per caricare i dati, selezionare i dati ed eseguire le stored procedure.

### <a name="experience-level"></a>Livello di esperienza

È consigliabile avere familiarità con operazioni fondamentali sui database, ad esempio la creazione di tabelle e database, l'importazione di dati in tabelle e creazione di query SQL.

Un programmatore SQL esperto deve essere in grado di completare questa procedura dettagliata usando [!INCLUDE[tsql](../../includes/tsql-md.md)] in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o eseguendo gli script di PowerShell disponibili.

Python: Knowledge base è utile ma non obbligatoria. Viene fornito tutto il codice Python.

È utile una discreta conoscenza di PowerShell.

### <a name="tools"></a>Strumenti

Per questa esercitazione, si suppone che hai raggiunto la fase di distribuzione. Si sono stati assegnati Pulisci dati, completare il codice T-SQL per funzionalità di progettazione e l'utilizzo di codice Python. Pertanto, è possibile completare questa esercitazione utilizzando SQL Server Management Studio o qualsiasi altro strumento che supporta le istruzioni SQL in esecuzione.

+ [Panoramica degli strumenti di SQL Server](https://docs.microsoft.com/sql/tools/overview-sql-tools) 

Se si desidera sviluppare e testare il proprio codice Python o eseguire il debug di una soluzione di Python, è consigliabile utilizzare un ambiente di sviluppo dedicato:

+ **Visual Studio 2017** supporta entrambi R e [Python](https://blogs.msdn.microsoft.com/visualstudio/2017/05/12/a-lap-around-python-in-visual-studio-2017/). È consigliabile il [carico di lavoro di analisi scientifica dei dati](https://blogs.msdn.microsoft.com/visualstudio/2016/11/18/data-science-workloads-in-visual-studio-2017-rc/), che supporta anche R e F #.
+ Se si dispone di una versione precedente di Visual Studio [estensioni Python per Visual Studio](https://docs.microsoft.com/visualstudio/python/python-in-visual-studio) rende facile la gestione di più ambienti Python.
+ PyCharm è un IDE diffusi tra gli sviluppatori di Python.

    > [!NOTE]
    > In generale, evitare la scrittura o testa nuovo codice Python in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Se il codice che viene incorporato in una stored procedure è presenti eventuali problemi, le informazioni che viene restituite dalla stored procedure sono in genere sufficienti per comprendere la causa dell'errore.

Usare le risorse seguenti per pianificare ed eseguire un esito positivo di machine learning progetto:

+ [Processo di analisi scientifica dei dati di team](https://docs.microsoft.com/azure/machine-learning/team-data-science-process/overview)

### <a name="estimated-time-required"></a>Tempo stimato necessario

|Passaggio| Tempo (ore)|
|----|----|
|Scaricare i dati di esempio| 0:15|
|Importare dati in SQL Server tramite PowerShell|0:15|
|Esplorare e visualizzare i dati|0:20|
|Creare le funzionalità di data utilizzando T-SQL|0:30|
|Eseguire il training e salvare un modello utilizzando T-SQL|0:15|
|Rendere operativo il modello|0:40|

## <a name="get-started"></a>Introduzione

  [Passaggio 1: Scaricare i dati di esempio](sqldev-py1-download-the-sample-data.md)

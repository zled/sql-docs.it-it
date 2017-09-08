---
title: Python Analitica nel Database per gli sviluppatori SQL | Documenti Microsoft
ms.custom: 
ms.date: 05/25/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2017
dev_langs:
- Python
- TSQL
ms.assetid: 
caps.latest.revision: 2
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 984ff8097b1f28cf11e28cc464c88dc3b9580a12
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="in-database-python-analytics-for-sql-developers"></a>Python Analitica nel Database per gli sviluppatori SQL

L'obiettivo di questa procedura dettagliata è fornire ai programmatori SQL con la creazione di un di machine learning soluzioni in SQL Server. In questa procedura dettagliata verrà illustrato come incorporare Python in un'applicazione mediante l'aggiunta di codice Python alle stored procedure.

> [!NOTE]
> Se si preferisce R, Vedere [questa esercitazione](sqldev-in-database-r-for-sql-developers.md), che fornisce una soluzione simile, ma utilizza R ed eb eseguibili in SQL Server 2016 o SQL Server 2017.

## <a name="overview"></a>Panoramica

Il processo di creazione di una soluzione end-to-end normalmente consiste in attività di acquisizione e pulizia dei dati, esplorazione dei dati e progettazione di funzionalità, training e ottimizzazione del modello e infine distribuzione del modello nell'ambiente di produzione. Sviluppo e test del codice effettivo viene eseguita meglio con un ambiente di sviluppo dedicato, ad esempio di questi strumenti Python:

+ PyCharm, un IDE comuni
+ Spyder, incluso in [Visual Studio 2017](https://blogs.msdn.microsoft.com/visualstudio/2017/05/12/a-lap-around-python-in-visual-studio-2017/) se si installa il [carico di lavoro di analisi scientifica dei dati](https://blogs.msdn.microsoft.com/visualstudio/2016/11/18/data-science-workloads-in-visual-studio-2017-rc/)
+ [Estensioni di Python per Visual Studio](https://docs.microsoft.com/visualstudio/python/python-in-visual-studio).

Dopo aver creato e testato la soluzione nell'IDE, è possibile distribuire il codice Python da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzando [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure nell'ambiente familiare di [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

In questa procedura dettagliata, si presupporrà che sono state concesse tutto il codice Python necessario per la soluzione e verrà concentrarsi sulla compilazione e distribuzione della soluzione Usa SQL Server.

- [Passaggio 1: Scaricare i dati di esempio](sqldev-py1-download-the-sample-data.md)

  Scaricare il set di dati di esempio e tutti i file di script in un computer locale.

- [Passaggio 2: Importare i dati in SQL Server usando PowerShell](sqldev-py2-import-data-to-sql-server-using-powershell.md)

  Eseguire uno script di PowerShell che crea un database e una tabella nell'istanza specificata e carica i dati di esempio per la tabella.

- [Passaggio 3: Esplorare e visualizzare i dati](sqldev-py3-explore-and-visualize-the-data.md)

  Eseguire l'esplorazione dei dati di base e la visualizzazione, dal chiamante Python da [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure.

- [Passaggio 4: Creare funzionalità di dati mediante T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

  Creare nuove funzionalità di dati usando funzioni personalizzate di SQL.
  
- [Passaggio 5: Training e salvataggio di un modello tramite T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

   Creare e salvare il modello di machine learning, usando Python nelle stored procedure.
  
-  [Passaggio 6: Rendere operativo il modello](sqldev-py6-operationalize-the-model.md)

  Dopo che il modello è stato salvato nel database, chiamare il modello per l'utilizzo di stima [!INCLUDE[tsql](../../includes/tsql-md.md)].

> [!NOTE]
> È consigliabile non utilizzare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per scrivere o testare il codice Python. Se il codice che viene incorporato in una stored procedure è presenti eventuali problemi, le informazioni che viene restituite dalla stored procedure sono in genere sufficienti per individuare la causa dell'errore.


### <a name="scenario"></a>Scenario

Questa procedura dettagliata usa il noto set di dati NYC Taxi. Per rendere questa procedura dettagliata semplice e rapido, i dati verranno campionati. Con questi dati, si creerà un modello di classificazione binaria che consente di stimare se un particolare trip è probabile che ottenere un suggerimento o non, in base alle colonne, ad esempio l'ora del giorno, distanza e posizione ritiro.

### <a name="requirements"></a>Requisiti

Questa procedura dettagliata è destinata agli utenti che hanno già familiarità con le operazioni fondamentali dei database, ad esempio la creazione di tabelle e database, l'importazione dei dati in tabelle e la creazione di query SQL.

Viene fornito tutto il codice Python. Un programmatore SQL esperto deve essere in grado di completare questa procedura dettagliata usando [!INCLUDE[tsql](../../includes/tsql-md.md)] in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o eseguendo gli script di PowerShell disponibili.

Prima di avviare la procedura dettagliata, è necessario completare le operazioni di preparazione:

- Installare un'istanza di SQL Server 2017 con servizi di Machine Learning e Python abilitato (richiede la versione CTP 2.0 o versione successiva).
- L'account di accesso usato per questa procedura deve avere le autorizzazioni necessarie per creare database e altri oggetti, per caricare i dati, selezionare i dati ed eseguire le stored procedure.

## <a name="next-step"></a>Passaggio successivo

  [Passaggio 1: Scaricare i dati di esempio](sqldev-py1-download-the-sample-data.md)

## <a name="see-also"></a>Vedere anche

[Servizi di Machine Learning con Python](../python/sql-server-python-services.md)




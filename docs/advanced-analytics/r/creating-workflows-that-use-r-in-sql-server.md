---
title: Creazione di flussi di lavoro di Business Intelligence con R | Documenti Microsoft
ms.custom: SQL2016_New_Updated
ms.date: 04/18/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34c3b1c2-97db-4cea-b287-c7f4fe4ecc1b
caps.latest.revision: "11"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c4fd8e50dc082acde85cb427c74e8a1fca91744d
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2017
---
# <a name="creating-bi-workflows-with-r"></a>Creazione di flussi di lavoro di Business Intelligence con R

Un database relazionale è una tecnologia altamente ottimizzata per la realizzazione di soluzioni scalabili per l'elaborazione delle transazioni, l'archiviazione e l'esecuzione di query sui dati.

Al contrario, sempre soluzioni R hanno in genere basata sull'importazione di dati da diverse origini, spesso in formato CSV, per eseguire la modellazione e l'esplorazione dei dati di altre. Si tratta di procedure non solo poco efficienti, ma anche non sicure.

Questo argomento descrive scenari di integrazione di R con SQL Server in modo da non comuni problemi e rischi di protezione che può verificarsi se le soluzioni di machine learning vengono sviluppate all'esterno del database.

Vengono inoltre descritti esempi di come applicazioni di business intelligence, in particolare i servizi di integrazione e Reportng, è possano interagire con il codice R e utilizzare dati o la grafica generati da R.

Si applica a: R Services SQL Server 2016, SQL Server 2017 di Machine Learning Services

## <a name="bring-compute-power-to-the-data"></a>Portare i dati di potenza di calcolo

Per portare analitica dati, è stato un obiettivo chiave della progettazione dell'integrazione di apprendimento con SQL Server. Ciò offre più vantaggi:

+ Sicurezza dei dati. Riportare l'avvicinamento di R per l'origine dei dati consente di evitare lo spostamento dei dati dispendiosa o non sicuro.

+ Velocità. I database sono ottimizzati per le operazioni basate su set. Le innovazioni recenti nel database come tabelle in memoria rendono riepiloghi e aggregazioni fulmine e sono la soluzione ideale per l'analisi scientifica dei dati.

+ Facilità di distribuzione e l'integrazione. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]è il punto centrale di operazioni per molte altre attività di gestione dati e applicazioni. Utilizzando i dati che si trovano i database warehouse per reporting, assicurarsi che i dati utilizzati da soluzioni di apprendimento automatico siano aggiornato e coerente. 

+ Efficienza tra cloud e locali. Invece di elaborare i dati in R, è possibile usare le pipeline di dati aziendali, inclusi [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] e Azure Data Factory. La creazione di report con i risultati o l'analisi è semplice con Power BI o [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].

Con la giusta combinazione di SQL e R per le diverse attività di elaborazione e analisi di dati, sia i data scientist che gli sviluppatori possono essere più produttivi.

## <a name="use-integration-services-for-data-transformation-and-automation"></a>Utilizzare Integration Services per i dati di trasformazione e automazione

I flussi di lavoro per l'analisi scientifica dei dati sono altamente iterativi e implicano molte trasformazioni dei dati, tra cui ridimensionamento, aggregazioni, calcolo delle probabilità, ridenominazione e unione degli attributi. I data scientist sono abituati a eseguire molte di queste attività in R, Python o con un altro linguaggio, ma, per eseguire tali flussi di lavoro su dati aziendali, è necessaria la perfetta integrazione con strumenti e processi ETL.

Poiché [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] consente di eseguire operazioni complesse in R tramite Transact-SQL e stored procedure, è possibile integrare attività specifiche di R con i processi ETL esistenti senza dover intervenire per adattare lo sviluppo. Invece di eseguire una catena di attività a elevato utilizzo di memoria di R, la preparazione dei dati può essere ottimizzata tramite gli strumenti più efficienti, tra cui [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] e [!INCLUDE[tsql](../../includes/tsql-md.md)]. 

Ecco alcuni ideass per come è possibile automatizzare l'elaborazione di un dmodeling dati pipeline utilizzando [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]:

+ Utilizzare [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] attività per creare le funzionalità di dati necessari nel database SQL
+ Usare la diramazione condizionale per cambiare il contesto di calcolo per i processi R
+ Eseguire processi R che generano i propri dati nel database e condividere i dati con le applicazioni
+ Quando si utilizza [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], caricare lo script R salvato in una variabile di testo ed eseguirlo in SQL Server

### <a name="examples"></a>Esempi

[Rendere operativo il progetto di Machine Learning usando SSIS e R Services di SQL Server 2016](https://blogs.msdn.microsoft.com/ssis/2016/01/11/operationalize-your-machine-learning-project-using-sql-server-2016-ssis-and-r-services/)  

Questo post di blog illustra le tecniche di base per la modifica di codice R usando [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]: 

+ Chiamare R utilizzando l'attività Esegui SQL per generare i dati e salvarlo in[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

+ Usare una stored procedure per eseguire il training di un modello R e archiviarlo nel database

+ Eseguire l'assegnazione dei punteggi al modello usando l'attività Script e l'attività Esegui SQL

##  <a name="bkmk_ssrs"></a>Utilizzare Reporting Services per la visualizzazione

Anche se R consente di creare grafici e visualizzazioni interessanti, non è ben integrato con le origini dati esterne e questo significa che ogni grafico deve essere prodotto singolarmente. Anche la condivisione può essere difficile.

Con [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] è possibile eseguire operazioni complesse in R tramite stored procedure di [!INCLUDE[tsql](../../includes/tsql-md.md)], facilmente accessibili da un'ampia gamma di strumenti per la creazione di report aziendali, tra cui [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e Power BI.

+ Visualizzare gli oggetti grafici restituiti da uno script R con [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]
+ Usare la tabella in Power BI

### <a name="examples"></a>Esempi

[R Graphics Device for Microsoft Reporting Services (SSRS)](https://rgraphicsdevice.codeplex.com/) (R Graphics Device per Microsoft Reporting Services - SSRS)

Questo progetto CodePlex fornisce il codice che consente di creare un elemento del report personalizzato che esegue il rendering dell'output grafico di R come immagine utilizzabile nei report di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  Usando l'elemento del report personalizzato, è possibile:

+ Pubblicare i grafici e i tracciati creati usando R Graphics Device nei dashboard di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]

+ Passare i parametri di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ai tracciati R

> [!NOTE]
> Per questo esempio, il codice che supporta il dispositivo di grafica R per Reporting Services deve essere installato sul server di Reporting Services, nonché in Visual Studio. Sono anche necessarie la compilazione e la configurazione manuali.

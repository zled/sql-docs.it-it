---
title: "Funzioni di ridimensionamento per l&#39;utilizzo con i dati SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "01/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "R"
ms.assetid: 5f3c9864-9c75-4688-947d-0940045b2671
caps.latest.revision: 9
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 7
---
# Funzioni di ridimensionamento per l&#39;utilizzo con i dati SQL Server
In questo argomento viene fornita una panoramica delle funzioni principali di ridimensionamento per l'utilizzo con SQL Server, insieme ai commenti sulla loro sintassi.

Per un elenco completo delle funzioni di ridimensionamento e sul loro utilizzo, vedere il [Microsoft R Server](https://msdn.microsoft.com/microsoft-r/index#) riferimento in MSDN library. 

## Funzioni per l'utilizzo di origini dati di SQL Server
Le funzioni seguenti consentono di definire un [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] origine dati. Un oggetto origine dati è un contenitore che specifica una stringa di connessione con il set di dati che si desidera, definita come una tabella, vista o query. Chiamate di stored procedure non sono supportate.  

Oltre a definire un'origine dati, è possibile eseguire istruzioni DDL da R, se si dispone di autorizzazioni necessarie per l'istanza e database. 
+ [RxSqlServerData](https://msdn.microsoft.com/microsoft-r/scaler/RxSqlServerData) -definire un [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] oggetto origine dati
+ [rxSqlServerDropTable](https://msdn.microsoft.com/microsoft-r/scaler/rxSqlServerDropTable) -eliminare un [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] tabella
+ [rxSqlServerTableExists](https://msdn.microsoft.com/microsoft-r/scaler/rxSqlServerTableExists) -verificare l'esistenza di un oggetto o tabella di database
+ [rxExecuteSQLDDL](https://msdn.microsoft.com/microsoft-r/scaler/rxExecuteSQLDDL) : eseguire un comando per definire, modificare o controllare i dati SQL, ma non restituiscono dati  

## Funzioni per la definizione o la gestione di un contesto di calcolo
Le funzioni seguenti consentono di definire un nuovo contesto di calcolo, cambiare il contesto di calcolo o identificare il contesto di calcolo corrente.
+ [RxComputeContext](https://msdn.microsoft.com/microsoft-r/scaler/RxComputeContext) -creare un contesto di calcolo. 
+ [rxInSqlServer](https://msdn.microsoft.com/microsoft-r/scaler/rxInSqlServer) -un contesto di calcolo di SQL Server che consente di generare **ridimensionamento** le funzioni eseguite in servizi di SQL Server R.
+ [rxGetComputeContext](https://msdn.microsoft.com/microsoft-r/scaler/rxGetComputeContext) -ottenere il contesto di calcolo corrente. 
+ [rxSetComputeContext](https://msdn.microsoft.com/microsoft-r/scaler/rxSetComputeContext) -specificare quale calcolare contesto da utilizzare. 

## Funzioni per l'utilizzo di un'origine dati
Dopo aver creato un oggetto origine dati, è possibile aprirlo per ottenere i dati oppure scrivere nuovi dati. A seconda delle dimensioni dei dati nell'origine, è inoltre possibile definire le dimensioni del batch come parte dell'origine dati e spostare i dati in blocchi. 
+ [rxIsOpen](https://msdn.microsoft.com/microsoft-r/scaler/rxIsOpen) -verifica se è disponibile un'origine dati
+ [rxOpen](https://msdn.microsoft.com/microsoft-r/scaler/rxOpen) -aprire un'origine dati per la lettura
+ [rxReadNext](https://msdn.microsoft.com/microsoft-r/scaler/rxReadNext) -leggere i dati da un'origine
+ [rxWriteNext](https://msdn.microsoft.com/microsoft-r/scaler/rxWriteNext) -scrivere dati nella destinazione
+ [rxClose](https://msdn.microsoft.com/microsoft-r/scaler/rxclose) -chiudere un'origine dati

Per ulteriori informazioni sull'utilizzo di queste funzioni di ridimensionamento, che siano compatibili con le origini dati diverso da [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], vedere [ Microsoft R Server - Introduzione](http://msdn.microsoft.com/microsoft-r/rserver/rserver-getting-started).

## Funzioni che utilizzano file XDF
Per creare una cache locale dei dati nel formato XDF, è possono utilizzare le funzioni seguenti. Questo file può essere utile quando si utilizzano più dati possono essere trasferiti dal database in un batch o più dati visualizzabili in memoria.

Se si spostano regolarmente grandi quantità di dati da un database in una workstation locale, invece di query del database più volte per ogni operazione R, è possibile utilizzare il file XDF per salvare i dati localmente e quindi utilizzarli nell'area di lavoro R, usando il file XDF come la cache.

+ `rxImport` -Spostare i dati da un'origine ODBC per il file XDF
+ `RxXdfData` : Consente di creare un oggetto dati XDF
+ `RxDataStep` -Leggere i dati da int XDF un frame di dati
+ `rxXdfToDataFrame` -Leggere i dati da XDF in un frame di dati
+ `rxReadXdf` -Legge i dati da XDF in un frame di dati

Per un esempio di come vengono utilizzati file XDF, vedere l'esercitazione:  [dati scienza approfondimento - utilizzo delle funzioni di ridimensionamento](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)

Per ulteriori informazioni su queste funzioni di ridimensionamento, che può essere utilizzato per trasferire i dati da molte origini diverse, vedere[ Microsoft R Server - Introduzione](http://msdn.microsoft.com/microsoft-r/rserver/rserver-getting-started).

## Vedere anche
[Confronto di Base R e delle funzioni di ridimensionamento](https://msdn.microsoft.com/microsoft-r/scaler/compare-base-r-scaler-functions)

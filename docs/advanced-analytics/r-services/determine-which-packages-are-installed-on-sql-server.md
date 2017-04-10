---
title: "Determinare i pacchetti che vengono installati in SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "08/31/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a7f7e43-b568-406c-9434-5a2ec64ec5f5
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 10
---
# Determinare i pacchetti che vengono installati in SQL Server
  Questo argomento viene descritto come è possibile determinare quali pacchetti R vengono installate le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza.  
  
Per impostazione predefinita, l'installazione di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] Crea una libreria di pacchetto R associata a ogni istanza. Pertanto, per sapere quali pacchetti vengono installati in un computer, è necessario eseguire questa query in ogni istanza separata in cui è installato Servizi di R. Si noti che le librerie di pacchetto sono **non** condivisi tra più istanze, pertanto è possibile che diversi pacchetti da installare in istanze diverse.

Per informazioni su come determinare il percorso di libreria predefinito per un'istanza, vedere [installazione e la gestione di pacchetti R](../../advanced-analytics/r-services/installing-and-managing-r-packages.md).   
   
 
## Ottenere un elenco dei pacchetti installati mediante R  
 Esistono diversi modi per ottenere un elenco dei pacchetti installati o caricati utilizzando gli strumenti di R e funzioni R.  
  
+   Molti strumenti di sviluppo di R forniscono un visualizzatore oggetti o un elenco dei pacchetti che vengono installati o caricati nell'area di lavoro corrente di R.  

+ Si consiglia le seguenti funzioni dal pacchetto RevoScaleR vengono fornite specificamente per la gestione di pacchetti in contesti di calcolo:
  - [rxFindPackage](https://msdn.microsoft.com/microsoft-r/scaler/rxfindpackage)
  - [rxInstalledPackages](https://msdn.microsoft.com/microsoft-r/scaler/rxInstalledPackages)   
  
+   È possibile usare una funzione di R, ad esempio `installed.packages()`, inclusa nel pacchetto di `utils` installato. La funzione esamina i file di descrizione di ogni pacchetto che è stato trovato nella libreria specificata e restituisce una matrice di nomi di pacchetto, i percorsi di libreria e i numeri di versione.  
 
### Esempi  
Nell'esempio seguente viene utilizzata la funzione `rxInstalledPackages` per ottenere un elenco dei pacchetti disponibili nel contesto di calcolo di SQL Server specificato.

~~~~
sqlServerCompute <- RxInSqlServer(connectionString = 
"Driver=SQL Server;Server=myServer;Database=TestDB;Uid=myID;Pwd=myPwd;")
     sqlPackages <- rxInstalledPackages(computeContext = sqlServerCompute)
     sqlPackages
~~~~

 Nell'esempio seguente viene utilizzata la funzione R base `installed.packages()` in un [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure per ottenere una matrice dei pacchetti che sono stati installati nella libreria R_SERVICES per l'istanza corrente. Per evitare l'analisi dei campi nel file DESCRIPTION, viene restituito solo il nome.  
  
```  
EXECUTE sp_execute_external_script  
@language=N'R'  
,@script = N'str(OutputDataSet);  
packagematrix <- installed.packages();  
NameOnly <- packagematrix[,1];  
OutputDataSet <- as.data.frame(NameOnly);'  
,@input_data_1 = N'SELECT 1 as col'  
WITH RESULT SETS ((PackageName nvarchar(250) ))  
```  
  
 Per ulteriori informazioni sui predefiniti e i campi facoltativi nel file di descrizione del pacchetto R, vedere [https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file](https://cran.r-project.org/doc/manuals/R-exts.html).  
  
## Vedere anche  
 [Installare pacchetti R aggiuntivi su SQL Server](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md)  
  
  
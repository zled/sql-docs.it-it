---
title: Determinare i pacchetti che vengono installati in SQL Server | Microsoft Docs
ms.custom: 
ms.date: 08/31/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a7f7e43-b568-406c-9434-5a2ec64ec5f5
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 90e7146bde123ca8ac8a8e6ff3e11d212fd4a35a
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="determine-which-packages-are-installed-on-sql-server"></a>Determinare i pacchetti che vengono installati in SQL Server
  Questo argomento descrive come determinare i pacchetti R che vengono installati nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Per impostazione predefinita, l'installazione di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] crea una libreria di pacchetti R associata a ogni istanza. Per sapere quali pacchetti sono installati in un computer, è quindi necessario eseguire questa query su ogni singola istanza in cui è installato R Services. Si noti che le librerie di pacchetti **non** sono condivise nelle istanze, quindi è possibile che pacchetti diversi siano installati in istanze diverse.

Per informazioni su come determinare il percorso predefinito di una libreria per un'istanza, vedere [Installazione e gestione dei pacchetti R](../../advanced-analytics/r-services/installing-and-managing-r-packages.md).   
   
 
## <a name="get-a-list-of-installed-packages-using-r"></a>Ottenere un elenco di pacchetti installati con R  
 Esistono diversi modi per ottenere un elenco dei pacchetti installati o caricati con gli strumenti R e le funzioni R.  
  
+   Molti strumenti di sviluppo di R forniscono un visualizzatore oggetti o un elenco dei pacchetti che vengono installati o caricati nell'area di lavoro corrente di R.  

+ Sono consigliate le funzioni seguenti del pacchetto RevoScaleR, che vengono fornite appositamente per la gestione pacchetti nei contesti di calcolo:
  - [rxFindPackage](https://msdn.microsoft.com/microsoft-r/scaler/packagehelp/rxfindpackage)
  - [rxInstalledPackages](https://msdn.microsoft.com/microsoft-r/scaler/packagehelp/rxinstalledpackages)   
  
+   È possibile usare una funzione di R, ad esempio `installed.packages()`, inclusa nel pacchetto di `utils` installato. La funzione analizza i file DESCRIPTION di ogni pacchetto trovato nella libreria specificata e restituisce una matrice di nomi di pacchetto, i percorsi di libreria e i numeri di versione.  
 
### <a name="examples"></a>Esempi  
L'esempio seguente usa la funzione `rxInstalledPackages` per ottenere un elenco di pacchetti disponibili nel contesto di calcolo di SQL Server specificato.

~~~~
sqlServerCompute <- RxInSqlServer(connectionString = 
"Driver=SQL Server;Server=myServer;Database=TestDB;Uid=myID;Pwd=myPwd;")
     sqlPackages <- rxInstalledPackages(computeContext = sqlServerCompute)
     sqlPackages
~~~~

 L'esempio seguente usa la funzione R di base `installed.packages()` in una stored procedure di [!INCLUDE[tsql](../../includes/tsql-md.md)] per ottenere una matrice di pacchetti installati nella libreria R_SERVICES per l'istanza corrente. Per evitare l'analisi dei campi nel file DESCRIPTION, viene restituito solo il nome.  
  
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
  
 Per altre informazioni, vedere la descrizione dei campi facoltativi e predefiniti per il file DESCRIPTION del pacchetto R, all'indirizzo [https://cran.r-project.org](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file).  
  
## <a name="see-also"></a>Vedere anche  
 [Installare pacchetti R aggiuntivi in SQL Server](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md)  
  
  


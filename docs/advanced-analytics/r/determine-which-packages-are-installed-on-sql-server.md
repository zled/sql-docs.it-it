---
title: Determinare quali pacchetti R vengono installati in SQL Server | Documenti Microsoft
ms.custom: 
ms.date: 10/09/2016
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a7f7e43-b568-406c-9434-5a2ec64ec5f5
caps.latest.revision: "11"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c570f5643880b1111889e29e6de03bbff4b10e1d
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2017
---
# <a name="determine-which-r-packages-are-installed-on-sql-server"></a>Determinare quali pacchetti R vengono installati in SQL Server

Quando si installa l'apprendimento di SQL Server con l'opzione di linguaggio R, il programma di installazione crea una libreria di pacchetti R associata all'istanza. Ogni istanza dispone di una libreria di pacchetto separato. Librerie del pacchetto sono **non** condivisi tra più istanze, pertanto è possibile che diversi pacchetti da installare in istanze diverse.

Questo articolo descrive come è possibile determinare quali pacchetti R vengono installati per un'istanza specifica.

## <a name="generate-r-package-list-using-a-stored-procedure"></a>Generare l'elenco dei pacchetti R tramite una stored procedure

Nell'esempio seguente viene utilizzata la funzione di R `installed.packages()` in un [!INCLUDE [tsql](..\..\includes\tsql-md.md)] stored procedure per ottenere una matrice di pacchetti che sono stati installati nella libreria R_SERVICES per l'istanza corrente. Per evitare l'analisi dei campi nel file DESCRIPTION, viene restituito solo il nome.

```SQL
EXECUTE sp_execute_external_script
@language=N'R'  
,@script = N'str(OutputDataSet);  
packagematrix <- installed.packages();  
NameOnly <- packagematrix[,1];  
OutputDataSet <- as.data.frame(NameOnly);'  
,@input_data_1 = N'SELECT 1 as col'  
WITH RESULT SETS ((PackageName nvarchar(250) ))  
```

Per ulteriori informazioni su facoltativo e campi predefiniti per il file di descrizione del pacchetto R, vedere [https://cran.r-project.org](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file).

## <a name="verify-whether-a-package-is-installed-with-an-instance"></a>Verificare se un pacchetto viene installato con un'istanza

Se si è installato un pacchetto e si desidera assicurarsi che sia disponibile per una particolare istanza di SQL Server, è possibile eseguire la seguente chiamata di stored procedure per caricare il pacchetto e restituire solo i messaggi.

```SQL
EXEC sp_execute_external_script  @language =N'R',
@script=N'library("RevoScaleR")'
GO
```

In questo esempio cerca e carica la libreria RevoScaleR.

+ Se il pacchetto viene trovato, il messaggio restituito deve essere un'operazione quale "Comandi vengano eseguiti correttamente."

+ Se è Impossibile trovare o caricare il pacchetto, si verifica un errore simile al seguente: "si è verificato un errore dello script esterno: errore in library("RevoScaleR"): nessun pacchetto RevoScaleR chiamato"

## <a name="get-a-list-of-installed-packages-using-r"></a>Ottenere un elenco dei pacchetti installati con R

Esistono diversi modi per ottenere un elenco dei pacchetti installati o caricati con gli strumenti R e le funzioni R. Molti strumenti di sviluppo di R forniscono un visualizzatore oggetti o un elenco dei pacchetti che vengono installati o caricati nell'area di lavoro corrente di R.

+ Da un'utilità R locale, utilizzare una funzione R di base, ad esempio `installed.packages()`, incluso nel `utils` pacchetto. Per ottenere un elenco che è preciso per un'istanza, è necessario specificare in modo esplicito il percorso di libreria o utilizzare gli strumenti di R associati con la libreria di istanza.

+ Per verificare se un pacchetto in un contesto di calcolo specifico, è possibile utilizzare le funzioni seguenti dal pacchetto RevoScaleR. Queste funzioni consentono di identificare i pacchetti in contesti di calcolo specificata:

+ [rxFindPackage](https://msdn.microsoft.com/microsoft-r/scaler/packagehelp/rxfindpackage)

+ [rxInstalledPackages](https://msdn.microsoft.com/microsoft-r/scaler/packagehelp/rxinstalledpackages)

Ad esempio, eseguire il seguente codice R per ottenere un elenco dei pacchetti disponibili nel contesto di calcolo specificato di SQL Server.

```r
sqlServerCompute <- RxInSqlServer(connectionString = "Driver=SQL Server;Server=myServer;Database=TestDB;Uid=myID;Pwd=myPwd;")
sqlPackages <- rxInstalledPackages(computeContext = sqlServerCompute)
sqlPackages
```
## <a name="see-also"></a>Vedere anche

[Installare pacchetti R aggiuntivi su SQL Server](install-additional-r-packages-on-sql-server.md)

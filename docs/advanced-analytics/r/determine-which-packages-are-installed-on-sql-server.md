---
title: Determinare quali pacchetti R vengono installati in SQL Server | Documenti Microsoft
ms.custom: 
ms.date: 01/04/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a7f7e43-b568-406c-9434-5a2ec64ec5f5
caps.latest.revision: "11"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e3f906e0c5290b6aa2cab375e4761390f84e718d
ms.sourcegitcommit: 60d0c9415630094a49d4ca9e4e18c3faa694f034
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="determine-which-r-packages-are-installed-on-sql-server"></a>Determinare quali pacchetti R vengono installati in SQL Server

Quando si installa l'apprendimento di SQL Server con l'opzione di linguaggio R, una libreria di pacchetti R viene creata appositamente per l'utilizzo dall'istanza. Ogni istanza del server ha la propria libreria del pacchetto. Librerie del pacchetto non possono essere condivisa tra più istanze.

Questo articolo descrive come è possibile determinare quali pacchetti R installati per una specifica istanza di SQL Server.

## <a name="generate-r-package-list-using-a-stored-procedure"></a>Generare l'elenco dei pacchetti R tramite una stored procedure

Nell'esempio seguente viene utilizzata la funzione di R `installed.packages()` in un [!INCLUDE [tsql](..\..\includes\tsql-md.md)] stored procedure per ottenere una matrice di pacchetti che sono stati installati nella libreria R_SERVICES per l'istanza corrente. Per evitare l'analisi dei campi nel file DESCRIPTION, viene restituito solo il nome.

```SQL
EXECUTE sp_execute_external_script
@language=N'R'
,@script = N'str(OutputDataSet);
packagematrix <- installed.packages();
NameOnly <- packagematrix[,1];
OutputDataSet <- as.data.frame(NameOnly);'
, @input_data_1 = N''
WITH RESULT SETS ((PackageName nvarchar(250) ))
```

Per ulteriori informazioni su facoltativo e campi predefiniti per il campo della descrizione del pacchetto R, vedere [https://cran.r-project.org](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file).

## <a name="verify-whether-a-package-is-installed-with-an-instance"></a>Verificare se un pacchetto viene installato con un'istanza

Se si è installato un pacchetto e si desidera assicurarsi che sia disponibile per una particolare istanza di SQL Server, è possibile eseguire la seguente chiamata di stored procedure per caricare il pacchetto e restituire solo i messaggi. In questo esempio cerca e carica la libreria RevoScaleR, se disponibile.

```sql
EXEC sp_execute_external_script  @language =N'R',
@script=N'library("RevoScaleR")'
GO
```

+ Se il pacchetto viene trovato, viene restituito un messaggio: "Comandi vengano eseguiti correttamente."

+ Se è Impossibile trovare o caricare il pacchetto, si verifica un errore che contiene il testo: "non è presente alcun pacchetto chiamato 'MissingPackageName'"

## <a name="get-a-list-of-installed-packages-using-r"></a>Ottenere un elenco dei pacchetti installati con R

Esistono diversi modi per ottenere un elenco dei pacchetti installati o caricati con gli strumenti R e le funzioni R. Molti strumenti di sviluppo di R forniscono un visualizzatore oggetti o un elenco dei pacchetti che vengono installati o caricati nell'area di lavoro corrente di R. Questa sezione vengono fornite alcune brevi comandi che è possibile utilizzare da qualsiasi riga di comando di R o sp\_eseguire\_esterno\_script.

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

## <a name="get-library-location-and-version"></a>Ottenere una versione e il percorso di libreria

Nell'esempio seguente ottiene la posizione della raccolta di RevoScaleR nel contesto di calcolo locale e la versione del pacchetto.

```r
rxFindPackage(RevoScaleR, "local")
packageVersion("RevoScaleR")
```

## <a name="determine-path-of-library-used-by-sql-server"></a>Determinare percorso di libreria utilizzata da SQL Server

Se è stato aggiornato di machine learning componenti mediante l'associazione, il percorso alla libreria R potrebbe cambiare. In questo caso, tasti di scelta rapida precedente degli strumenti di R potrebbe fare riferimento a una versione precedente. Per essere certi della versione del pacchetto e del percorso utilizzata da SQL Server, è possibile eseguire un comando analogo al seguente:

```sql
EXEC sp_execute_external_script
    @language =N'R',
    @script=N'
    sql_r_path <- rxSqlLibPaths("local")
      print(sql_r_path)
    version_info <-packageVersion("RevoScaleR")
      print(version_info)'
```

**Risultati**

```text
STDOUT message(s) from external script: 
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER1000/R_SERVICES/library"
[1] '9.2.1'
```
## <a name="see-also"></a>Vedere anche

[Installare pacchetti R aggiuntivi su SQL Server](install-additional-r-packages-on-sql-server.md)

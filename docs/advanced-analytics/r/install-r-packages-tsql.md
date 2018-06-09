---
title: Utilizzare T-SQL (creare libreria esterna) per installare i pacchetti R in servizi di SQL Server Machine Learning | Documenti Microsoft
description: Aggiungere i nuovi pacchetti R in SQL Server 2017 Machine Learning Services (In-Database)
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/30/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 7a5a0c394e9a26244661a4ae712d20583c1f1c99
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34585483"
---
# <a name="use-t-sql-create-external-library-to-install-r-packages-on-sql-server-2017-machine-learning-services"></a>Utilizzare T-SQL (creare libreria esterna) per installare i pacchetti R in servizi di SQL Server 2017 Machine Learning
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo articolo viene illustrato come installare i nuovi pacchetti di R in un'istanza di SQL Server in cui è abilitata l'apprendimento automatico. Esistono diversi approcci disponibili tra cui scegliere. Utilizzo di T-SQL è adatto per gli amministratori di server che ha familiarità con R.

**Si applica a:**  [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

Il [creare libreria esterna](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) istruzione consente di aggiungere un pacchetto o un set di pacchetti a un'istanza o un database specifico senza eseguire R o Python code direttamente. Tuttavia, questo metodo richiede la preparazione del pacchetto e le autorizzazioni di database aggiuntivo.

+ Tutti i pacchetti devono essere disponibili come un file compresso locale, anziché scaricati su richiesta da internet.

+ Tutte le dipendenze devono essere identificate dal nome e la versione e inclusi nel file zip. L'istruzione ha esito negativo se pacchetti richiesti non sono disponibili, tra cui le dipendenze dei pacchetti a valle. 

+ È necessario essere **db_owner** oppure disporre dell'autorizzazione CREATE libreria esterna in un ruolo del database. Per informazioni dettagliate, vedere [creare libreria esterna](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql).

## <a name="download-packages-in-archive-format"></a>Scaricare i pacchetti in formato di archiviazione

Se si sta installando un singolo pacchetto, è possibile scaricare il pacchetto in formato compresso.

È più comune per installare più pacchetti a causa di dipendenze di pacchetto. Quando un pacchetto richiede altri pacchetti, è necessario verificare che tutti gli elementi sono accessibili a altro durante l'installazione. È consigliabile [creazione di un repository locale](create-a-local-package-repository-using-minicran.md) utilizzando [miniCRAN](http://andrie.github.io/miniCRAN/) per assemblare un insieme completo di pacchetti, nonché [igraph](http://igraph.org/r/) per l'analisi delle dipendenze dei pacchetti. Installare la versione non corretta di un pacchetto o l'omissione di una dipendenza pacchetto può causare un'esito negativo dell'istruzione CREATE libreria esterna. 

## <a name="copy-the-file-to-a-local-folder"></a>Copiare il file in una cartella locale

Copiare il file compresso che contiene tutti i pacchetti in una cartella locale nel server. Se non si dispone dell'accesso al file system nel server, è inoltre possibile passare un pacchetto completo come una variabile, utilizzando un formato binario. Per ulteriori informazioni, vedere [creare libreria esterna](../../t-sql/statements/create-external-library-transact-sql.md).

## <a name="run-the-statement-to-upload-packages"></a>Eseguire l'istruzione per caricare i pacchetti

Aprire un **Query** finestra, utilizzando un account con privilegi amministrativi.

Eseguire l'istruzione T-SQL `CREATE EXTERNAL LIBRARY` per caricare la raccolta di pacchetto compresso nel database.

Ad esempio, l'istruzione seguente nomi, come origine del pacchetto, di un repository miniCRAN contenenti il **randomForest** pacchetto, insieme alle relative dipendenze. 

```SQL
CREATE EXTERNAL LIBRARY randomForest
FROM (CONTENT = 'C:\Temp\Rpackages\randomForest_4.6-12.zip')
WITH (LANGUAGE = 'R');
```

Non è possibile utilizzare un nome arbitrario. il nome della libreria esterna deve avere lo stesso nome che si prevede di utilizzare durante il caricamento o la chiamata del pacchetto.

## <a name="verify-package-installation"></a>Verificare l'installazione del pacchetto

Se la raccolta è stata creata, è possibile eseguire il pacchetto in SQL Server, quando viene chiamata all'interno di una stored procedure.
    
```SQL
EXEC sp_execute_external_script
@language =N'R',
@script=N'library(randomForest)'
```

## <a name="see-also"></a>Vedere anche

+ [Ottenere informazioni sui pacchetti](determine-which-packages-are-installed-on-sql-server.md)
+ [Esercitazioni di R](../tutorials/sql-server-r-tutorials.md)
+ [Guide pratiche](sql-server-machine-learning-tasks.md)
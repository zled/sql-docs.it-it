---
title: Utilizzare T-SQL (creare libreria esterna) per installare i pacchetti R in servizi di SQL Server Machine Learning | Documenti Microsoft
description: Aggiungere i nuovi pacchetti R in SQL Server 2017 Machine Learning Services (In-Database)
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/20/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: bbc1adf4868cbfbd02afe5cae3a38fd6223e2d4d
ms.sourcegitcommit: b5ab9f3a55800b0ccd7e16997f4cd6184b4995f9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2018
---
# <a name="use-t-sql-create-external-library-to-install-r-packages-on-sql-server-2017-machine-learning-services"></a>Utilizzare T-SQL (creare libreria esterna) per installare i pacchetti R in servizi di SQL Server 2017 Machine Learning
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo articolo viene descritto come installare i nuovi pacchetti di R a un'istanza di SQL Server in cui è abilitato l'apprendimento. Esistono diversi approcci disponibili tra cui scegliere. Questo approccio è adatto per gli amministratori di server che ha familiarità con R.

**Si applica a:**  [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

Il [creare libreria esterna](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) istruzione consente di aggiungere un pacchetto o un set di pacchetti a un'istanza o un database specifico senza eseguire R o Python code direttamente. Tuttavia, questo metodo richiede la preparazione del pacchetto e le autorizzazioni di database aggiuntivo.

+ Tutti i pacchetti devono essere disponibili come un file compresso locale, anziché scaricati su richiesta da internet.

+ Tutte le dipendenze devono essere identificate dal nome e la versione e inclusi nel file zip. L'istruzione ha esito negativo se pacchetti richiesti non sono disponibili, tra cui le dipendenze dei pacchetti a valle. 

+ È necessario disporre delle autorizzazioni necessarie nel database. Per informazioni dettagliate, vedere [creare libreria esterna](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql).

## <a name="download-packages-in-archive-format"></a>Scaricare i pacchetti in formato di archiviazione

Se si sta installando un singolo pacchetto, è possibile scaricare il pacchetto in formato compresso.

Se il pacchetto richiede eventuali altri pacchetti, è necessario verificare che i pacchetti richiesti siano disponibili. È possibile utilizzare miniCRAN per analizzare il pacchetto di destinazione e identificare tutte le relative dipendenze. Si consiglia di usare [ **miniCRAN** ](create-a-local-package-repository-using-minicran.md) oppure [ **igraph** ](http://igraph.org/r/) per l'analisi delle dipendenze dei pacchetti. Installazione della versione errata del pacchetto o una dipendenza pacchetto possono causare l'esito negativo dell'istruzione. 

## <a name="copy-the-file-to-a-local-folder"></a>Copiare il file in una cartella locale

Copiare il file compresso che contiene tutti i pacchetti in una cartella locale nel server. Se non si dispone dell'accesso al file system nel server, è inoltre possibile passare un pacchetto completo come una variabile, utilizzando un formato binario. Per ulteriori informazioni, vedere [creare libreria esterna](../../t-sql/statements/create-external-library-transact-sql.md).

## <a name="run-the-statement-to-upload-packages"></a>Eseguire l'istruzione per caricare i pacchetti

Aprire un **Query** finestra, utilizzando un account con privilegi amministrativi.

Eseguire l'istruzione T-SQL `CREATE EXTERNAL LIBRARY` per caricare la raccolta di pacchetto compresso nel database.

    For example, the following statement names as the package source a miniCRAN repository containing the **randomForest** package, together with its dependencies. 

    ```R
    CREATE EXTERNAL LIBRARY randomForest
    FROM (CONTENT = 'C:\Temp\Rpackages\randomForest_4.6-12.zip')
    WITH (LANGUAGE = 'R');
    ```

    You cannot use an arbitrary name; the external library name must have the same name that you expect to use when loading or calling the package.

## <a name="verify-package-installation"></a>Verificare l'installazione del pacchetto

Se la raccolta è stata creata, è possibile eseguire il pacchetto in SQL Server, quando viene chiamata all'interno di una stored procedure.
    
    ```SQL
    EXEC sp_execute_external_script
    @language =N'R',
    @script=N'
    library(randomForest)'
    ```


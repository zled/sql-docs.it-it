---
title: Lezione 1 i dati di esempio di Download e script per embedded R (SQL Server Machine Learning Services) | Microsoft Docs
description: Esercitazione che illustra come incorporare R in SQL Server stored procedure e funzioni T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/07/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 74a60a95da4fb701f3862c36e35a4bada6ef933b
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38030379"
---
# <a name="lesson-1-download-data-and-scripts"></a>Lezione 1: Scaricare i dati e gli script
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo fa parte di un'esercitazione per sviluppatori SQL su come usare R in SQL Server.

In questo passaggio, verrà scaricato il set di dati di esempio e [!INCLUDE[tsql](../../includes/tsql-md.md)] file che vengono usati in questa esercitazione di script. Sia i dati e i file di script sono condivisi in GitHub, ma lo script di PowerShell scaricherà i file di dati e script in una directory locale di propria scelta.

## <a name="download-tutorial-files-from-github"></a>Scaricare i file dell'esercitazione da Github

1.  Aprire una console dei comandi di Windows PowerShell.
  
    Usare l'opzione **Esegui come amministratore**se sono necessari privilegi amministrativi per creare la directory di destinazione o per scrivere i file nella destinazione specificata.
  
2.  Eseguire i seguenti comandi di PowerShell modificando il valore del parametro *DestDir* in una directory locale.  Il valore predefinito usato in questo caso è **TempRSQL**.
  
    ```ps
    $source = ‘https://raw.githubusercontent.com/Azure/Azure-MachineLearning-DataScience/master/Misc/RSQL/Download_Scripts_SQL_Walkthrough.ps1’  
    $ps1_dest = “$pwd\Download_Scripts_SQL_Walkthrough.ps1”
    $wc = New-Object System.Net.WebClient
    $wc.DownloadFile($source, $ps1_dest)
    .\Download_Scripts_SQL_Walkthrough.ps1 –DestDir ‘C:\tempRSQL’
    ```
  
    Se la cartella *DestDir* specificata non esiste, verrà creata dallo script di PowerShell.
  
    > [!TIP]
    > Se si verifica un errore, è possibile impostare temporaneamente i criteri per l'esecuzione di script di PowerShell su **Senza restrizioni** solo per questa procedura dettagliata, usando l'argomento Bypass e definendo l'ambito delle modifiche alla sessione corrente.
    >   
    >````
    > Set\-ExecutionPolicy Bypass \-Scope Process
    >````
    > Questo comando non comporta una modifica della configurazione.
  
    A seconda della connessione Internet, il download potrebbe richiedere alcuni minuti.
  
3.  Dopo aver scaricato tutti i file, lo script di PowerShell si aprirà nella cartella specificata con il nome  *DestDir*. Nel prompt dei comandi di PowerShell eseguire il comando seguente ed esaminare i file scaricati.
  
    ```
    ls
    ```
  
    **Risultati:**
  
    ![Elenco dei file scaricati dallo script di PowerShell](media/rsql-devtut-filelist.png "Elenco dei file scaricati dallo script di PowerShell")
  
## <a name="next-lesson"></a>Lezione successiva

[Lezione 2: Importare i dati in SQL Server usando PowerShell](../r/sqldev-import-data-to-sql-server-using-powershell.md)

## <a name="previous-lesson"></a>Lezione precedente

[Analitica incorporata di R per sviluppatori SQL](../tutorials/sqldev-in-database-r-for-sql-developers.md)

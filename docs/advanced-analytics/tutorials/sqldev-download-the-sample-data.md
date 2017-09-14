---
title: 'Lezione 1: Scaricare i dati di esempio | Documenti Microsoft'
ms.custom: 
ms.date: 07/26/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
dev_langs:
- R
- TSQL
ms.assetid: 32a5d5ad-c58a-4669-a90d-ef296b48fcd8
caps.latest.revision: 10
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1843dc06a0587e34e0ed369ea54fd5b71b217b24
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-1-download-the-sample-data"></a>Lezione 1: Scaricare i dati di esempio

In questo articolo fa parte di un'esercitazione per gli sviluppatori SQL su come usare il linguaggio R in SQL Server.

In questo passaggio, verrà scaricato il set di dati di esempio e [!INCLUDE[tsql](../../includes/tsql-md.md)] dello script di file che vengono utilizzati in questa esercitazione. I dati e i file di script vengono condivisi su GitHub, ma lo script di PowerShell scaricherà i file di dati e script in una directory locale di propria scelta.

## <a name="download-the-data-and-scripts"></a>Scaricare i dati e gli script

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

[Lezione 2: Importare dati in SQL Server tramite PowerShell](../r/sqldev-import-data-to-sql-server-using-powershell.md)

## <a name="previous-lesson"></a>Lezione precedente

[Analitica R nel database per gli sviluppatori SQL](../tutorials/sqldev-in-database-r-for-sql-developers.md)

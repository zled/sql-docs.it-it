---
title: Passaggio 1 scaricare i dati di esempio | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 541066ac00efc1b15f8cae838097cfd8ee49df3d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="step-1-download-the-sample-data"></a>Passaggio 1: Scaricare i dati di esempio
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo articolo fa parte di un'esercitazione, [analitica Python nel database per gli sviluppatori SQL](sqldev-in-database-python-for-sql-developers.md). 

I dati e gli script per questa esercitazione vengono condivisi su Github. In questo passaggio, utilizzare uno script di PowerShell per scaricare i file di dati e script in una directory locale di propria scelta.

## <a name="run-the-script"></a>Eseguire lo script

1. Aprire una console dei comandi di Windows PowerShell.

    Utilizzare l'opzione **Esegui come amministratore**, se sono necessari privilegi di amministratore per creare la directory di destinazione o per scrivere file di destinazione specificata.

2. Eseguire i seguenti comandi di PowerShell modificando il valore del parametro *DestDir* in una directory locale.  Il valore predefinito è stata utilizzata in questo caso è `C:\temp\pysql`.

    ```ps
    $source = 'https://raw.githubusercontent.com/Azure/Azure-MachineLearning-DataScience/master/Misc/PythonSQL/Download_Scripts_SQL_Walkthrough.ps1'
    $ps1_dest = "$pwd\Download_Scripts_SQL_Walkthrough.ps1"
    $wc = New-Object System.Net.WebClient
    $wc.DownloadFile($source, $ps1_dest)
    .\Download_Scripts_SQL_Walkthrough.ps1 –DestDir 'C:\temp\pysql'
    ```
    
    Se la cartella *DestDir* specificata non esiste, verrà creata dallo script di PowerShell.
    
    Se si verifica un errore, impostare temporaneamente i criteri per l'esecuzione di script di PowerShell per **senza restrizioni** per questa procedura dettagliata, usando il **Bypass** argomento e le modifiche alla sessione corrente di ambito. Questo comando non comporta una modifica della configurazione.
    
    ```ps
    Set-ExecutionPolicy Bypass -Scope Process
    ```

3. A seconda della connessione internet, il download potrebbe richiedere qualche istante. 

## <a name="view-the-results"></a>Visualizzare i risultati

Dopo aver scaricato tutti i file, lo script di PowerShell si aprirà nella cartella specificata con il nome  *DestDir*. 

+ Nel prompt dei comandi di PowerShell, eseguire il comando seguente, per elencare i file che sono stati scaricati.

    ```ps
    ls
    ```

![Elenco dei file scaricati dallo script di PowerShell](media/sqldev-python-filelist.png "Elenco dei file scaricati dallo script di PowerShell")

## <a name="next-step"></a>Passaggio successivo

[Passaggio 2: Importare i dati in SQL Server usando PowerShell](sqldev-py2-import-data-to-sql-server-using-powershell.md)

## <a name="previous-step"></a>Passaggio precedente

[Python Analitica nel Database per gli sviluppatori di SQL](sqldev-in-database-python-for-sql-developers.md)

## <a name="see-also"></a>Vedere anche

[Servizi di Machine Learning con Python](../python/sql-server-python-services.md)



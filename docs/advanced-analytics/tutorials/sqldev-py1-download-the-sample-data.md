---
title: 'Passaggio 1: Scaricare i dati di esempio | Documenti Microsoft'
ms.custom: 
ms.date: 05/25/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2017
dev_langs:
- Python
- TSQL
ms.assetid: 
caps.latest.revision: 2
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 147860e9af8cce86d1a7ccbd3e53f20d240fcd49
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="step-1-download-the-sample-data"></a>Passaggio 1: Scaricare i dati di esempio

In questo passaggio, verrà scaricato il set di dati di esempio e gli script. Sia i dati e che i file di script sono condivisi in GitHub. Lo script di PowerShell scaricherà tuttavia i dati e i file di script in una directory locale a scelta.

## <a name="download-the-data-and-scripts"></a>Scaricare i dati e gli script

1. Aprire una console dei comandi di Windows PowerShell.

    Utilizzare l'opzione **Esegui come amministratore**, se sono necessari privilegi di amministratore per creare la directory di destinazione o per scrivere file di destinazione specificata.

2. Eseguire i seguenti comandi di PowerShell modificando il valore del parametro *DestDir* in una directory locale.  Il valore predefinito è stata utilizzata in questo caso è **TempPythonSQL**.

    ```
    $source = 'https://raw.githubusercontent.com/Azure/Azure-MachineLearning-DataScience/master/Misc/PythonSQL/Download_Scripts_SQL_Walkthrough.ps1'
    $ps1_dest = "$pwd\Download_Scripts_SQL_Walkthrough.ps1"
    $wc = New-Object System.Net.WebClient
    $wc.DownloadFile($source, $ps1_dest)
    .\Download_Scripts_SQL_Walkthrough.ps1 –DestDir 'C:\tempPythonSQL'
    ```
    
    Se la cartella *DestDir* specificata non esiste, verrà creata dallo script di PowerShell.
    
    Se si verifica un errore, è possibile impostare temporaneamente i criteri per l'esecuzione di script di PowerShell per **senza restrizioni** solo per questa procedura dettagliata, usando il **Bypass** argomento e le modifiche all'oggetto di ambito sessione. Questo comando non comporta una modifica della configurazione.
    
    `Set\-ExecutionPolicy Bypass \-Scope Process`

3. A seconda della connessione Internet, il download potrebbe richiedere alcuni minuti. Dopo aver scaricato tutti i file, lo script di PowerShell si aprirà nella cartella specificata con il nome  *DestDir*. Nel prompt dei comandi di PowerShell eseguire il comando seguente ed esaminare i file scaricati.

    ```
    ls
    ```
**Risultati:**

![Elenco dei file scaricati dallo script di PowerShell](media/sqldev-python-filelist.png "Elenco dei file scaricati dallo script di PowerShell")

## <a name="next-step"></a>Passaggio successivo

[Passaggio 2: Importare i dati in SQL Server usando PowerShell](sqldev-py2-import-data-to-sql-server-using-powershell.md)

## <a name="previous-step"></a>Passaggio precedente

[Python Analitica nel Database per gli sviluppatori di SQL](sqldev-in-database-python-for-sql-developers.md)

## <a name="see-also"></a>Vedere anche

[Servizi di Machine Learning con Python](../python/sql-server-python-services.md)




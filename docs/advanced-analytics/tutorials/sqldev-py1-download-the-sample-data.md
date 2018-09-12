---
title: Passaggio 1 scaricare i dati di esempio | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 07a9b5219649b370b0a5df1e53cf75765f18ec7f
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "43888319"
---
# <a name="step-1-download-the-sample-data"></a>Passaggio 1: Scaricare i dati di esempio
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo fa parte di un'esercitazione [analitica di Python nel database per sviluppatori SQL](sqldev-in-database-python-for-sql-developers.md). 

I dati e gli script per questa esercitazione vengono condivisi in Github. In questo passaggio si usa uno script di PowerShell per scaricare i file di dati e script in una directory locale di propria scelta.

## <a name="run-the-script"></a>Eseguire lo script

1. Aprire una console dei comandi di Windows PowerShell.

    Usare l'opzione **Esegui come amministratore**, se sono necessari privilegi amministrativi per creare la directory di destinazione o per scrivere i file nella destinazione specificata.

2. Eseguire i seguenti comandi di PowerShell modificando il valore del parametro *DestDir* in una directory locale.  Il valore predefinito è usato in questo caso è `C:\temp\pysql`.

    ```ps
    $source = 'https://raw.githubusercontent.com/Azure/Azure-MachineLearning-DataScience/master/Misc/PythonSQL/Download_Scripts_SQL_Walkthrough.ps1'
    $ps1_dest = "$pwd\Download_Scripts_SQL_Walkthrough.ps1"
    $wc = New-Object System.Net.WebClient
    $wc.DownloadFile($source, $ps1_dest)
    .\Download_Scripts_SQL_Walkthrough.ps1 –DestDir 'C:\temp\pysql'
    ```
    
    Se la cartella *DestDir* specificata non esiste, verrà creata dallo script di PowerShell.
    
    Se si verifica un errore, impostare temporaneamente i criteri per l'esecuzione di script di PowerShell per **senza restrizioni** questa procedura dettagliata, usando la **Bypass** argomento e le modifiche alla sessione corrente di ambito. Questo comando non comporta una modifica della configurazione.
    
    ```ps
    Set-ExecutionPolicy Bypass -Scope Process
    ```

3. A seconda della connessione internet, il download potrebbe richiedere qualche minuto. 

## <a name="view-results"></a>Visualizzare i risultati

Dopo aver scaricato tutti i file, lo script di PowerShell si aprirà nella cartella specificata con il nome  *DestDir*. 

+ Al prompt dei comandi di PowerShell, eseguire il comando seguente per elencare i file che sono stati scaricati.

    ```ps
    ls
    ```

![Elenco dei file scaricati dallo script di PowerShell](media/sqldev-python-filelist.png "Elenco dei file scaricati dallo script di PowerShell")

## <a name="next-step"></a>Passaggio successivo

[Passaggio 2: Importare i dati in SQL Server usando PowerShell](sqldev-py2-import-data-to-sql-server-using-powershell.md)

## <a name="previous-step"></a>Passaggio precedente

[Python Analitica nel Database per sviluppatori SQL](sqldev-in-database-python-for-sql-developers.md)

## <a name="see-also"></a>Vedere anche

[Estensione di Python in SQL Server](../concepts/extension-python.md)



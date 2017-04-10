---
title: "Passaggio 1: Scaricare i dati di esempio (esercitazione di analisi avanzata dei dati nel database) | Microsoft Docs"
ms.custom: ""
ms.date: "04/19/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
  - "TSQL"
ms.assetid: 32a5d5ad-c58a-4669-a90d-ef296b48fcd8
caps.latest.revision: 10
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 10
---
# Passaggio 1: Scaricare i dati di esempio (esercitazione di analisi avanzata dei dati nel database)
In questo passaggio sarò scaricato il set di dati di esempio e i file di script [!INCLUDE[tsql](../../includes/tsql-md.md)] usati in questa procedura dettagliata. Sia i dati e che i file di script sono condivisi in GitHub. Lo script di PowerShell scaricherà tuttavia i dati e i file di script in una directory locale a scelta.  
  
## Scaricare i dati e gli script  
  
1.  Aprire una console dei comandi di Windows PowerShell.  
  
    Usare l'opzione **Esegui come amministratore** se sono necessari privilegi amministrativi per creare la directory di destinazione o per scrivere i file nella destinazione specificata.  
  
2.  Eseguire i seguenti comandi di PowerShell modificando il valore del parametro *DestDir* in una directory locale.  Il valore predefinito usato in questo caso è **TempRSQL**.  
  
    ```  
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
  
3.  Dopo aver scaricato tutti i file, lo script di PowerShell si aprirà nella cartella specificata con il nome *DestDir*. Nel prompt dei comandi di PowerShell eseguire il comando seguente ed esaminare i file scaricati.  
  
    ```  
    ls  
    ```  
  
    **Risultati:**  
  
    ![list of files downloaded by PowerShell script](../../advanced-analytics/r-services/media/rsql-devtut-filelist.PNG "list of files downloaded by PowerShell script")  
  
## Passaggio successivo  
[Passaggio 2: Importare i dati in SQL Server usando PowerShell](../../advanced-analytics/r-services/step-2-import-data-to-sql-server-using-powershell.md)  
  
## Passaggio precedente  
[Analisi avanzata nel database per sviluppatori SQL &#40;Esercitazione&#41;](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)  
  
## Vedere anche  
[Esercitazioni di SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
  
  
  

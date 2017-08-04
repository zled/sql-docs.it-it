---
title: Flusso di lavoro ETL | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- samples
ms.custom: 
ms.date: 06/15/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 679e58fe-b062-4934-a94c-9bb916b0bcb0
caps.latest.revision: 5
author: BarbKess
ms.author: barbkess
manager: jhubbard
robots: noindex,nofollow
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 85898dfc3a12ee195910bf965f0099b35f95b239
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="wideworldimportersdw-etl-workflow"></a>Flusso di lavoro WideWorldImportersDW ETL
Il pacchetto ETL WWI_Integration viene utilizzato per la migrazione dei dati dal database WideWorldImporters al database WideWorldImportersDW come le modifiche dei dati. Il pacchetto viene eseguito periodicamente (in genere ogni giorno).

## <a name="overview"></a>Panoramica

La progettazione del pacchetto utilizza SQL Server Integration Services (SSIS) per poter gestire le operazioni bulk T-SQL (anziché come trasformazioni separate all'interno di SSIS) per garantire prestazioni elevate.

Le dimensioni vengono caricate per primi, seguito da tabelle dei fatti. Il pacchetto può essere nuovamente eseguito in qualsiasi momento dopo un errore.

Il flusso di lavoro è come segue:

 ![Flusso di lavoro WideWorldImporters ETL](../../sample/world-wide-importers/media/wideworldimporters-etl-workflow.png)

Inizia un'attività di espressione che utilizza il tempo limite appropriato. Questo tempo è l'ora corrente meno qualche minuto. Questo è più affidabile rispetto alla richiesta di dati direttamente all'ora corrente. Verrà quindi troncato qualsiasi millisecondi dal momento.

L'elaborazione principale Avvia popolamento della tabella della dimensione Data. Assicura che siano state popolate tutte le date per l'anno corrente nella tabella.

Successivamente, una serie di attività del flusso di dati carica ogni dimensione, quindi ogni fatto.

## <a name="prerequisites"></a>Prerequisiti

- SQL Server 2016 (o versioni successive) con i database WideWorldImporters e WideWorldImportersDW. Può trattarsi nelle istanze di SQL Server uguale o diverse.
- SQL Server Management Studio (SSMS)
- SQL Server 2016 Integration Services (SSIS).
  - Assicurarsi di che aver creato un catalogo SSIS. In caso contrario, fare clic destro **Integration Services** in Esplora oggetti di SQL Server Management Studio, scegliere **aggiungere catalogo**. Seguono le impostazioni predefinite. Verrà chiesto di abilitare sqlclr e fornire una password.


## <a name="download"></a>Scarica

La versione più recente dell'esempio:

[unità di importazione di world wide-rilascio](http://go.microsoft.com/fwlink/?LinkID=800630)

Scaricare il file del pacchetto SSIS **ETL.ispac giornaliero**.

Il codice sorgente per ricreare il database di esempio è disponibile dal seguente percorso.

[livello mondo](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/wwi-integration-etl)

## <a name="install"></a>Install

1. Distribuire il pacchetto SSIS.
   - Aprire il pacchetto "ETL.ispac giornaliero" da Esplora risorse. Verrà avviata la distribuzione guidata di Integration Services.
   - In "Seleziona origine" seguire il valore predefinito di distribuzione del progetto, con il percorso che punta al pacchetto "ETL.ispac giornaliero".
   - Nella sezione "Destinazione selezionare" Immettere il nome del server che ospita il catalogo SSIS.
   - Selezionare un percorso all'interno del catalogo SSIS, ad esempio in una nuova cartella "WideWorldImporters".
   - Completare la procedura guidata, fare clic su Distribuisci.

2. Creare un processo di SQL Server Agent per il processo ETL.
   - In SSMS, pulsante destro del mouse "SQL Server Agent" e selezionare New -> processi.
   - Scegliere un nome, ad esempio "WideWorldImporters ETL".
   - Aggiungere un passaggio del processo di tipo "Pacchetto SQL Server Integration Services".
   - Selezionare il server con il catalogo SSIS e selezionare il pacchetto "ETL giornaliero".
   - Configurazione -> gestioni connessioni verificare le connessioni all'origine e destinazione siano configurate correttamente. Il valore predefinito è per la connessione all'istanza locale.
   - Fare clic su OK per creare il processo.

3. Eseguire o pianificare il processo.


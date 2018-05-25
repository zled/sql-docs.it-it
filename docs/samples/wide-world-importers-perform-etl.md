---
title: WideWorldImportersDW - flusso di lavoro ETL | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 36638c4cc2bda58ac277822d5c4a4ce5421ab8b4
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2018
---
# <a name="wideworldimportersdw-etl-workflow"></a>Flusso di lavoro WideWorldImportersDW ETL
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Usare la *WWI_Integration* pacchetto ETL per la migrazione dei dati dal database WideWorldImporters al database WideWorldImportersDW le modifiche dei dati. Il pacchetto viene eseguito periodicamente (in genere ogni giorno).

Il pacchetto assicura prestazioni elevate utilizzando SQL Server Integration Services per orchestrare le operazioni bulk T-SQL (anziché separate trasformazioni in Integration Services).

Le quote vengano caricate per primi, e quindi vengono caricate le tabelle dei fatti. È possibile eseguire di nuovo il pacchetto in qualsiasi momento dopo un errore.

Il flusso di lavoro è simile al seguente:

 ![Flusso di lavoro WideWorldImporters ETL](media/wide-world-importers/wideworldimporters-etl-workflow.png)

Il flusso di lavoro inizia con un'attività di espressione che determina il tempo limito appropriato. Il tempo di cambio data è l'ora corrente meno qualche minuto. (Questo approccio è più affidabile rispetto alla richiesta di dati direttamente all'ora corrente). Dal momento in cui vengono troncati qualsiasi millisecondi.

L'elaborazione principale Avvia popolamento della tabella della dimensione Data. L'elaborazione assicura che siano state popolate tutte le date per l'anno corrente nella tabella.

Successivamente, una serie di attività flusso di dati carica ogni dimensione. Quindi, devono essere caricati ogni fatto.

## <a name="prerequisites"></a>Prerequisiti

- SQL Server 2016 (o versione successiva), con i database WideWorldImporters e WideWorldImportersDW (nello stesso o in istanze diverse di SQL Server)
- SQL Server Management Studio
- SQL Server 2016 Integration Services
  - Assicurarsi di creare un catalogo di Integration Services. Per creare un catalogo di Integration Services, in Esplora oggetti di SQL Server Management Studio, fare doppio clic su **Integration Services**, quindi selezionare **aggiungere catalogo**. Lasciare le opzioni predefinite. Viene chiesto di abilitare SQLCLR e fornire una password.


## <a name="download"></a>Scarica

Per la versione più recente dell'esempio, vedere [world wide-rilascio importers](http://go.microsoft.com/fwlink/?LinkID=800630). Scaricare il *ETL.ispac giornaliero* file del pacchetto Integration Services.

Per il codice sorgente ricreare il database di esempio, vedere [wide mondo](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/wwi-integration-etl).

## <a name="install"></a>Install

1. Distribuire il pacchetto di Integration Services:
   1. In Esplora risorse, aprire il *ETL.ispac giornaliero* pacchetto. Verrà avviata la distribuzione guidata di SQL Server Integration Services.
   2. Sotto **Seleziona origine**, seguono le impostazioni predefinite per la distribuzione del progetto, con il percorso che punta al *ETL.ispac giornaliero* pacchetto.
   3. Sotto **Seleziona destinazione**, immettere il nome del server che ospita il catalogo di Integration Services.
   4. Selezionare un percorso del catalogo di Integration Services, ad esempio, in una nuova cartella denominata *WideWorldImporters*.
   5. Selezionare **Distribuisci** per completare la procedura guidata.

2. Creare un processo di SQL Server Agent per il processo ETL:
   1. In Management Studio, fare doppio clic su **SQL Server Agent**, quindi selezionare **New** > **processo**.
   2. Immettere un nome, ad esempio *WideWorldImporters ETL*.
   3. Aggiungere un **passaggio processo** del tipo **pacchetto SQL Server Integration Services**.
   4. Selezionare il server contenente il catalogo di Integration Services e quindi selezionare il *ETL giornaliera* pacchetto.
   5. Sotto **Configuration** > **Gestioni**, assicurarsi che le connessioni all'origine e destinazione siano configurate correttamente. Il valore predefinito è per la connessione all'istanza locale.
   6. Selezionare **OK** per creare il processo.

3. Eseguire o pianificare il processo.

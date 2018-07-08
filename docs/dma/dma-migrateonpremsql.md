---
title: Eseguire la migrazione di un on-premises SQL Server con Data Migration Assistant | Microsoft Docs
description: Informazioni su come usare Data Migration Assistant per eseguire la migrazione di un Server SQL locale a un altro SQL Server o Database SQL di Azure
ms.custom: ''
ms.date: 09/01/2017
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, on-premises SQL Server
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.openlocfilehash: 8133b4176fc8f8197cab646d51f4ece68b6250bc
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/04/2018
ms.locfileid: "37784812"
---
# <a name="migrate-an-on-premises-sql-server-with-data-migration-assistant"></a>Eseguire la migrazione di un on-premises SQL Server con Data Migration Assistant

Questo articolo vengono fornite istruzioni dettagliate per la migrazione del Server SQL usando Data Migration Assistant. Data Migration Assistant fornisce facile valutazioni e le migrazioni per piattaforme di dati moderna in locale della macchina virtuale di SQL Azure e SQL Server e Database SQL di Azure.  

Per eseguire la migrazione, completare le attività seguenti.

- [Creare un nuovo progetto di migrazione](#create-a-new-migration-project)
- [Specificare l'origine e destinazione](#specify-source-and-target)
- [Aggiungere i database](#add-databases)
- [Selezionare gli account di accesso](#select-logins)

## <a name="create-a-new-migration-project"></a>Creare un nuovo progetto di migrazione

1. Fare clic su **New** (+) nel riquadro a sinistra e selezionare il **migrazione** tipo di progetto.

1. Il tipo di server di origine e di destinazione impostato su **SQL Server** se si sta aggiornando un Server SQL locale a una moderna SQL Server locale.

1. Fare clic su **Crea**.

   ![Crea progetto di migrazione](../dma/media/NewCreate.png)

## <a name="specify-the-source-and-target"></a>Specificare l'origine e destinazione

1. Per l'origine, immettere il nome dell'istanza SQL Server nel **nome Server** campo le **i dettagli del server di origine** sezione. 

1. Selezionare il **tipo di autenticazione** supportati dall'istanza di SQL Server di origine.

1. Per la destinazione, immettere il nome dell'istanza SQL Server nel **nome Server** campo le **i dettagli del server di destinazione** sezione. 

1. Selezionare il **tipo di autenticazione** supportati dall'istanza di SQL Server di destinazione.

1. È consigliabile crittografare la connessione selezionando **Encrypt connection** nel **delle proprietà di connessione** sezione.

1. Scegliere **Avanti**.

   ![Pagina di origine e di destinazione specifica](../dma/media/SourceTarget.png)

## <a name="add-databases"></a>Aggiungere i database

1. Scegliere i database specifici che si desidera migrare selezionando solo questi database, nel riquadro sinistro della finestra di **aggiungono database** pagina.

   Per impostazione predefinita sono selezionati tutti i database utente nell'istanza di SQL Server di origine per la migrazione

1. Usare le impostazioni della migrazione sul lato destro della pagina per impostare le opzioni di migrazione che vengono applicate ai database, eseguire le operazioni seguenti.

   > [!NOTE]
   > È possibile applicare le impostazioni di migrazione in tutti i database che si esegue la migrazione, selezionando il server nel riquadro sinistro. È anche possibile configurare un database singolo con impostazioni specifiche selezionando il database nel riquadro sinistro.

 1. Specificare il **condiviso percorso accessibile dal server SQL di origine e destinazione per l'operazione di backup**. Assicurarsi che l'account del servizio in esecuzione l'origine SQL Server istanza dispone di scrivere privilegi per la posizione condivisa e l'account del servizio di destinazione dispone di privilegi di lettura per la posizione condivisa.

 1. Specificare il percorso in cui ripristinare i dati e file di log transazionale nel server di destinazione.

    ![Aggiungi pagina di database](../dma/media/AddDatabases.png)

1. Immettere un percorso condiviso a cui le istanze di SQL Server di origine e di destinazione hanno accesso, nelle **condividono opzioni posizione** casella.

1. Se non è possibile fornire un percorso condiviso che istanze di SQL Server di origine e destinazione hanno accesso, selezionare **copiare i backup del database in un percorso diverso che il server di destinazione può leggere e ripristinare dalla**. Quindi, immettere un valore per il **percorso per i backup per l'opzione di ripristino** casella. 

   Assicurarsi che l'account utente che esegue Data Migration Assistant disponga dei privilegi necessari per il percorso di backup di lettura e scrittura i privilegi per il percorso da cui ripristinare il server di destinazione.

   ![Opzione per copiare i backup dei database in un percorso diverso](../dma/media/CopyDatabaseDifferentLocation.png)

1. Scegliere **Avanti**.

Data Migration Assistant esegue le convalide nelle cartelle di backup, log e dati percorsi dei file. Se qualsiasi convalida non riesce, correggere le opzioni e fare clic su **successivo**.

## <a name="select-logins"></a>Selezionare gli account di accesso

1. Selezionare un account di accesso specifici per la migrazione.

   > [!IMPORTANT]
   > Assicurarsi di selezionare gli account di accesso viene eseguito il mapping a uno o più utenti nei database selezionati per la migrazione.   

   Per impostazione predefinita, tutti i Server SQL e Windows gli account di accesso che soddisfano le condizioni per la migrazione sono selezionati per la migrazione.

1. Fare clic su **avviare la migrazione**.

   ![Selezionare gli account di accesso e avviare la migrazione](../dma/media/SelectLogins.png)

## <a name="view-results"></a>Visualizzare i risultati

È possibile monitorare l'avanzamento della migrazione sul **visualizzare i risultati** pagina.

![Pagina di visualizzazione dei risultati](../dma/media/ViewResults.png)

## <a name="export-migration-results"></a>Esportare i risultati della migrazione

1. Fare clic su **esportare report** in fondo il **visualizzare risultati** pagina per salvare i risultati di migrazione in un file CSV.

1. Esaminare il file salvato per informazioni dettagliate relative alla migrazione di account di accesso e quindi verificare le modifiche.

## <a name="see-also"></a>Vedere anche

[Data Migration Assistant (DMA)](../dma/dma-overview.md)

[Data Migration Assistant: Le impostazioni di configurazione](../dma/dma-configurationsettings.md)

[Data Migration Assistant: Procedure consigliate](../dma/dma-bestpractices.md)

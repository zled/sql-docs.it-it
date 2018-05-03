---
title: Eseguire la migrazione di Server SQL locale (dati Migration Assistant) | Documenti Microsoft
ms.custom: ''
ms.date: 09/01/2017
ms.prod: sql
ms.prod_service: dma
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-dma
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
ms.openlocfilehash: fd4c8e57b0854fb56eafa3d90b31bfddbe6455a3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="migrate-on-premises-sql-server-using-data-migration-assistant"></a>Eseguire la migrazione di Server SQL locale utilizzando dati Migration Assistant

In questo articolo vengono fornite istruzioni dettagliate per la migrazione a SQL Server utilizzando dati Migration Assistant.

Fornisce dati Migration Assistant valutazioni trasparente e le migrazioni a piattaforme di dati di SQL Server e SQL Azure VM moderna locale.  

Completare le attività seguenti per eseguire la migrazione.

- [Creare un nuovo progetto di migrazione](#create-a-new-migration-project)
- [Specificare l'origine e destinazione](#specify-source-and-target)
- [Aggiungere i database](#add-databases)
- [Selezionare gli account di accesso](#select-logins)

## <a name="create-a-new-migration-project"></a>Creare un nuovo progetto di migrazione

1. Fare clic su **New** (+) nel riquadro sinistro e selezionare il **migrazione** tipo di progetto.

1. Impostare il tipo di server di origine e destinazione su **SQL Server** se si esegue l'aggiornamento di un Server SQL locale per un moderno SQL Server locale.

1. Fare clic su **Crea**.

   ![Creare il progetto di migrazione](../dma/media/NewCreate.png)

## <a name="specify-the-source-and-target"></a>Specificare l'origine e destinazione

1. Per l'origine, immettere il nome di istanza di SQL Server nel **nome Server** campo il **i dettagli del server di origine** sezione. 

1. Selezionare il **tipo di autenticazione** supportati dall'istanza di SQL Server di origine.

1. Per la destinazione, immettere il nome di istanza di SQL Server nel **nome Server** campo il **i dettagli del server di destinazione** sezione. 

1. Selezionare il **tipo di autenticazione** supportati dall'istanza di SQL Server di destinazione.

1. È consigliabile crittografare la connessione selezionando **Crittografa connessione** nel **le proprietà di connessione** sezione.

1. Scegliere **Avanti**.

   ![Pagina di origine e di destinazione specifica](../dma/media/SourceTarget.png)

## <a name="add-databases"></a>Aggiungere i database

1. Scegliere i database specifici che si desidera eseguire la migrazione selezionando solo tali database, nel riquadro sinistro della finestra di **aggiungere database** pagina.

   Per impostazione predefinita sono selezionati tutti i database utente nell'istanza di SQL Server di origine per la migrazione

1. Utilizzare le impostazioni di migrazione sul lato destro della pagina per impostare le opzioni di migrazione che vengono applicate ai database, eseguire le operazioni seguenti.

   > [!NOTE]
   > È possibile applicare le impostazioni di migrazione per tutti i database che si esegue la migrazione, selezionando il server nel riquadro a sinistra. È anche possibile configurare un singolo database con impostazioni specifiche selezionando il database nel riquadro a sinistra.


 1. Specificare il **condiviso percorso accessibile da server SQL di origine e destinazione per l'operazione di backup**. Verificare che l'account del servizio in esecuzione l'origine dispone di istanza di SQL Server di accesso di scrittura al percorso condiviso e l'account del servizio di destinazione dispone di privilegi di lettura per la posizione condivisa.

 1. Specificare il percorso in cui ripristinare i dati e file di log transazionale nel server di destinazione.

    ![Aggiungere la pagina di database](../dma/media/AddDatabases.png)

1. Immettere un percorso condiviso a cui le istanze di SQL Server di origine e di destinazione hanno accesso, nel **condividono opzioni posizione** casella.

1. Se non è possibile fornire un percorso condiviso che SQL Server di origine e destinazione hanno accesso a determinate **copiare i backup del database in un percorso diverso che il server di destinazione può leggere e ripristinare da**. Quindi, immettere un valore per il **percorso per il backup per l'opzione di ripristino** casella. 

   Assicurarsi che l'account utente che esegue Data Migration Assistant disponga dei privilegi necessari per il percorso di backup di lettura e privilegi di scrittura per il percorso da cui ripristinare il server di destinazione.

   ![Opzione per copiare i backup del database in un percorso diverso](../dma/media/CopyDatabaseDifferentLocation.png)

1. Scegliere **Avanti**.

Dati della migrazione guidata esegue la convalida per le cartelle di backup, dati e log percorsi di file. Se qualsiasi convalida non riesce, correggere le opzioni e fare clic su **Avanti**.

## <a name="select-logins"></a>Selezionare gli account di accesso

1. Selezionare un account di accesso specifici per la migrazione.

   > [!IMPORTANT]
   > Assicurarsi di selezionare gli account di accesso viene eseguito il mapping a uno o più utenti nei database selezionati per la migrazione.   

   Per impostazione predefinita, SQL Server e Windows gli account di accesso che soddisfano le condizioni per la migrazione sono selezionate per la migrazione.

1. Fare clic su **avviare la migrazione**.

   ![Selezionare gli account di accesso e avviare la migrazione](../dma/media/SelectLogins.png)

## <a name="view-results"></a>Visualizzare i risultati

È possibile monitorare l'avanzamento della migrazione sul **visualizzare risultati** pagina.

![Pagina di visualizzazione dei risultati](../dma/media/ViewResults.png)

## <a name="export-migration-results"></a>Esportare i risultati della migrazione

1. Fare clic su **esportare report** in fondo il **visualizzare risultati** pagina per salvare i risultati della migrazione in un file CSV.

1. Esaminare il file salvato per informazioni dettagliate sulla migrazione di account di accesso e quindi verificare le modifiche.

## <a name="see-also"></a>Vedere anche

[Data Migration Assistant (DMA)](../dma/dma-overview.md)

[Dati Migration Assistant: Le impostazioni di configurazione](../dma/dma-configurationsettings.md)

[Dati Migration Assistant: Procedure consigliate](../dma/dma-bestpractices.md)

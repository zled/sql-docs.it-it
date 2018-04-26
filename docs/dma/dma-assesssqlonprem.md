---
title: Eseguire una valutazione della migrazione a SQL Server (dati della migrazione guidata) | Documenti Microsoft
ms.custom: ''
ms.date: 10/04/2017
ms.prod: sql
ms.prod_service: dma
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-dma
ms.tgt_pltfrm: ''
ms.topic: article
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fe0447cf841eb5b45526d3a8fd1099c84ad4113c
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="perform-a-sql-server-migration-assessment"></a>Eseguire una valutazione della migrazione a SQL Server
Le procedure dettagliate seguenti consentono di eseguire la prima valutazione per la migrazione di on-premise SQL Server, SQL Server in esecuzione nella macchina virtuale di Azure o Database SQL di Azure, tramite dati Migration Assistant.

## <a name="create-an-assessment"></a>Creare una valutazione

1.  Selezionare il **New** (+), icona e quindi selezionare il **valutazione** tipo di progetto.

2.  Impostare il tipo di server di origine e di destinazione.

    Se si aggiorna l'istanza di SQL Server locale a un'istanza di SQL Server on-premise moderna o a SQL Server ospitato in una macchina virtuale di Azure, è possibile impostare il tipo di server di origine e di destinazione su **SQL Server**. Se si esegue la migrazione di Database SQL di Azure, al contrario impostare il tipo di server di destinazione su **Database SQL di Azure**.

3.  Fare clic su **Crea**.

    ![Creare una valutazione](../dma/media/NewAssessment.png)

## <a name="choose-assessment-options"></a>Scegliere le opzioni di valutazione

1. Selezionare la versione di SQL Server di destinazione che si intende eseguire la migrazione a.

2. Selezionare il tipo di report.

   Quando si desidera valutare l'istanza di SQL Server di origine per la migrazione al Server SQL locale o a SQL Server ospitati in destinazioni di macchina virtuale di Azure, è possibile scegliere uno o entrambi i tipi di report di valutazione seguenti:

    -   **Problemi di compatibilità**

    -   **Indicazione di nuove funzionalità**

    ![Selezionare un tipo di report di valutazione per la destinazione di SQL Server](../dma/media/AssessmentTypes.png)

   Quando si desidera valutare l'istanza di SQL Server di origine per la migrazione di Database SQL di Azure, è possibile scegliere uno o entrambi i tipi di report di valutazione seguenti:

    -   **Verificare la compatibilità di database**

    -   **Parità di funzionalità di controllo**

    ![Selezione tipo di report di valutazione per il Database SQL di destinazione](../dma/media/AssessmentTypes_Azure.png)

## <a name="add-databases-to-assess"></a>Aggiungere i database per valutare

1.  Selezionare **aggiungere origini** per aprire il menu a comparsa connessione.

2.  Immettere il nome dell'istanza SQL server, scegliere il tipo di autenticazione, impostare le proprietà di connessione corrette e quindi selezionare **Connetti**.

3.  Selezionare i database per valutare e quindi selezionare **Aggiungi**.

    > [!NOTE] 
    > È possibile rimuovere più database selezionandoli durante tenendo premuto il tasto MAIUSC o Ctrl e quindi fare clic su **rimuovere origini**. È anche possibile aggiungere i database da più istanze di SQL Server utilizzando il **aggiungere origini** pulsante.

4.  Fare clic su **Avanti** per iniziare la valutazione.

    ![Aggiungere le origini e avviare valutazione](../dma/media/SelectDatabase.png)

## <a name="view-results"></a>Visualizzare i risultati

La durata della valutazione varia a seconda del numero di database aggiunto e le dimensioni dello schema di ogni database. Risultati vengono visualizzati per ogni database, non appena sono disponibili.

1.  Selezionare il database che è stata completata la valutazione e quindi passare tra **problemi di compatibilità** e **funzionalità indicazioni** tramite la selezione.

2.  Esaminare i problemi di compatibilità per tutti i livelli di compatibilità supportati dalla versione di SQL Server di destinazione selezionato nel **opzioni** pagina.

È possibile esaminare i problemi di compatibilità per l'analisi di oggetto interessato e i relativi dettagli per ogni problema identificato in **modifiche di rilievo**, **modifiche del comportamento**, e **funzionalità deprecate** .

![Visualizzare i risultati della valutazione](../dma/media/ReviewResults.png)

Analogamente, è possibile esaminare l'indicazione di funzionalità tra **prestazioni**, **archiviazione**, e **sicurezza** aree.

Funzionalità indicazioni illustrano una varietà di funzionalità come OLTP In memoria e Columnstore, estensione Database, crittografia sempre attiva, la maschera dati dinamica e Transparent Data Encryption.

![Visualizzare le indicazioni funzionalità](../dma/media/FeatureRecommendations.png)

Database SQL di Azure, le valutazioni forniscono i problemi di blocco di migrazione e problemi di parità della funzionalità. Esaminare i risultati per entrambe le categorie selezionando le opzioni specifiche.

- Il **parità di funzionalità di SQL Server** categoria fornisce un set completo di indicazioni, disponibile in Azure e attenuazione agli approcci alternativi. Consente di pianificare questa attività nei progetti di migrazione.

  ![Visualizzare le informazioni di parità di funzionalità di SQL Server](../dma/media/SQLFeatureParity.png)

- Il **problemi di compatibilità** categoria fornisce funzionalità parzialmente supportate o non supportata che blocca la migrazione i database di SQL Server locale al database SQL di Azure. Fornisce quindi indicazioni che consentono di risolvere tali problemi.

  ![Problemi di compatibilità di visualizzazione](../dma/media/CompatibilityIssues.png)

## <a name="export-results"></a>Esportare i risultati

Al termine della valutazione tutti i database, selezionare **esportare report** per esportare i risultati in un file JSON o un file CSV. È quindi possibile analizzare i dati a seconda delle proprie esigenze.

È possibile eseguire contemporaneamente più valutazioni e visualizzare lo stato delle valutazioni aprendo il **tutte le valutazioni** pagina.

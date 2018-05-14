---
title: "Lezione dell'esercitazione di Analysis Services 11: creare ruoli | Documenti Microsoft"
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfiles"
ms.openlocfilehash: 8e630d53aed8f722c2de4a21afea8391cefe8bd8
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="create-roles"></a>Creazione di ruoli

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In questa lezione si creare ruoli. I ruoli garantiscono protezione dati e oggetti di database modello, limitando l'accesso solo agli utenti che sono membri del ruolo. Ogni ruolo è definito con una singola autorizzazione, di lettura, lettura ed elaborazione, elaborazione o amministratore oppure nessuna autorizzazione. I ruoli possono essere definiti durante la creazione di modelli tramite Gestione ruoli. Dopo la distribuzione di un modello, è possibile gestire ruoli tramite SQL Server Management Studio (SSMS). Per ulteriori informazioni, vedere [ruoli](../tabular-models/roles-ssas-tabular.md).
  
> [!NOTE]  
> La creazione di ruoli non è necessaria per completare questa esercitazione. Per impostazione predefinita, l'account a cui che si è connessi con privilegi di amministratore per il modello. Tuttavia, per altri utenti nell'organizzazione esplorare utilizzando uno strumento client, è necessario creare almeno un ruolo lettura autorizzazioni e aggiungere tali utenti come membri.  
  
Creare tre ruoli:  
  
-   **Responsabile vendite** : questo ruolo può includere gli utenti dell'organizzazione per il quale si desidera avere autorizzazione di lettura per tutti i dati e oggetti modello.  
  
-   **Sales Analyst US** : questo ruolo può includere gli utenti dell'organizzazione per il quale si desidera solo essere in grado di esplorare i dati correlati alle vendite negli Stati Uniti. Per questo ruolo, è possibile per definire una formula DAX un *filtro di riga*, che limita i membri per esplorare i dati solo per gli Stati Uniti.  
  
-   **Amministratore** : questo ruolo può includere utenti per cui si desidera concedere l'autorizzazione di amministratore, che consente accesso illimitato e autorizzazioni per eseguire attività amministrative sul database modello.  
  
Poiché gli account di gruppo e utente di Windows nell'organizzazione sono univoci, è possibile aggiungere account dell'organizzazione specifica ai membri. Tuttavia, per questa esercitazione, è anche possibile lasciare i membri vuoti. Testare l'effetto di ogni ruolo in un secondo momento nella lezione 12: analizza in Excel.  
  
Tempo stimato per il completamento della lezione: **15 minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  

In questo articolo fa parte di un'esercitazione di modellazione tabulare, che deve essere completata nell'ordine. Prima di eseguire le attività in questa lezione, è necessario avere completato la lezione precedente: [lezione 10: creare partizioni](../tutorial-tabular-1400/as-lesson-10-create-partitions.md).  
  
## <a name="create-roles"></a>Creazione di ruoli  
  
#### <a name="to-create-a-sales-manager-user-role"></a>Per creare un ruolo utente Sales Manager  
  
1.  In Esplora modelli tabulari, fare doppio clic su **ruoli** > **ruoli**.  
  
2.  Fare clic su Gestione ruoli, **New**.  
  
3.  Fare clic sul nuovo ruolo e quindi la **nome** colonna, rinominare il ruolo in **Sales Manager**.  
  
4.  Nella colonna **Autorizzazioni** fare clic nell'elenco a discesa, quindi selezionare l'autorizzazione **Lettura** . 

    ![as-lesson11-new-role](../tutorial-tabular-1400/media/as-lesson11-new-role.png) 
  
5.  Facoltativo: Fare clic su di **membri** scheda e quindi fare clic su **Aggiungi**. Nella finestra di dialogo **Selezione utenti o gruppi** immettere i gruppi o gli utenti di Windows dell'organizzazione che si desidera includere nel ruolo.  
  
#### <a name="to-create-a-sales-analyst-us-user-role"></a>Per creare un ruolo utente Sales Analyst US  
  
1.  Fare clic su Gestione ruoli, **New**.    
  
2.  Rinominare il ruolo in **Sales Analyst US**.  
  
3.  Assegnare il ruolo specificato **lettura** autorizzazione.  
  
4.  Fare clic sulla scheda filtri di riga e quindi per il **DimGeography** tabella solo nella colonna filtro DAX digitare la formula seguente:  
  
    ```Administrator
    =DimGeography[CountryRegionCode] = "US" 
    ```
    
    Una formula di filtro di riga deve essere risolta in un valore booleano (TRUE/FALSE). Con questa formula, si specifica che solo le righe con il valore del codice paese "US" sono visibili all'utente.  
    ![as-lesson11-role-filter](../tutorial-tabular-1400/media/as-lesson11-role-filter.png) 
  
6.  Facoltativo: Fare clic su di **membri** scheda e quindi fare clic su **Aggiungi**. Nella finestra di dialogo **Selezione utenti o gruppi** immettere i gruppi o gli utenti di Windows dell'organizzazione che si desidera includere nel ruolo.  
  
#### <a name="to-create-an-administrator-user-role"></a>Per creare un ruolo utente amministratore  
  
1.  Fare clic su **Nuovo**.  
  
2.  Rinominare il ruolo in **amministratore**.  
  
3.  Assegnare il ruolo specificato **amministratore** autorizzazione.  
  
4.  Facoltativo: Fare clic su di **membri** scheda e quindi fare clic su **Aggiungi**. Nella finestra di dialogo **Selezione utenti o gruppi** immettere i gruppi o gli utenti di Windows dell'organizzazione che si desidera includere nel ruolo. 
  
  
## <a name="whats-next"></a>Quali sono le operazioni successive?

[Lezione 12: Analizza in Excel](../tutorial-tabular-1400/as-lesson-12-analyze-in-excel.md).

  
  

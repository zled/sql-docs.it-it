---
title: "Lezione 12: Creare ruoli | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 984face4-00fc-46d3-8ae1-9755bf737bdf
caps.latest.revision: 17
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Lezione 12: Creare ruoli
In questa lezione verranno creati ruoli. I ruoli forniscono la sicurezza per i dati e gli oggetti del database modello, limitando l'accesso unicamente agli utenti di Windows che sono membri del ruolo. Ogni ruolo è definito con una singola autorizzazione, di lettura, lettura ed elaborazione, elaborazione o amministratore oppure nessuna autorizzazione. È possibile definire i ruoli durante la creazione del modello tramite la finestra di dialogo Gestione ruoli in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]. Dopo la distribuzione di un modello, è possibile gestire i ruoli tramite [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Per altre informazioni, vedere [Ruoli &#40;SSAS tabulare&#41;](../analysis-services/tabular-models/roles-ssas-tabular.md).  
  
> [!NOTE]  
> La creazione di ruoli non è necessaria per completare questa esercitazione. Per impostazione predefinita, l'account con il quale è stato attualmente effettuato l'accesso dispone di privilegi di amministratore nel modello. Per consentire ad altri utenti nell'organizzazione di esplorare il modello utilizzando un'applicazione client di creazione di report, è tuttavia necessario creare almeno un ruolo che disponga di autorizzazioni di lettura e aggiungere tali utenti come membri.  
  
Verranno creati tre ruoli:  
  
-   Sales Manager: questo ruolo può includere gli utenti nell'organizzazione per i quali si desidera concedere l'autorizzazione di lettura per i dati e gli oggetti del modello.  
  
-   Sales Analyst US: questo ruolo può includere gli utenti nell'organizzazione per i quali si desidera consentire l'esplorazione dei dati correlati alle vendite negli Stati Uniti. Per questo ruolo, si utilizzerà una formula DAX per definire un *Filtro di riga* che consente ai membri di esplorare solo i dati per gli Stati Uniti.  
  
-   Amministratore: questo ruolo può includere gli utenti per i quali si desidera concedere l'autorizzazione di amministratore, che garantisce accesso illimitato e autorizzazioni per l'esecuzione di attività amministrative sul database modello.  
  
Poiché gli account di gruppo e utente di Windows nell'organizzazione sono univoci, è possibile aggiungere account dell'organizzazione specifica ai membri. Tuttavia, per questa esercitazione, è anche possibile lasciare i membri vuoti. Sarà ancora possibile verificare gli effetti di ciascun ruolo più avanti nella Lezione 12: Analizzare in Excel.  
  
Tempo stimato per il completamento della lezione: **15 minuti**  
  
## Prerequisiti  
Questo argomento fa parte di un'esercitazione relativa alla modellazione tabulare che deve essere completata nell'ordine specificato. Prima di eseguire le attività in questa lezione è necessario aver completato la lezione precedente: [Lezione 11: Creare partizioni](../analysis-services/lesson-11-create-partitions.md).  
  
## Creazione di ruoli  
  
#### Per creare un ruolo utente Sales Manager  
  
1.  In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] scegliere **Ruoli** dal menu **Modello**.  
  
2.  Nella finestra di dialogo **Gestione ruoli** fare clic su **Nuovo**.  
  
    All'elenco verrà aggiunto un nuovo ruolo con l'autorizzazione Nessuno.  
  
3.  Fare clic sul nuovo ruolo, quindi nella colonna **Nome** rinominare il ruolo in **Internet Sales Manager**.  
  
4.  Nella colonna **Autorizzazioni** fare clic nell'elenco a discesa, quindi selezionare l'autorizzazione **Lettura**.  
  
5.  Facoltativo: fare clic sulla scheda **Membri**, quindi su **Aggiungi**.  
  
6.  Nella finestra di dialogo **Selezione utenti o gruppi** immettere i gruppi o gli utenti di Windows dell'organizzazione che si desidera includere nel ruolo.  
  
7.  Verificare le opzioni selezionate, quindi fare clic su **OK**  
  
#### Per creare un ruolo utente Sales Analyst US  
  
1.  In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] scegliere **Ruoli** dal menu **Modello**.  
  
2.  Nella finestra di dialogo **Gestione ruoli** fare clic su **Nuovo**.  
  
    All'elenco verrà aggiunto un nuovo ruolo con l'autorizzazione Nessuno.  
  
3.  Fare clic sul nuovo ruolo, quindi nella colonna **Nome** rinominare il ruolo in **Internet Sales US**.  
  
4.  Nella colonna **Autorizzazioni** fare clic nell'elenco a discesa, quindi selezionare l'autorizzazione **Lettura**.  
  
5.  Fare clic sulla scheda Filtri di riga, quindi, solo per la tabella **Geography**, digitare la formula seguente nella colonna Filtro DAX:  
  
    **=Geography[Country Region Code] = "US"**  
  
    Una formula di filtro di riga deve essere risolta in un valore booleano (TRUE/FALSE). Con questa formula, si specifica che solo le righe il cui valore Country Region Code è "US" sono visibili all'utente.  
  
    Dopo avere completato la compilazione della formula, premere INVIO.  
  
6.  Facoltativo: fare clic sulla scheda **Membri**, quindi su **Aggiungi**.  
  
7.  Nella finestra di dialogo **Seleziona utenti o gruppi** immettere i gruppi o gli utenti di Windows dell'organizzazione da includere nel ruolo.  
  
8.  Verificare le opzioni selezionate, quindi fare clic su **OK**  
  
#### Per creare un ruolo di amministratore  
  
1.  Nella finestra di dialogo **Gestione ruoli** fare clic su **Nuovo**.  
  
2.  Fare clic sul nuovo ruolo, quindi nella colonna **Nome** rinominare il ruolo in **Internet Sales Administrator**.  
  
3.  Nella colonna **Autorizzazioni** fare clic nell'elenco a discesa, quindi selezionare l'autorizzazione **Amministratore**.  
  
4.  Fare clic sulla scheda **Membri**, quindi su **Aggiungi**.  
  
5.  Facoltativo: nella finestra di dialogo **Seleziona utenti o gruppi** immettere i gruppi o gli utenti di Windows dell'organizzazione da includere nel ruolo.  
  
6.  Verificare le opzioni selezionate, quindi fare clic su **OK**  
  
## Passaggi successivi  
Per continuare questa esercitazione, passare alla lezione successiva: [Lezione 13: Analizza in Excel](../analysis-services/lesson-13-analyze-in-excel.md).  
  
  
  

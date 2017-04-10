---
title: "Analizzare un modello tabulare in Excel (SSAS tabulare) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.asvs.bidtoolset.chooseperspect.f1"
ms.assetid: 47fa45fc-60ab-41a1-bde3-5781c8462889
caps.latest.revision: 13
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 13
---
# Analizzare un modello tabulare in Excel (SSAS tabulare)
  La funzionalità Analizza in Excel di [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] consente di aprire Microsoft Excel, di creare una connessione dell'origine dati al database dell'area di lavoro del modello e di aggiungere automaticamente una tabella pivot al foglio di lavoro. Gli oggetti del modello (tabelle, colonne, misure, gerarchie e indicatori KPI) sono inclusi come campi nel relativo elenco della tabella pivot.  
  
> [!NOTE]  
>  Per usare la funzionalità Analizza in Excel, è necessario che Microsoft Office 2003 o versione successiva sia installato nello stesso computer di [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. In caso contrario, è possibile utilizzare Excel in un altro computer e connettersi al database dell'area di lavoro modello come origine dati. Successivamente, è possibile aggiungere manualmente una tabella pivot al foglio di lavoro. Gli oggetti del modello (tabelle, colonne, misure e indicatori KPI) sono inclusi come campi nel relativo elenco della tabella pivot.  
  
## Attività  
  
#### Per analizzare un progetto di modello tabulare tramite la funzionalità Analizza in Excel  
  
1.  In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] fare clic sul menu **Modello** e quindi scegliere **Analizza in Excel**.  
  
2.  Nella finestra di dialogo **Scegli credenziale e prospettive** selezionare una delle seguenti opzioni relative alle credenziali per connettersi all'origine dati dell'area di lavoro del modello:  
  
    -   Per usare l'account utente corrente, selezionare **Utente di Windows corrente**.  
  
    -   Per usare un account utente diverso, selezionare **Altro utente di Windows**.  
  
         In genere, questo account utente sarà membro di un ruolo. Non è necessaria alcuna password. L'account può essere utilizzato solo nel contesto di una connessione di Excel al database dell'area di lavoro.  
  
    -   Per usare un ruolo di sicurezza, fare clic su **Ruolo** e quindi, nella casella di riepilogo, selezionare uno o più ruoli.  
  
         I ruoli di sicurezza devono essere definiti utilizzando Gestione ruoli. Per altre informazioni, vedere [Creare e gestire ruoli &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/create-and-manage-roles-ssas-tabular.md).  
  
3.  Per usare una prospettiva, nella casella di riepilogo **Prospettiva** selezionare una prospettiva.  
  
     Le prospettive (diverse dall'impostazione predefinita) devono essere definite tramite la finestra di dialogo Prospettive. Per altre informazioni, vedere [Creare e gestire prospettive &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/create-and-manage-perspectives-ssas-tabular.md).  
  
> [!NOTE]  
>  L'elenco di campi della tabella pivot in Excel non viene aggiornato automaticamente mentre si apportano modifiche al progetto di modello in Progettazione modelli. Per aggiornare l'elenco di campi della tabella pivot, fare clic su **Aggiorna** nella barra multifunzione **Opzioni** di Excel.  
  
## Vedere anche  
 [Analizzare in Excel &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md)  
  
  
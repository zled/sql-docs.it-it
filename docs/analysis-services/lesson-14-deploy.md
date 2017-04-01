---
title: "Lezione 14: Distribuire | Microsoft Docs"
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
ms.assetid: 24863a8a-9017-415a-a97b-fbac76ed0675
caps.latest.revision: 25
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Lezione 14: Distribuire
In questa lezione verranno configurate proprietà di distribuzione, specificando un'istanza del server di distribuzione di Analysis Services in esecuzione in modalità tabulare e un nome per il modello distribuito. Si distribuirà quindi il modello nell'istanza. Dopo la distribuzione, gli utenti possono connettersi al modello utilizzando un'applicazione client di creazione di report. Per altre informazioni, vedere [Distribuzione di una soluzione del modello tabulare &#40;SSAS tabulare&#41;](../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md).  
  
Tempo stimato per il completamento della lezione: **5 minuti**  
  
## Prerequisiti  
Questo argomento fa parte di un'esercitazione relativa alla modellazione tabulare che deve essere completata nell'ordine specificato. Prima di eseguire le attività in questa lezione è necessario aver completato la lezione precedente: [Lezione 13: Analizza in Excel](../analysis-services/lesson-13-analyze-in-excel.md).  
  
## Distribuire il modello  
  
#### Per configurare le proprietà di distribuzione  
  
1.  In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], in **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto **Adventure Works Internet Sales Tabular Model** e scegliere **Proprietà** dal menu di scelta rapida.  
  
2.  Nella finestra di dialogo **Deployment Tutorial Property Pages** (Pagine delle proprietà di Deployment Tutorial), in **Server di distribuzione** digitare il nome dell'istanza di Analysis Services in esecuzione in modalità tabulare nella proprietà **Server**. Si tratta dell'istanza in cui verrà distribuito il modello.  
  
    > [!IMPORTANT]  
    > Per eseguire la distribuzione in un'istanza remota di Analysis Services, è necessario disporre delle autorizzazioni di amministratore.  
  
3.  Nella proprietà **Database** digitare **Adventure Works Internet Sales Model**.  
  
4.  Nella proprietà **Nome cubo** digitare **Adventure Works Internet Sales Model**.  
  
5.  Verificare le opzioni selezionate e fare clic su **OK**.  
  
#### Per distribuire il modello tabulare Adventure Works Internet Sales  
  
1.  In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] scegliere **Deploy AW Internet Sales Tabular Model** (Distribuisci AW Internet Sales Tabular Model) dal menu **Compila**.  
  
    Verrà visualizzata la finestra di dialogo Distribuisci in cui sono indicati lo stato della distribuzione e ogni tabella inclusa nel modello.  
  
2. Dopo aver completato la distribuzione, fare clic su **Chiudi**.  
  
## Conclusioni  
Congratulazioni! La procedura di creazione e distribuzione del primo modello tabulare di Analysis Services è stata completata. Tramite questa esercitazione sono state completate le attività più comuni di creazione di un modello tabulare. Ora che il modello Adventure Works Internet Sales è stato distribuito, è possibile utilizzare SQL Server Management Studio per gestire il modello, nonché creare script di processo e un piano di backup. Gli utenti possono connettersi al modello utilizzando un'applicazione client di creazione report, ad esempio Microsoft Excel o [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)].  
  
## Risorse aggiuntive  
Per altre informazioni sulle proprietà dei modelli tabulari che supportano i report [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)], vedere [Proprietà report Power View &#40;SSAS tabulare&#41;](../analysis-services/tabular-models/power-view-reporting-properties-ssas-tabular.md).  
  
## Vedere anche  
[Modalità DirectQuery &#40;SSAS tabulare&#41;](../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)  
[Configurare la modellazione dei dati e le proprietà di distribuzione predefinite &#40;SSAS tabulare&#41;](../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)  
[Database modello tabulare &#40;SSAS tabulare&#41;](../analysis-services/tabular-models/tabular-model-databases-ssas-tabular.md)  
  
  
  

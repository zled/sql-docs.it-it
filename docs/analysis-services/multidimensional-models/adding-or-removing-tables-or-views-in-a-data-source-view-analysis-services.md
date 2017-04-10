---
title: "Aggiunta o rimozione di tabelle o viste in una vista origine dati (Analysis Services) | Microsoft Docs"
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
  - "sql13.asvs.dsvdesigner.tablespane.f1"
helpviewer_keywords: 
  - "eliminazione di tabelle"
  - "tabelle [Analysis Services]"
  - "rimozione di tabelle"
  - "aggiunta di tabelle"
  - "viste origine dati [Analysis Services], tabelle"
  - "tabelle [Analysis Services], viste origine dati"
ms.assetid: 98307d04-6548-4d7d-9244-2371dd165249
caps.latest.revision: 34
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 34
---
# Aggiunta o rimozione di tabelle o viste in una vista origine dati (Analysis Services)
  Dopo aver creato una vista origine dati in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], è possibile modificarla in Progettazione vista origine dati aggiungendo o rimuovendo tabelle e colonne, incluse quelle provenienti da un'altra origine dati.  
  
 Per aprire la vista origine dati in Progettazione vista origine dati, è necessario fare doppio clic sulla vista in Esplora soluzioni. Una volta aperta la vista origine dati, è possibile usare il comando **Aggiungi/Rimuovi tabelle** nella barra dei pulsanti o nel menu per modificare o estendere la vista origine dati. È possibile inoltre utilizzare gli oggetti nel diagramma. Ad esempio, è possibile selezionare un oggetto e utilizzare il tasto CANC sulla tastiera per rimuovere un oggetto.  
  
> [!WARNING]  
>  Prestare attenzione in caso di rimozione di una tabella. Se si rimuove una tabella vengono eliminate anche tutte le colonne e relazioni associate dalla vista origine dati e tutti gli oggetti associati a tale tabella non sono più validi.  
  
## Selezione delle tabelle o delle viste da aggiungere o rimuovere  
 Usando la finestra di dialogo **Aggiungi/Rimuovi tabelle** è possibile spostare tabelle o viste tra gli elenchi **Oggetti disponibili** e **Oggetti inclusi**. Nell'elenco **Oggetti disponibili** vengono incluse inizialmente tutte le tabelle o le viste dell'origine dei dati primaria che non sono già contenute nella vista origine dati. Se l'origine dati primaria supporta la funzione **OPENROWSET**, è anche possibile aggiungere tabelle o viste da altre origini dati nel progetto o nel database.  
  
 Se si aggiunge o si rimuove una tabella dalla vista origine dati, la tabella verrà aggiunta o rimossa anche dal diagramma corrente selezionato nella vista. Per altre informazioni sui diagrammi, vedere [Usare diagrammi in Progettazione vista origine dati &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md).  
  
 Dopo aver spostato una tabella nell'elenco **Oggetti inclusi** della finestra di dialogo **Aggiungi/Rimuovi tabelle**, è possibile aggiungere tutte le tabelle correlate. Questa operazione consente di aggiungere le tabelle nell'origine dei dati in base a vincoli di chiave esterna, se esistono. Se non esistono vincoli di chiave esterna, è possibile usare la proprietà **NameMatchingCriteria** della vista origine dati per determinare le relazioni specificando un criterio di corrispondenza per i nomi delle colonne nelle tabelle al fine di generare le relazioni probabili. Se è specificata la proprietà **NameMatchingCriteria** per la vista origine dati, fare clic su **Aggiungi tabelle correlate** per aggiungere le tabelle dell'origine dati con nomi di colonne corrispondenti. Per altre informazioni sull'impostazione della proprietà **NameMatchingCriteria**, vedere [Viste origine dati in modelli multidimensionali](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md).  
  
> [!NOTE]  
>  L'aggiunta o la rimozione di oggetti in una vista origine dati non influisce sull'origine dati sottostante.  
  
## Vedere anche  
 [Viste origine dati in modelli multidimensionali](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)   
 [Usare diagrammi in Progettazione vista origine dati &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md)  
  
  
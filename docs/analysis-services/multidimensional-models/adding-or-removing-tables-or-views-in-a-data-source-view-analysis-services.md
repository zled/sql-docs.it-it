---
title: Aggiungendo o rimuovendo tabelle o viste in un tipo di dati di origine vista (Analysis Services) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.asvs.dsvdesigner.tablespane.f1
helpviewer_keywords:
- deleting tables
- tables [Analysis Services]
- removing tables
- adding tables
- data source views [Analysis Services], tables
- tables [Analysis Services], data source views
ms.assetid: 98307d04-6548-4d7d-9244-2371dd165249
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2b2f865766530f174cc3affe410679f1880e9813
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services"></a>Aggiunta o rimozione di tabelle o viste in una vista origine dati (Analysis Services)
  Dopo aver creato una vista origine dati in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], è possibile modificarla in Progettazione vista origine dati aggiungendo o rimuovendo tabelle e colonne, incluse quelle provenienti da un'altra origine dati.  
  
 Per aprire la vista origine dati in Progettazione vista origine dati, è necessario fare doppio clic sulla vista in Esplora soluzioni. Una volta aperta la vista origine dati, è possibile usare il comando **Aggiungi/Rimuovi tabelle** nella barra dei pulsanti o nel menu per modificare o estendere la vista origine dati. È possibile inoltre utilizzare gli oggetti nel diagramma. Ad esempio, è possibile selezionare un oggetto e utilizzare il tasto CANC sulla tastiera per rimuovere un oggetto.  
  
> [!WARNING]  
>  Prestare attenzione in caso di rimozione di una tabella. Se si rimuove una tabella vengono eliminate anche tutte le colonne e relazioni associate dalla vista origine dati e tutti gli oggetti associati a tale tabella non sono più validi.  
  
## <a name="selecting-tables-or-views-to-add-or-remove"></a>Selezione delle tabelle o delle viste da aggiungere o rimuovere  
 Usando la finestra di dialogo **Aggiungi/Rimuovi tabelle** è possibile spostare tabelle o viste tra gli elenchi **Oggetti disponibili** e **Oggetti inclusi** . Nell'elenco **Oggetti disponibili** vengono incluse inizialmente tutte le tabelle o le viste dell'origine dei dati primaria che non sono già contenute nella vista origine dati. Se l'origine dati primaria supporta la funzione **OPENROWSET** , è anche possibile aggiungere tabelle o viste da altre origini dati nel progetto o nel database.  
  
 Se si aggiunge o si rimuove una tabella dalla vista origine dati, la tabella verrà aggiunta o rimossa anche dal diagramma corrente selezionato nella vista. Per altre informazioni sui diagrammi, vedere [Usare diagrammi in Progettazione vista origine dati &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md).  
  
 Dopo aver spostato una tabella nell'elenco **Oggetti inclusi** della finestra di dialogo **Aggiungi/Rimuovi tabelle** , è possibile aggiungere tutte le tabelle correlate. Questa operazione consente di aggiungere le tabelle nell'origine dei dati in base a vincoli di chiave esterna, se esistono. Se non esistono vincoli di chiave esterna, è possibile usare la proprietà **NameMatchingCriteria** della vista origine dati per determinare le relazioni specificando un criterio di corrispondenza per i nomi delle colonne nelle tabelle al fine di generare le relazioni probabili. Se è specificata la proprietà **NameMatchingCriteria**per la vista origine dati, fare clic su **Aggiungi tabelle correlate** per aggiungere le tabelle dell'origine dati con nomi di colonne corrispondenti. Per altre informazioni sull'impostazione della proprietà **NameMatchingCriteria** , vedere [Viste origine dati in modelli multidimensionali](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md).  
  
> [!NOTE]  
>  L'aggiunta o la rimozione di oggetti in una vista origine dati non influisce sull'origine dati sottostante.  
  
## <a name="see-also"></a>Vedere anche  
 [Viste origine dati in modelli multidimensionali](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)   
 [Usare diagrammi in Progettazione vista origine dati &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md)  
  
  


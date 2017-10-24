---
title: I database modello multidimensionale (SSAS) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Management Studio [Analysis Services], databases
- SQL Server Analysis Services, databases
- SSAS, databases
- Analysis Services, databases
- databases [Analysis Services], designing
- Business Intelligence Development Studio, databases [Analysis Services]
- databases [Analysis Services]
ms.assetid: 78b2f22a-b7bd-4a2b-b6fc-0bff4d2b3168
caps.latest.revision: 55
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2b9b4fa79c4ef7a37158c1fbeea32a80c56effa2
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="multidimensional-model-databases-ssas"></a>Database modelli multidimensionali (SSAS)
  Un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è una raccolta di origini dati, viste origine dati, cubi, dimensioni e ruoli. Facoltativamente, in un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] possono essere incluse strutture per data mining e assembly personalizzati che consentono di aggiungere funzioni definite dall'utente al database.  
  
 I cubi sono gli oggetti query fondamentali in Analysis Services. Quando si esegue una connessione a un database di Analysis Services tramite un'applicazione client, si esegue in pratica la connessione a un cubo all'interno di tale database. È possibile che in un database siano contenuti più cubi se si riutilizzano dimensioni, assembly, ruoli o strutture di data mining in più contesti.  
  
 È possibile creare e modificare a livello di codice un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] o tramite uno di questi metodi interattivi:  
  
-   Distribuire un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] da [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in un'istanza designata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Con questo processo viene creato un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , se nell'istanza non esiste già un database con lo stesso nome, e viene creata un'istanza degli oggetti designati nel nuovo database creato. Quando si utilizza un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], le modifiche apportate agli oggetti nel progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] diventano effettive solo al momento della distribuzione del progetto in un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
-   Creare un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] vuoto all'interno di un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], quindi connettersi direttamente a tale database mediante [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] e creare oggetti all'interno di esso anziché di un progetto. Quando si utilizza un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in questo modo, le modifiche apportate agli oggetti diventano effettive nel database con cui viene stabilita la connessione al momento del salvataggio dell'oggetto modificato.  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] viene utilizzata l'integrazione con software per il controllo del codice sorgente per supportare più sviluppatori che utilizzano contemporaneamente oggetti diversi all'interno di un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Uno sviluppatore può inoltre interagire direttamente con un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , anziché tramite un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . In questo caso, tuttavia, gli oggetti di un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] potrebbero risultare non sincronizzati con il progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilizzato per la distribuzione. Dopo la distribuzione, un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] viene amministrato mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Mediante [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è inoltre possibile apportare determinate modifiche a un database di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ad esempio a partizioni e ruoli, a causa delle quali gli oggetti di un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] potrebbero risultare non sincronizzati con il progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilizzato per la distribuzione.  
  
## <a name="related-tasks"></a>Attività correlate  
 [Collegamento e scollegamento di database di Analysis Services](../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)  
  
 [Backup e ripristino di database di Analysis Services](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
 [Documentazione e script per un database di Analysis Services](../../analysis-services/multidimensional-models/document-and-script-an-analysis-services-database.md)  
  
 [Modificare o eliminare un database di Analysis Services](../../analysis-services/multidimensional-models/modify-or-delete-an-analysis-services-database.md)  
  
 [Spostare un database di Analysis Services](../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)  
  
 [Rinominare un database multidimensionale &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/rename-a-multidimensional-database-analysis-services.md)  
  
 [Livello di compatibilità di un database multidimensionale &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md)  
  
 [Impostare le proprietà dei database multidimensionali &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/set-multidimensional-database-properties-analysis-services.md)  
  
 [Sincronizzare database di Analysis Services](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md)  
  
 [Passare un database di Analysis Services tra le modalità ReadOnly e ReadWrite](../../analysis-services/multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Connettersi in modalità online a un database di Analysis Services](../../analysis-services/multidimensional-models/connect-in-online-mode-to-an-analysis-services-database.md)   
 [Creare un progetto di Analysis Services &#40;SSDT&#41;](../../analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt.md)   
 [Query su dati multidimensionali con MDX](../../analysis-services/multidimensional-models/mdx/querying-multidimensional-data-with-mdx.md)  
  
  


---
title: Modificare o eliminare un Database di Analysis Services | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
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
- databases [Analysis Services], modifying
- removing databases
- deleting databases
- dropping databases
- databases [Analysis Services], deleting
- modifying databases
ms.assetid: e48e3988-c091-4379-aabc-4da62f709a7e
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 58ba47239da28dfa023bb59a1bbb6ed77e11d425
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="modify-or-delete-an-analysis-services-database"></a>Modificare o eliminare un database di Analysis Services
  È possibile modificare il nome e la descrizione di un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prima della distribuzione in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] e dopo la distribuzione in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. A seconda dell'ambiente di lavoro, è inoltre possibile modificare altre impostazioni di un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
> [!NOTE]  
>  Le proprietà del database tuttavia non possono essere modificate quando [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] è nella modalità online.  
  
## <a name="modifying-databases-using-sql-server-management-studio"></a>Modifica di databases tramite SQL Server Management Studio  
 Dopo la distribuzione di un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] è possibile modificare la modalità di rappresentazione utilizzata da [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] durante la connessione alle origini dei dati contenute nel database. Nella modalità di rappresentazione è possibile specificare il contesto di sicurezza utilizzato da [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] nei tentativi di connessione a un'origine dati a scopo di elaborazione, esplorazione e drill-through.  
  
## <a name="modifying-databases-using-sql-server-data-tools"></a>Modifica di database tramite SQL Server Data Tools  
 È possibile usare [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] nella modalità progetto per modificare le traduzioni della didascalia e della descrizione di un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] usato per definire un database. Per altre informazioni sulle traduzioni in un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , vedere [Scenari di globalizzazione per Analysis Services](../../analysis-services/globalization-scenarios-for-analysis-services.md).  
  
 È inoltre possibile impostare gli alias e le funzioni di aggregazione associate ai tipi di conto utilizzati dagli attributi Conto nelle dimensioni incluse in un database. Gli alias consentono di selezionare la terminologia aziendale specifica utilizzata all'interno di un'organizzazione per i tipi di conto in un grafico dei conti. I tipi di conto vengono utilizzati dai membri di un attributo Conto per indicare la modalità di aggregazione delle misure per ogni membro tramite le funzioni di aggregazione specificate per ogni tipo di conto incluso nel database. Per altre informazioni sugli attributi dell'account, vedere [Attributi e gerarchie di attributi](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md).  
  
## <a name="deleting-databases"></a>eliminazione di database  
 Quando si elimina un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] esistente vengono eliminati anche tutti i cubi, le dimensioni e i modelli di data mining del database. È possibile eliminare solo un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] esistente in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-delete-an-analysis-services-database"></a>Per eliminare un database di Analysis Services  
  
1.  Connettersi a un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
2.  In **Esplora oggetti**espandere il nodo dell'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connessa e verificare che l'oggetto da eliminare sia visibile.  
  
3.  Fare clic con il pulsante destro del mouse sull'oggetto da eliminare e scegliere **Elimina**.  
  
4.  Nella finestra di dialogo **Elimina oggetto** fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Documentazione e script per un database di Analysis Services](../../analysis-services/multidimensional-models/document-and-script-an-analysis-services-database.md)  
  
  


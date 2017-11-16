---
title: Rinominare un Database multidimensionale (Analysis Services) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
helpviewer_keywords:
- renaming databases
ms.assetid: 15fdaec7-f3e4-44d9-9b78-1a1d78c484e0
caps.latest.revision: 20
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3d822aff82a3f38bd4dd8fdec69a87792e8d56a5
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="rename-a-multidimensional-database-analysis-services"></a>Rinominare un database multidimensionale (Analysis Services)
  Il modo in cui il nome di un database di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] viene modificato dipende dalla modalità di connessione al database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Per modificare il nome di un database esistente, è necessario connettersi in modalità online. Per modificare il nome del database in cui verranno create istanze degli oggetti di un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , è necessario connettersi in modalità progetto.  
  
### <a name="to-change-the-database-name-in-online-mode"></a>Per modificare il nome del database in modalità online  
  
1.  Connettersi direttamente al database di [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]utilizzando [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
2.  In Esplora soluzioni fare clic con il pulsante destro del mouse sul database e quindi scegliere **Modifica database**.  
  
3.  Nella casella di testo **Nome database** modificare il nome del database.  
  
4.  Fare clic su **Salva** o **Salva tutto** sulla barra degli strumenti, scegliere **Salva elementi selezionati** o **Salva tutto** dal menu **File** oppure chiudere **Progettazione database** e quindi fare clic su **Salva** quando richiesto.  
  
     Il nome del database verrà aggiornato nell'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e l'oggetto di database verrà aggiornato in Esplora soluzioni.  
  
### <a name="to-change-the-database-name-in-project-mode"></a>Per modificare il nome del database in modalità progetto  
  
1.  Aprire il progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
2.  In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e quindi scegliere **Proprietà**.  
  
3.  Nella finestra di dialogo **Pagine delle proprietà** fare clic su **Distribuzione** nella sezione **Proprietà di configurazione** .  
  
4.  Modificare la proprietà **Database** nel nuovo nome del database.  
  
     La successiva distribuzione del progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] verrà eseguita per questo nuovo nome di database. Se il database esiste già, verrà sovrascritto.  
  
### <a name="to-change-the-database-name-using-sql-server-management-studio"></a>Per modificare il nome del database tramite SQL Server Management Studio  
  
-   Fare clic con il pulsante destro del mouse sul database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e modificare la proprietà Name.  
  
## <a name="see-also"></a>Vedere anche  
 [proprietà server in Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Impostare le proprietà del Database multidimensionale &#40; Analysis Services &#41;](../../analysis-services/multidimensional-models/set-multidimensional-database-properties-analysis-services.md)   
 [Configurare proprietà di progetti di Analysis Services &#40;SSDT&#41;](../../analysis-services/multidimensional-models/configure-analysis-services-project-properties-ssdt.md)   
 [Distribuire progetti di Analysis Services &#40;SSDT&#41;](../../analysis-services/multidimensional-models/deploy-analysis-services-projects-ssdt.md)  
  
  


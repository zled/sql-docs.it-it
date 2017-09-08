---
title: Eliminare un'origine dati in Esplora soluzioni (SSAS multidimensionale) | Documenti Microsoft
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
f1_keywords:
- sql13.asvs.deleteobjects.f1
helpviewer_keywords:
- data sources [Analysis Services], deleting
- deleting data sources
- removing data sources
ms.assetid: b45441ef-f909-4736-98b9-cc80d0acac99
caps.latest.revision: 46
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 67b093b4d4af59139dcd32401f177724823b5926
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="delete-a-data-source-in-solution-explorer-ssas-multidimensional"></a>Eliminare un'origine dati in Esplora soluzioni (SSAS multidimensionale)
  È possibile eliminare un oggetto origine dati per rimuoverlo definitivamente da un progetto di modello multidimensionale di Analysis Services.  
  
 In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]le origini dati costituiscono la base sulla quale vengono costruite le viste origine dati e queste ultime vengono a propria volta utilizzate per definire dimensioni, cubi e strutture di data mining in un database o un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Di conseguenza, l'eliminazione di un'origine dei dati può invalidare altri oggetti di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Prima di eliminare l'oggetto, si consiglia di verificare sempre l'elenco degli oggetti dipendenti fornito.  
  
> [!IMPORTANT]  
>  Non è possibile eliminare origini dati da cui dipendono altri oggetti da un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] aperto da [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in modalità online. Prima di eliminare l'origine dati, è necessario eliminare tutti gli oggetti del database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] che dipendono da tale origine dati. Per altre informazioni sulla modalità online, vedere [Connect in Online Mode to an Analysis Services Database](../../analysis-services/multidimensional-models/connect-in-online-mode-to-an-analysis-services-database.md).  
  
### <a name="to-delete-a-data-source"></a>Per eliminare un'origine dati  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aprire il progetto o connettersi al database da cui si desidera eliminare un'origine dati.  
  
2.  In **Esplora soluzioni**espandere la cartella **Origini dati** .  
  
3.  Fare clic con il pulsante destro del mouse sull'origine dati, quindi scegliere **Elimina**. Viene visualizzata la finestra di dialogo **Elimina oggetti**  in cui sono riportati gli oggetti che saranno invalidati in caso di eliminazione dell'origine dati. Esaminare attentamente l'elenco prima di fare clic su **OK** per eliminare l'origine dati.  
  
4.  Salvare il progetto.  
  
     Dopo l'eliminazione di un'origine dati da un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , è necessario salvare il progetto modificato. In caso contrario, alla successiva apertura del progetto verrà visualizzato un errore poiché il file XML sottostante per l'origine dati eliminata risulta mancante quando il progetto tenta di caricare tale origine dati.  
  
## <a name="see-also"></a>Vedere anche  
 [Origini dati nei modelli multidimensionali](../../analysis-services/multidimensional-models/data-sources-in-multidimensional-models.md)   
 [Origini dati supportate &#40;SSAS - multidimensionale&#41;](../../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md)  
  
  

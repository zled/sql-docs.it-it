---
title: Creazione di un'analisi di progetto (esercitazione di base di Data Mining) di servizi | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 784c0401-0358-4117-9c85-4e8220ce71d9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e3c88894ee271e9b96e98e25dc14e62bfc0361ca
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048331"
---
# <a name="creating-an-analysis-services-project-basic-data-mining-tutorial"></a>Creazione di un progetto di Analysis Services (Esercitazione di base sul data mining)
  Ciascuna [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] progetto definisce gli oggetti in una singola [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database. Un database di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] può contenere molti tipi diversi di oggetti  
  
-   Modelli multidimensionali (cubi)  
  
-   Strutture e modelli di data mining  
  
-   Supporto di oggetti quali origini dati, viste origine dati e assembly personalizzati  
  
 Si noti che il processo di data mining **non** richiede l'uso di un cubo. Se è necessario eseguire il data mining in un cubo esistente, occorre aggiungere i modelli di data mining nello stesso progetto usato per compilare il cubo. Per la maggior parte delle operazioni è tuttavia possibile compilare i modelli in origini dati relazionali, ad esempio un data warehouse, evitando così l'uso di un cubo che comporta una riduzione delle prestazioni.  
  
 In questa esercitazione si userà un data warehouse relazionale, [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)], come origine dati. Si distribuirà tutti gli oggetti di data mining di dati a un [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database denominato `BasicDataMining`, usato esclusivamente per il data mining.  
  
 Per impostazione predefinita [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] utilizza le **localhost** istanza per i nuovi progetti. Se si usa un'istanza denominata o un server diverso, è necessario creare e aprire il progetto prima di modificare il nome dell'istanza.  
  
 Per altre informazioni sulle [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] progetti, vedere [creazione di un progetto di Analysis Services](../analysis-services/lesson-1-1-creating-an-analysis-services-project.md).  
  
### <a name="to-create-an-analysis-services-project"></a>Per creare un progetto di Analysis Services  
  
1.  Aprire [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
2.  Scegliere **Nuovo** dal menu **File**e quindi selezionare **Progetto**.  
  
3.  Verificare che **Progetti Business Intelligence** sia selezionato nel riquadro **Tipi progetto** .  
  
4.  Nel riquadro **Modelli** selezionare **Progetto multidimensionale e di data mining di Analysis Services**.  
  
5.  Nel **Name** casella, denominare il nuovo progetto `BasicDataMining`.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-change-the-instance-where-data-mining-objects-are-stored"></a>Per modificare l'istanza in cui vengono archiviati gli oggetti di data mining  
  
1.  Nella [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]via il **Project** dal menu **proprietà**.  
  
2.  Sul lato sinistro del riquadro **Pagine delle proprietà** fare clic su **Distribuzione**in **Proprietà di configurazione**.  
  
3.  Sul lato destro del riquadro **Pagine delle proprietà** , verificare in **Destinazione**che il nome del **Server** sia **localhost**. Se si utilizza un'altra istanza, digitarne il nome. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Creazione di un'origine dati &#40;esercitazione di base di Data Mining&#41;](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Compilare progetti di Analysis Services &#40;SSDT&#41;](../analysis-services/multidimensional-models/build-analysis-services-projects-ssdt.md)   
 [Creare un progetto di Analysis Services &#40;SSDT&#41;](../analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt.md)  
  
  

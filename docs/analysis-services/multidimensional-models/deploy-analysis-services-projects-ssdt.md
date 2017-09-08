---
title: Distribuire progetti di Analysis Services (SSDT) | Documenti Microsoft
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
- deploy [Analysis Services]
- projects [Analysis Services], deploying
- Business Intelligence Development Studio, deploying projects [Analysis Services]
ms.assetid: 29490a5b-1573-4a35-9277-10c6a6e4ef0e
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8d115e6a40d8954641d0cfc39636748de15636cf
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="deploy-analysis-services-projects-ssdt"></a>Distribuire progetti di Analysis Services (SSDT)
  Durante lo sviluppo di un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], si distribuisce frequentemente il progetto su un server di sviluppo per creare il database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] definito dal progetto. Ciò è necessario per testare il progetto, ad esempio per esplorare le celle nel cubo o i membri della dimensione oppure per verificare le formule per gli indicatori di prestazioni chiave (KPI).  
  
## <a name="deploying-a-project"></a>Distribuzione di un progetto  
 È possibile distribuire un progetto in modo indipendente oppure distribuire tutti i progetti all'interno della soluzione. Quando si distribuisce un progetto, vengono eseguite diverse operazioni in sequenza. Viene innanzitutto compilato il progetto. In questo passaggio vengono creati i file di output che definiscono il database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e gli oggetti da cui è costituito. Viene quindi convalidato il server di destinazione e infine vengono creati il database di destinazione e i relativi oggetti sul server di destinazione. Durante la distribuzione, qualsiasi database preesistente viene completamente sostituito dal motore di distribuzione con il contenuto del progetto, a meno che gli oggetti non siano stati creati dal progetto durante una distribuzione precedente.  
  
 Dopo una distribuzione iniziale, viene generato un file IncrementalSnapshot.xml nella \<nome progetto > \obj cartella. Tale file consente di determinare se il database o gli oggetti sul server di destinazione sono stati modificati all'esterno del progetto. In tal caso, verrà richiesto di sovrascrivere tutti gli oggetti nel database di destinazione. Se tutte le modifiche sono state apportate all'interno del progetto e il progetto è configurato per la distribuzione incrementale, sul server di destinazione verranno distribuite soltanto le modifiche.  
  
 La configurazione di progetto e le impostazioni associate determinano le proprietà di distribuzione che verranno utilizzate per distribuire il progetto. Per un progetto condiviso, ogni sviluppatore può utilizzare la propria configurazione con specifiche opzioni di configurazione del progetto. Ogni sviluppatore può ad esempio specificare un diverso server di prova per mantenere l'isolamento rispetto agli altri sviluppatori.  
  
## <a name="see-also"></a>Vedere anche  
 [Creare un progetto di Analysis Services &#40;SSDT&#41;](../../analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt.md)  
  
  

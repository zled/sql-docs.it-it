---
title: Modificare l'origine di una partizione per l'utilizzo di una tabella dei fatti diverse | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fact tables [Analysis Services]
- partitions [Analysis Services], fact tables
ms.assetid: 5508312f-8e46-4802-9362-6688ca03d098
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a1094f1f32b7f15c70a395d810a542a35cf02a74
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="change-a-partition-source-to-use-a-different-fact-table"></a>Modificare l'origine di una partizione in modo da utilizzare una tabella dei fatti diversa
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Quando si crea una partizione per un cubo, è possibile scegliere di utilizzare una tabella dei fatti diverse. Le tabelle diverse possono derivare da una singola vista origine dati, da più viste origine dati diverse o da origini dei dati diverse. Una vista origine dati può inoltre contenere tabelle diverse derivate da più origini dei dati.  
  
 Tutte le tabelle dei fatti e le dimensioni delle partizioni di un cubo devono avere la stessa struttura della tabella dei fatti e delle dimensioni del cubo. Ad esempio, tabelle dei fatti diverse possono avere la stessa struttura ma contenere dati relativi a linee di prodotto o anni diversi.  
  
 È possibile specificare una tabella dei fatti nella pagina **Impostazione informazioni origine** della Creazione guidata partizione. In questa pagina, nel gruppo Origine partizione accanto a **Cerca in**specificare un'origine dei dati o una vista origine dati in cui eseguire la ricerca. Successivamente, fare clic su **Trova tabelle**e quindi selezionare la tabella da usare in **Tabelle disponibili**.  
  
 Se si utilizzano tabelle dei fatti diverse, verificare che non esistano dati duplicati nelle partizioni. Se ad esempio una tabella dei fatti contiene solo le transazioni relative al 2012 e un'altra tabella dei fatti solo quelle relative al 2013, i dati delle due tabelle saranno indipendenti. Analogamente, le tabelle dei fatti relative a linee di prodotti diverse o ad aree geografiche distinte sono indipendenti.  
  
 È possibile, ma non consigliabile, utilizzare tabelle dei fatti diverse contenenti dati duplicati. In questo caso, è necessario applicare filtri alle partizioni per garantire che i dati utilizzati da una partizione non vengano utilizzati dalle altre. Per altre informazioni, vedere [Creare e gestire una partizione locale &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/create-and-manage-a-local-partition-analysis-services.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Creare e gestire una partizione locale &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/create-and-manage-a-local-partition-analysis-services.md)  
  
  

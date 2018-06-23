---
title: Selezione dimensione cubo di origine (Creazione guidata Data Mining) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dm.dmwizard.selectsourcecube.f1
ms.assetid: 556e216b-5e21-4160-967d-4c57591fbab4
caps.latest.revision: 26
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ddd4affa954cf080cec3ad1ca37df82d494221e6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36054379"
---
# <a name="select-the-source-cube-dimension-data-mining-wizard"></a>Selezione dimensione cubo di origine (Creazione guidata modello di data mining)
  Usare la pagina **Selezione dimensione cubo di origine** per selezionare la dimensione del cubo contenente i case da analizzare. Se, ad esempio, si compila un modello che analizza il comportamento di acquisto dei clienti in base ai dati demografici, è necessario selezionare la dimensione Customer che in genere contiene un record univoco per ogni cliente e vari attributi che rappresentano i dati demografici, ad esempio sesso, ubicazione o reddito. Più avanti nella procedura guidata si potrà aggiungere una tabella correlata a questa tabella del case, ad esempio una tabella nidificata in cui sono elencati i prodotti acquistati dal cliente.  
  
> [!NOTE]  
>  Questa pagina viene visualizzata solo se è stata selezionata l'opzione **Da cubo esistente** nella pagina **Selezione metodo di definizione** della procedura guidata.  
  
## <a name="options"></a>Opzioni  
 **Selezionare una dimensione cubo di origine**  
 Consente di selezionare la dimensione del cubo da cui verranno recuperati i dati dell'origine per la struttura di data mining.  
  
## <a name="choosing-a-dimension"></a>Scelta di una dimensione  
 Poiché è possibile selezionare una sola dimensione da utilizzare nel modello, è importante comprendere la struttura del cubo e selezionare la dimensione che fornisce le informazioni più appropriate per il modello. In caso di dubbi sulla dimensione da utilizzare, potrebbe essere utile esplorare il cubo ed esaminare i campi e i dati delle dimensioni utilizzando Progettazione dimensioni. Per altre informazioni, vedere [Esplorare i dati di una dimensione in Progettazione dimensioni](multidimensional-models/database-dimensions-browse-dimension-data-in-dimension-designer.md).  
  
 Se non si ha familiarità con le dimensioni in generale, vedere [Introduzione alle dimensioni &#40;Analysis Services - Dati multidimensionali&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md).  
  
 Per altre informazioni sul tipo di informazioni generalmente contenute in una singola dimensione, inclusi gli attributi e le misure che potrebbero essere utili per il data mining, vedere [Relazioni tra dimensioni](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).  
  
 Se la dimensione scelta non contiene tutti gli attributi correlati richiesti per la compilazione del modello di data mining, potrebbe essere necessario modificarla. Per altre informazioni, vedere [Definire le dimensioni del database](multidimensional-models/define-database-dimensions.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Data Mining della Guida F1 di procedura guidata &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md)   
 [Creare la struttura di Data Mining &#40;Creazione guidata di Data Mining&#41;](create-the-data-mining-structure-data-mining-wizard.md)   
 [Selezionare la chiave del Case &#40;Creazione guidata di Data Mining&#41;](select-the-case-key-data-mining-wizard.md)  
  
  
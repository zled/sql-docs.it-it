---
title: Creazione di una struttura di previsione e un modello (esercitazione intermedia di Data Mining) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5f55cbf6-0db4-4cb4-a0f5-e27441873d4f
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 47d6e75a691c53fe1658fb5f79ee2bde8e9c2d01
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312269"
---
# <a name="creating-a-forecasting-structure-and-model-intermediate-data-mining-tutorial"></a>Creazione di una struttura e di un modello di previsione (Esercitazione intermedia sul data mining)
  Verrà ora utilizzata la Creazione guidata modello di data mining per creare una nuova struttura di data mining e un nuovo modello di data mining basati sulla vista origine dati appena creata. In questa attività si specificherà che il modello di data mining deve utilizzare l'algoritmo [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series.  
  
### <a name="to-create-a-forecasting-mining-structure"></a>Per creare una struttura di data mining per la previsione  
  
1.  In Esplora soluzioni [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], fare doppio clic su **strutture di Data Mining** e selezionare **nuova struttura di Data Mining**.  
  
2.  Nella pagina iniziale **Creazione guidata modello di data mining** fare clic su **Avanti**.  
  
3.  Nel **Selezione metodo di definizione** verificare che **da esistente database relazionale o data warehouse** sia selezionata e quindi fare clic su **Avanti**.  
  
4.  Nel **Crea struttura di Data Mining** nella pagina **tecnica di data mining si desidera utilizzare?**, selezionare **Microsoft Time Series**, quindi fare clic su  **Avanti**.  
  
5.  Nel **selezione vista origine dati** nella pagina **viste origine dati disponibili**, selezionare **SalesByRegion**.  
  
6.  Scegliere **Avanti**.  
  
7.  Nel **impostazione tipi di tabelle** pagina, assicurarsi che la casella di controllo nel **Case** colonna per la tabella vTimeSeries sia selezionata e quindi fare clic su **Avanti**.  
  
8.  Nel **specificano i dati di Training** pagina, selezionare le caselle di controllo nel **chiave** colonna per le colonne ModelRegion e ReportingDate.  
  
     La colonna ReportingDate dovrebbe essere selezionata per impostazione predefinita, poiché è stata specificata come chiave primaria logica quando è stata creata la vista origine dati. Aggiungendo ModelRegion come seconda chiave, si indica all'algoritmo di creare una serie temporale distinta per ogni combinazione di modello e area geografica elencata in questo campo.  
  
9. Selezionare le caselle di controllo nel **Input** e **stimabile** le colonne per la quantità, colonna e quindi fare clic su **Avanti**.  
  
     Se si seleziona **stimabile**, si indica che si desidera creare previsioni sui dati in questa colonna. Tuttavia, poiché si desidera basare le previsioni sui dati passati, è inoltre necessario aggiungere la colonna come input.  
  
10. Nella pagina **di specificare le colonne tipo di contenuto e dati**, rivedere le selezioni.  
  
     La colonna ModelRegion viene definita come un **chiave** colonna e la colonna ReportingDate viene definita automaticamente come un **Key Time** colonna. È consentito un solo tipo per ogni tipo di chiave.  
  
11. Scegliere **Avanti**.  
  
12. Nel **Completamento procedura guidata** pagina per **nome struttura di Data Mining**, tipo `Forecasting`.  
  
    > [!NOTE]  
    >  L'opzione di drill-through non è disponibile per i modelli Time Series.  
  
13. In **nome del modello di Data Mining**, tipo `Forecasting`, quindi fare clic su **fine**.  
  
     Verrà aperto Progettazione modelli di Data Mining per visualizzare il `Forecasting` struttura di data mining appena creato.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Modifica della struttura di previsione &#40;intermedi dell'esercitazione sul Data Mining&#41;](../../2014/tutorials/modifying-the-forecasting-structure-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Progettazione di Data Mining](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [Algoritmo Microsoft Time Series](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
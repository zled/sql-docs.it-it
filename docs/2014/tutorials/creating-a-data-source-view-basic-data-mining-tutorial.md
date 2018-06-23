---
title: Creazione di un tipo di dati di origine vista (esercitazione di base di Data Mining) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1e68a88-0f82-415d-becc-78d180d4f845
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 37c1548820bfe40478cdd5a8fd7b7ed051722056
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/21/2018
ms.locfileid: "36311849"
---
# <a name="creating-a-data-source-view-basic-data-mining-tutorial"></a>Creazione di una vista origine dati (Esercitazione di base sul data mining)
  Una vista origine dati si basa su un'origine dati e definisce un subset dei dati che è possibile utilizzare nelle strutture di data mining. È inoltre possibile utilizzare la vista origine dati per aggiungere colonne, creare aggregazioni e colonne calcolate nonché aggiungere viste denominate. Le viste origine dati consentono di selezionare i dati correlati al progetto, stabilire relazioni tra tabelle e modificare la struttura dei dati senza modificare l'origine dati originale. Per altre informazioni, vedere [Viste origine dati in modelli multidimensionali](../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md).  
  
### <a name="to-create-a-data-source-view"></a>Per creare una vista origine dati  
  
1.  In **Esplora soluzioni**, fare doppio clic su **viste origine dati**e selezionare **nuova vista origine dati**.  
  
2.  Nella pagina iniziale di **Creazione guidata vista origine dati** fare clic su **Avanti**.  
  
3.  Nel **selezionare un'origine dati** nella pagina **origini dati relazionali**, selezionare l'origine dati Adventure Works DW 2012 creata nell'ultima attività. Scegliere **Avanti**.  
  
    > [!NOTE]  
    >  Se si desidera creare un'origine dati, fare doppio clic su **origini** e quindi fare clic su **nuova origine dati** per avviare la creazione guidata origine dati.  
  
4.  Nel **selezione tabelle e viste** pagina, selezionare gli oggetti seguenti e quindi fare clic sulla freccia a destra per includerli nella nuova vista origine dati:  
  
    -   **ProspectiveBuyer (dbo)** -tabella di potenziali acquirenti di biciclette  
  
    -   **vTargetMail (dbo)** -visualizzazione dei dati cronologici relativi precedenti acquirenti di biciclette  
  
5.  Scegliere **Avanti**.  
  
6.  Nel **Completamento procedura guidata** pagina, per impostazione predefinita la vista origine dati è denominata Adventure Works DW 2012. Modificare il nome in `Targeted Mailing`, quindi fare clic su **fine**.  
  
     La nuova vista origine dati viene aperto nel **destinazione DSV [Progettazione]** scheda.  
  
## <a name="previous-task-in-lesson"></a>Attività precedente della lezione  
 [Creazione di un'origine dati &#40;esercitazione di base di Data Mining&#41;](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>Lezione successiva  
 [Lezione 2: Compilazione di una struttura di Mailing diretto &#40;esercitazione di base di Data Mining&#41;](../../2014/tutorials/lesson-2-building-a-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Definizione di un tipo di dati della vista origine &#40;Analysis Services&#41;](../analysis-services/multidimensional-models/defining-a-data-source-view-analysis-services.md)  
  
  
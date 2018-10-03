---
title: Eliminare un filtro da un modello di Data Mining | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- filters [Analysis Services]
ms.assetid: 91220b21-adbc-49a9-b200-8bf0a724eff1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 02bf9026d14f759b5e5931b132faae3ee0fec1a2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48082941"
---
# <a name="delete-a-filter-from-a-mining-model"></a>Eliminare un filtro da un modello di data mining
  Quando si crea un filtro in un modello di data mining, è possibile creare modelli in un subset dei dati nella vista origine dati. I filtri sono anche utili per il test dell'accuratezza del modello su un subset dei dati originali.  
  
 Tuttavia, è necessario eliminare il filtro se si desidera visualizzare nuovamente il set completo dei case. In questa procedura viene descritto come rimuovere le condizioni su un filtro o eliminare completamente il filtro.  
  
### <a name="to-delete-a-condition-from-a-filter-on-a-mining-model"></a>Per eliminare una condizione da un filtro su un modello di data mining  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in Esplora soluzioni, fare clic sulla struttura di data mining che contiene il modello di data mining da filtrare.  
  
2.  Fare clic sulla scheda **Modelli di data mining** .  
  
3.  Selezionare il modello, quindi fare clic con il pulsante destro del mouse per aprire il menu di scelta rapida.  
  
     -oppure-  
  
     Selezionare il modello. Scegliere **Imposta filtro modello** dal menu **Modello di data mining**.  
  
4.  Nella finestra di dialogo **Filtro modello** fare clic con il pulsante destro del mouse sulla riga della griglia che contiene la condizione da eliminare.  
  
5.  Selezionare **Elimina**.  
  
### <a name="to-clear-the-filter-on-a-mining-model-in-the-filter-editor-dialog-box"></a>Per cancellare il filtro su un modello di data mining nella finestra di dialogo Editor filtri  
  
-   Nella finestra di dialogo **Editor filtri** fare clic con il pulsante destro del mouse su una riga della griglia e quindi scegliere **Elimina tutto**.  
  
## <a name="working-with-model-filters-using-the-properties-window"></a>Utilizzo dei filtri di modelli con la finestra Proprietà  
 Se si desidera eliminare l'intero filtro, non è necessario aprire le finestre di dialogo Editor filtri. Le condizioni di filtro creata sono disponibili nel `Filter` proprietà del modello di data mining.  
  
> [!NOTE]  
>  È possibile visualizzare le proprietà di un modello di data mining in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ma non in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-clear-the-filter-on-a-mining-model-in-solution-explorer"></a>Per cancellare il filtro su un modello di data mining in Esplora soluzioni  
  
1.  In Esplora soluzioni fare clic sul modello di data mining che contiene il filtro.  
  
2.  Nel **delle proprietà** finestra, fare clic sul testo del filtro nella `Filter` proprietà e selezionare **Seleziona tutto**.  
  
3.  Premere il tasto BACKSPACE o CANC.  
  
## <a name="see-also"></a>Vedere anche  
 [Il drill-Through nei dati del Case da un modello di Data Mining](drill-through-to-case-data-from-a-mining-model.md)   
 [Procedure dettagliate e le attività del modello di data mining](mining-model-tasks-and-how-tos.md)   
 [Filtri per i modelli di Data Mining &#40;Analysis Services - Data Mining&#41;](mining-models-analysis-services-data-mining.md)  
  
  

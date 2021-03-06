---
title: Livello e membri (scheda esplorazione, progettazione dimensioni) (Analysis Services - dati multidimensionali) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.browsertab.levelsandmembers.f1
ms.assetid: 3f61e384-5b4e-4480-a7ed-b408de2fdea7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9a737b79944635af1a45dd4fc51a9ef2e2967a31
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48209703"
---
# <a name="level-and-members-browser-tab-dimension-designer-analysis-services---multidimensional-data"></a>Livello e membri (scheda Esplorazione, Progettazione dimensioni) (Analysis Services – Dati multidimensionali)
  Utilizzare questo riquadro per visualizzare i membri della gerarchia e della lingua attualmente selezionate. Per selezionare una gerarchia o una lingua da visualizzare, utilizzare le opzioni **Gerarchia** e **Lingua** nel riquadro **Barra degli strumenti** . Per altre informazioni sul riquadro Barra degli strumenti, vedere [Toolbar &#40;Browser Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-browser-tab-dimension-designer-analysis-services-multidimensional-data.md).  
  
## <a name="writeback-mode"></a>Modalità writeback  
 La funzionalità di questo riquadro cambia se la modalità writeback è abilitata. La dimensione selezionata deve essere abilitata per la scrittura (in altre parole, il `WriteEnabled` della dimensione deve essere impostata su true) e la dimensione deve essere distribuita a un [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] istanza per poter abilitare la modalità writeback.  
  
 Per abilitare la modalità di writeback, puoi selezionare **Writeback** dal riquadro **Toolbar**, oppure fare clic con il pulsante destro del mouse sul riquadro **Level e Members** e selezionare **Writeback** dal menu di scelta rapida.  
  
 Se la modalità writeback è abilitata è possibile eseguire le azioni aggiuntive seguenti nel riquadro dei **livelli e dei membri** :  
  
|Per|Attività svolte|  
|-----------|-------------|  
|Creare membri di pari livello e membri figlio nella gerarchia selezionata.|Fare clic con il pulsante destro del mouse sul membro selezionato e scegliere **Crea elemento di pari livello**, per creare un membro di pari livello, o **Crea elemento figlio**, per creare un membro figlio, dal menu di scelta rapida.|  
|Spostare un membro selezionato a un livello superiore o inferiore della gerarchia.|Trascinare il membro selezionato sul membro padre o figlio corretto, oppure fare clic su **Aumenta rientro** o su **Riduci rientro** nel riquadro **Barra degli strumenti** per spostare il membro selezionato a un livello superiore o inferiore della gerarchia.|  
|Rinominare un membro selezionato.|Fare clic con il pulsante destro del mouse sul membro selezionato e scegliere **Rinomina**. In alternativa, fare clic su un membro già selezionato.|  
|Modificare i valori delle proprietà dei membri.|Fare doppio clic sul valore della proprietà selezionata del membro selezionato per modificare tale valore.|  
  
## <a name="options"></a>Opzioni  
 **Livello corrente**  
 Consente di visualizzare il livello a cui appartiene il membro attualmente selezionato in **Albero** .  
  
 **Struttura ad albero**  
 Consente di visualizzare i membri della gerarchia e della lingua attualmente selezionate.  
  
 Se le proprietà membro vengono selezionate dall'opzione **Proprietà membro** del riquadro Barra degli strumenti, ogni proprietà membro viene visualizzata come colonna.  
  
 Se la modalità writeback è abilitata, viene visualizzata una colonna per ogni colonna chiave associata all'attributo chiave nella dimensione.  
  
## <a name="context-menu"></a>Menu di scelta rapida  
 Le opzioni seguenti sono disponibili nel menu di scelta rapida visualizzato facendo clic con il pulsante destro del mouse su qualsiasi parte del riquadro dei **livelli e dei membri** per il membro selezionato:  
  
 **Crea elemento di pari livello**  
 Consente di creare un nuovo membro allo stesso livello del membro selezionato.  
  
> [!NOTE]  
>  Questa opzione è disponibile solo se è selezionato un membro a un livello diverso dal livello Totale.  
  
> [!NOTE]  
>  Questa opzione viene visualizzata solo se è abilitata la modalità writeback.  
  
 **Creare figlio**  
 Consente di creare un nuovo membro al livello immediatamente inferiore a quello del membro selezionato, come elemento figlio del membro selezionato.  
  
> [!NOTE]  
>  Questa opzione è disponibile solo se è selezionato un membro a un livello diverso da quello più basso.  
  
> [!NOTE]  
>  Questa opzione viene visualizzata solo se è abilitata la modalità writeback.  
  
 **Taglia**  
 Consente di copiare i membri selezionati negli Appunti e di rimuoverli dalla gerarchia.  
  
> [!NOTE]  
>  Questa opzione è disponibile solo se è selezionato un membro diverso dal membro Totale.  
  
> [!NOTE]  
>  Questa opzione viene visualizzata solo se è abilitata la modalità writeback.  
  
 **Incolla**  
 Consente di incollare i membri precedentemente rimossi usando **Taglia** immediatamente dopo il membro selezionato.  
  
> [!NOTE]  
>  Questa opzione viene visualizzata solo se è abilitata la modalità writeback.  
  
 **Elimina**  
 Consente di rimuovere i membri selezionati dalla gerarchia.  
  
> [!NOTE]  
>  Questa opzione è disponibile solo se è selezionato un membro diverso dal membro Totale.  
  
> [!NOTE]  
>  Questa opzione viene visualizzata solo se è abilitata la modalità writeback.  
  
 **Rinominare**  
 Selezionare questa opzione per modificare il nome del membro selezionato.  
  
> [!NOTE]  
>  Questa opzione è disponibile solo se è selezionato un membro diverso dal membro Totale.  
  
> [!NOTE]  
>  Questa opzione viene visualizzata solo se è abilitata la modalità writeback.  
  
 **Filtra membri**  
 Visualizza la finestra di dialogo **Membri filtro** per filtrare i membri visualizzati in **Livello e Membri** per la gerarchia selezionata. Per altre informazioni sulla finestra di dialogo **Filtra membri** vedere [Finestra di dialogo Filtra membri &#40;Analysis Services - Dati multidimensionali&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md).  
  
 **Espandi tutto**  
 Consente di espandere tutti i membri contenuti in **Albero**.  
  
> [!NOTE]  
>  Questa opzione è disponibile solo se è selezionato un membro a un livello diverso da quello più basso.  
  
 **Comprimi tutto**  
 Consente di comprimere tutti i membri contenuti in **Albero**.  
  
 **Espandi membro**  
 Consente di espandere il membro selezionato in **Albero**.  
  
 **Comprimi membro**  
 Consente di comprimere il membro selezionato in **Albero**.  
  
 **Writeback**  
 Selezionare questa opzione per abilitare la modalità writeback.  
  
## <a name="see-also"></a>Vedere anche  
 [Sulla barra degli strumenti &#40;scheda esplorazione, progettazione dimensioni&#41; &#40;Analysis Services - dati multidimensionali&#41;](toolbar-browser-tab-dimension-designer-analysis-services-multidimensional-data.md)   
 [Browser &#40;progettazione dimensioni&#41; &#40;Analysis Services - dati multidimensionali&#41;](browser-dimension-designer-analysis-services-multidimensional-data.md)  
  
  

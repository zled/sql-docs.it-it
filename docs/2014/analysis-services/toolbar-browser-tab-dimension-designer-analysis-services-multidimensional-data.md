---
title: Sulla barra degli strumenti (scheda esplorazione, progettazione dimensioni) (Analysis Services - dati multidimensionali) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d0abb2a7-e981-4b0a-a442-80c819aca2ae
caps.latest.revision: 19
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cb561ed65f629879f48aa8c47cf470dfecedff74
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37192379"
---
# <a name="toolbar-browser-tab-dimension-designer-analysis-services---multidimensional-data"></a>Barra degli strumenti (scheda Esplorazione, Progettazione dimensioni) (Analysis Services – Dati multidimensionali)
  Il riquadro **Barra degli strumenti** consente di eseguire operazioni comuni nella scheda **Esplorazione** di **Progettazione dimensioni**.  
  
## <a name="options"></a>Opzioni  
 **Process**  
 Fare clic su questo pulsante per aprire la finestra di dialogo **Elabora** ed elaborare la dimensione selezionata.  
  
 **Ristabilire la connessione**  
 Fare clic su questo pulsante per riconnettere la scheda **Esplorazione** all'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] e al database contenente la dimensione, se la sessione della scheda **Esplorazione** viene disconnessa a causa dell'interruzione o del timeout della connessione.  
  
 **Aggiorna**  
 Fare clic su questo pulsante per ricaricare i dati e i metadati delle dimensioni nella scheda **Esplorazione** .  
  
 **Proprietà dei membri**  
 Fare clic su questo pulsante per visualizzare e selezionare le proprietà membro da mostrare nel riquadro **Level and Members** (Livello e membri). Se si seleziona **(Mostra tutto)** , vengono visualizzate tutte le proprietà membro elencate.  
  
 Ogni proprietà membro selezionata in **Proprietà membro** viene visualizzata in una colonna separata all'interno del riquadro **Level and Members** (Livello e membri) per consentire la modifica dei valori della proprietà membro in modalità writeback.  
  
 **Filtra membri**  
 Fare clic su questo pulsante per visualizzare la finestra di dialogo **Filtra membri** e filtrare i membri riportati nel riquadro **Level and Members** (Livelli e membri) per la gerarchia selezionata.  
  
 **Writeback**  
 Selezionare questo pulsante per impostare il riquadro **Level and Members** (Livello e membri) in modalità di writeback della dimensione.  
  
 **Riduci rientro**  
 Fare clic su questo pulsante per trasformare il membro selezionato nel riquadro **Level and Members** (Livello e membri) in un elemento di pari livello del relativo membro padre.  
  
> [!NOTE]  
>  Questa opzione viene abilitata solo se è abilitata la modalità writeback.  
  
 **Aumenta rientro**  
 Fare clic su questo pulsante per trasformare il membro selezionato nel riquadro **Level and Members** (Livello e membri) in un membro figlio dell'elemento di pari livello che precede il membro selezionato.  
  
> [!NOTE]  
>  Questa opzione viene abilitata solo se è abilitata la modalità writeback.  
  
 **Hierarchy**  
 Consente di selezionare la gerarchia da cui visualizzare i membri nel riquadro **Level and Members** (Livello e membri).  
  
 **Lingua**  
 Consente di selezionare la lingua usata per visualizzare i membri nel riquadro **Level and Members** (Livello e membri).  
  
 Se per la lingua selezionata non è stata definita una traduzione, viene usata la lingua predefinita per visualizzare i membri nel riquadro **Level and Members** (Livello e membri). In tal caso la modalità writeback risulterà disabilitata.  
  
  

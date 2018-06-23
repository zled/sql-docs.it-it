---
title: Analizza in Excel (scheda esplorazione, Progettazione cubi) (Analysis Services - dati multidimensionali) | Documenti Microsoft
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
- sql12.asvs.cubeeditor.browsecube.datapane.f1
- sql12.asvs.ssms.analyzeinexcel.f1
ms.assetid: 890ed457-137e-44ac-9b2c-83344a1b8fc9
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: b6e20d95fc7d1a097f50eb5cca4937cc62580ef3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156394"
---
# <a name="analyze-in-excel-browser-tab-cube-designer-analysis-services---multidimensional-data"></a>Analizza in Excel (scheda Esplorazione, Progettazione cubi) (Analysis Services - Dati multidimensionali)
  La funzionalità**Analizza in Excel** offre allo sviluppatore del cubo un modo per verificare rapidamente come apparirebbe un progetto all'utente finale. La funzionalità **Analizza in Excel** consente di aprire Microsoft Excel, creare una connessione origine dati al database dell'area di lavoro modello e di aggiungere automaticamente una tabella pivot al foglio di lavoro. Questa funzionalità sostituisce il controllo Web di Office che nelle versioni precedenti forniva una tabella pivot incorporata nella scheda Esplorazione.  
  
 **Per visualizzare i dati del cubo:**  
  
1.  In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], fare doppio clic su un cubo in Esplora soluzioni per aprirlo in Progettazione cubi.  
  
2.  Fare clic sulla scheda **Esplorazione** .  
  
3.  Per convalidare la connessione, fare clic su **Riconnetti** .  
  
4.  Fare clic sull'icona di Excel nella barra dei menu.  
  
5.  Fare clic su **Abilita**quando viene richiesto di abilitare le connessioni dati. Viene visualizzato Excel utilizzando la connessione dati corrente e aggiungendo una tabella pivot al foglio di lavoro in modo che sia possibile cominciare l'esplorazione dei dati.  
  
 A questo punto, è possibile compilare in modo interattivo una tabella pivot trascinando le misure dalla tabella dei fatti nell'area Valori e gli attributi della dimensione alle aree Riga e Colonna. Se sono disponibili gerarchie, aggiungerle all'area Righe o Colonna. È possibile eseguire il rollup o il drill-down della gerarchia per esplorare i dati della tabella dei fatti a livelli diversi.  
  
 Gli oggetti e i dati vengono visualizzati all'interno del contesto dell'utente effettivo o del ruolo e della prospettiva. In Excel, vengono utilizzate le credenziali dell'utente corrente, non quelle specificate nella pagina **Impostazioni di rappresentazione** , per la connessione all'origine dati quando viene eseguita una query.  
  
> [!NOTE]  
>  Per utilizzare la funzionalità Analizza in Excel, è necessario che Excel sia installato nello stesso computer di [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. In caso contrario, è possibile utilizzare Excel in un altro computer e connettersi al cubo come origine dati. Successivamente, è possibile aggiungere manualmente una tabella pivot al foglio di lavoro. Gli oggetti del modello (tabelle, colonne, misure e indicatori KPI) sono inclusi come campi nel relativo elenco della tabella pivot.  
  
 Per ulteriori informazioni sulla funzionalità **Analizza in Excel** , vedere le seguenti risorse.  
  
 [Analizza in Excel &#40;tabulare di SSAS&#41;](tabular-models/analyze-in-excel-ssas-tabular.md)  
  
 [Analizzare un modello tabulare in Excel &#40;tabulare di SSAS&#41;](tabular-models/analyze-a-tabular-model-in-excel-ssas-tabular.md)  
  
 [Esplorare dati e metadati in un cubo](multidimensional-models/browse-data-and-metadata-in-cube.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Browser &#40;Progettazione cubi&#41; &#40;Analysis Services - dati multidimensionali&#41;](browser-cube-designer-analysis-services-multidimensional-data.md)   
 [Barra degli strumenti &#40;scheda esplorazione, Progettazione cubi&#41; &#40;Analysis Services - dati multidimensionali&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [I metadati &#40;scheda esplorazione, Progettazione cubi&#41; &#40;Analysis Services - dati multidimensionali&#41;](metadata-browser-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [Progettazione query e filtro &#40;scheda esplorazione, Progettazione cubi&#41; &#40;Analysis Services - dati multidimensionali&#41;](query-filter-browser-cube-designer-analysis-services-multidimensional-data.md)  
  
  
---
title: Sezionare il cubo di origine (Creazione guidata Data Mining) | Documenti Microsoft
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
- sql12.dm.dmwizard.slicesourcecube.f1
ms.assetid: 16485608-d3b9-49ee-8baa-948038cdd7ec
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: a0e3badd385e654db3b869a197130fde26fbffcc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157008"
---
# <a name="slice-source-cube-data-mining-wizard"></a>Sezionamento cubo di origine (Creazione guidata modello di data mining)
  È possibile utilizzare la finestra di dialogo **Sezionamento cubo di origine** per limitare i dati utilizzati per il training del modello. In genere un cubo contiene i dati correlati a molti attributi e dimensioni diversi, ad esempio tutti i negozi, tutte le aree e tutti i prodotti. Poiché non è pratico eseguire il training di un modello su un numero illimitato di combinazioni di attributi, utilizzare questa finestra di dialogo per scegliere un set specifico da utilizzare per il training di un modello.  
  
 Ad esempio, nel cubo AdventureWorks è possibile sezionare per una linea di prodotti, un'area o un anno specifico per ottenere una parte dei dati.  
  
 Se non si ha familiarità con le sezioni e con i cubi, è consigliabile consultare questi articoli:  
  
-   [Impostare la proprietà Slice delle partizioni &#40;Analysis Services&#41;](multidimensional-models/set-the-partition-slice-property-analysis-services.md)  
  
-   [Creare e gestire una partizione locale &#40;Analysis Services&#41;](multidimensional-models/create-and-manage-a-local-partition-analysis-services.md)  
  
> [!NOTE]  
>  Si noti che le funzioni MDX dinamiche, ad esempio [Generate &#40;MDX&#41;](/sql/mdx/generate-mdx) o [Except &#40;MDX&#41;](/sql/mdx/except-mdx-function) non sono supportate nella proprietà Slice per le partizioni. È necessario definire la sezione usando tuple esplicite o riferimenti ai membri.  
>   
>  Ad esempio, anziché usare [: &#40;intervallo&#41; &#40;MDX&#41; ](/sql/mdx/range-mdx) per definire un intervallo, è necessario enumerare ogni membro in base agli anni specifici.  
>   
>  Se occorre definire una sezione complessa, è consigliabile definire le tuple nella sezione mediante uno script XMLA Alter. Quindi, è possibile utilizzare lo strumento da riga di comando ascmd o SSIS [Services attività Esegui DDL Analysis](../integration-services/control-flow/analysis-services-execute-ddl-task.md) per eseguire lo script e creare il set di membri specificato immediatamente prima dell'elaborazione della partizione.  
  
 **Per altre informazioni:** [Creazione guidata modello di data mining &#40;Analysis Services - Data mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md) e [Creare una struttura di data mining relazionale](data-mining/create-a-relational-mining-structure.md)  
  
## <a name="options"></a>Opzioni  
 **Dimension**  
 Consente di selezionare la dimensione che si desidera sezionare.  
  
 **Hierarchy**  
 Consente di selezionare la gerarchia che si desidera sezionare. È possibile scegliere qualsiasi livello di una gerarchia, ma gli attributi utilizzati nel modello saranno valido solo al livello selezionato.  
  
 Se ad esempio si sceglie la gerarchia Geography e si seleziona Country come livello, non è possibile compilare un modello che utilizza City come attributi. Viceversa, se si sceglie City come livello della gerarchia in base a cui eseguire il sezionamento, non è possibile creare un modello di data mining basato su Country.  
  
 **Operatore**  
 Selezionare l'operatore da utilizzare per la compilazione di un'espressione di sezione.  
  
 Se ad esempio si sceglie Geography come gerarchia, è possibile selezionare l'operatore = quindi digitare "Europe" come filtro, per ottenere i dati del cubo per solo per l'Europa.  
  
 **Espressione filtro**  
 Digitare un'espressione da utilizzare come criterio per filtrare il cubo in base alla dimensione selezionata.  
  
 **Parametri**  
 Questa opzione non è utilizzata per i modelli di data mining.  
  
## <a name="see-also"></a>Vedere anche  
 [Completamento procedura guidata &#40;Creazione guidata di Data Mining&#41;](completing-the-wizard-data-mining-wizard.md)   
 [Data Mining della Guida F1 di procedura guidata &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md)   
 [Specificare l'utilizzo colonne modello di Data Mining &#40;Creazione guidata di Data Mining&#41;](specify-mining-model-column-usage-data-mining-wizard.md)  
  
  

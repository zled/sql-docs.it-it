---
title: Ordinare i dati in una tabella (SSAS tabulare) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5fa6ad56-bf68-4aac-a226-52556173b7e2
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 156f75856c371914c41519a1ce577c02e4773679
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064984"
---
# <a name="sort-data-in-a-table-ssas-tabular"></a>Ordinare i dati di una tabella (SSAS tabulare)
  È possibile ordinare i dati per testo (da A a Z o da Z ad A) e numeri (dal più piccolo al più grande o dal più grande al più piccolo) in una o più colonne.  
  
### <a name="to-sort-the-data-in-a-table-based-on-a-text-column"></a>Per ordinare i dati in una tabella basata su una colonna di testo  
  
1.  In Progettazione modelli selezionare una colonna di dati alfanumerici, un intervallo di celle in una colonna oppure assicurarsi che la cella attiva si trovi in una colonna di una tabella contenente dati alfanumerici, quindi fare clic sulla freccia nell'intestazione della colonna in base alla quale filtrare i dati.  
  
2.  Nel menu Filtro automatico effettuare uno dei passaggi seguenti:  
  
    -   Per ordinare in ordine alfanumerico crescente, fare clic su **Ordina da A a Z**.  
  
    -   Per ordinare in ordine alfanumerico decrescente, fare clic su **Ordina da Z a A**.  
  
    > [!NOTE]  
    >  In alcuni casi, dati importati da un'altra applicazione potrebbero presentare spazi iniziali inseriti prima dei dati stessi. È necessario rimuovere gli spazi iniziali per ordinare correttamente i dati.  
  
### <a name="to-sort-the-data-in-a-table-based-on-a-numeric-column"></a>Per ordinare i dati in una tabella basata su una colonna numerica  
  
1.  In Progettazione modelli selezionare una colonna di dati alfanumerici, un intervallo di celle in una colonna oppure assicurarsi che la cella attiva si trovi in una colonna di una tabella contenente dati alfanumerici, quindi fare clic sulla freccia nell'intestazione della colonna in base alla quale filtrare i dati.  
  
2.  Nel menu Filtro automatico effettuare uno dei passaggi seguenti:  
  
    -   Per l'ordinamento ascendente fare clic su **Ordina dal più piccolo al più grande**.  
  
    -   Per l'ordinamento discendente fare clic su **Ordina dal più grande al più piccolo**.  
  
    > [!NOTE]  
    >  Se i risultati non sono quelli previsti, la colonna potrebbe contenere numeri archiviati come testo e non come numeri. Ad esempio numeri negativi importati da alcuni sistemi di contabilità o un numero immesso con carattere apostrofo (') iniziale, vengono archiviati come testo.  
  
## <a name="see-also"></a>Vedere anche  
 [Filtrare e ordinare i dati &#40;tabulare di SSAS&#41;](../filter-and-sort-data-ssas-tabular.md)   
 [Prospettive &#40;tabulare di SSAS&#41;](perspectives-ssas-tabular.md)   
 [Ruoli &#40;tabulare di SSAS&#41;](roles-ssas-tabular.md)  
  
  
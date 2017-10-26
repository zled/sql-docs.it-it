---
title: Modifica tabella, colonna o il mapping dei filtri di riga (SSAS tabulare) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2124c526-5772-4f84-a019-9dd3e906e8dd
caps.latest.revision: 10
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b80323e5aaf1dd6c469ddffefb5d92542e9d3a19
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="change-table-column-or-row-filter-mappings-ssas-tabular"></a>Modificare i mapping di filtri tabella, colonna o riga (SSAS tabulare)
  Questo argomento descrive come modificare i mapping di filtri tabella, colonna o riga tramite la finestra di dialogo **Modifica proprietà tabella** di [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
 Le opzioni disponibili nella finestra di dialogo **Modifica proprietà tabella** sono diverse, a seconda che i dati siano stati originariamente importati selezionando tabelle da un elenco o usando una query SQL. Se i dati sono stati originariamente importati selezionandoli da un elenco, nella finestra di dialogo **Modifica proprietà tabella** viene visualizzata la modalità Anteprima tabella. Questa modalità consente di visualizzare solo un subset limitato alle prime cinquanta righe della tabella di origine. Se i dati sono stati originariamente importati usando un'istruzione SQL, nella finestra di dialogo **Modifica proprietà tabella** viene visualizzata solo un'istruzione SQL. Utilizzando un'istruzione di query SQL è possibile recuperare un subset di righe progettando un filtro o modificando manualmente l'istruzione SQL.  
  
 Se per l'origine si imposta una tabella con colonne diverse rispetto alla tabella corrente, viene visualizzato un messaggio indicante che le colonne sono diverse. Sarà necessario quindi selezionare le colonne che si desidera inserire nella tabella corrente e fare clic su **Salva**. Selezionando la casella di controllo a sinistra della tabella è possibile sostituire l'intera tabella.  
  
> [!NOTE]  
>  Se nella tabella è presente più di una partizione, non è possibile utilizzare la finestra di dialogo Modifica proprietà tabella per modificare i mapping del filtro di riga. Per modificare i mapping del filtro di riga per le tabelle con più partizioni, utilizzare Gestione partizioni. Per altre informazioni, vedere [Partizioni &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/partitions-ssas-tabular.md).  
  
#### <a name="to-change-table-column-or-row-filter-mappings"></a>Per modificare i mapping dei filtri tabella, colonna o riga  
  
1.  In Progettazione modelli fare clic su una tabella e quindi scegliere **Proprietà tabella** dal menu **Tabella**.  
  
2.  Nella finestra di dialogo **Modifica proprietà tabella** individuare la colonna in cui sono contenuti i criteri in base ai quali si vuole filtrare e quindi fare clic sulla freccia GIÙ a destra dell'intestazione di colonna.  
  
3.  Nel menu **Filtro automatico** effettuare uno dei passaggi seguenti:  
  
    -   Nell'elenco di valori delle colonne selezionare o deselezionare uno o più valori da utilizzare come filtri, quindi fare clic su OK.  
  
         Se il numero di valori è estremamente elevato, singoli elementi potrebbero non essere visualizzati nell'elenco. Verrà invece visualizzato il messaggio, "Troppi elementi da visualizzare".  
  
    -   Fare clic su **Filtri per numeri** o su **Filtri per testo** (a seconda del tipo di colonna) e quindi fare clic su uno dei comandi di operatore di confronto (ad esempio Uguale a) o su Filtro personalizzato. Nella finestra di dialogo **Filtro personalizzato** creare il filtro, quindi fare clic su **OK**.  
  
         Se si commette un errore ed è necessario ricominciare, fare clic su **Cancella filtri di riga**.  
  
## <a name="see-also"></a>Vedere anche  
 [Finestra di dialogo Modifica proprietà tabella &#40;SSAS&#41;](http://msdn.microsoft.com/library/8d913e83-7246-44cc-8fc7-31729023c0d8)  
  
  


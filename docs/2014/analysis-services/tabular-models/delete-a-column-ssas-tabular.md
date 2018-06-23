---
title: Eliminare una colonna (SSAS tabulare) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 703db83b-e554-450e-813e-23ad08c1cdad
caps.latest.revision: 4
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: bef4966295acafa3b122fe1786cf06495962890d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169976"
---
# <a name="delete-a-column-ssas-tabular"></a>Eliminare una colonna (SSAS tabulare)
  In questo argomento viene descritto come eliminare una colonna da una tabella di modello tabulare.  
  
## <a name="delete-a-model-table-column"></a>Eliminare una colonna dalla tabella del modello  
  
> [!NOTE]  
>  L'eliminazione di una colonna da una tabella del modello non elimina la colonna da una definizione della query della partizione. Se la colonna che si desidera eliminare fa parte di una partizione, è necessario eliminare manualmente la colonna dalla definizione della query della partizione. Se non si elimina la colonna dalla definizione della query della partizione, durante le operazioni di elaborazione verranno eseguite query sulla colonna e restituiti dati che tuttavia non saranno popolati nella tabella del modello. Per altre informazioni, vedere [Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md).  
  
#### <a name="to-delete-a-model-table-column"></a>Per eliminare una colonna dalla tabella del modello  
  
-   In Progettazione modelli, nella tabella contenente la colonna che si desidera eliminare, fare clic con il pulsante destro del mouse su tale colonna, quindi scegliere **Elimina**.  
  
#### <a name="to-delete-a-model-table-column-by-using-the-table-properties-dialog-box"></a>Per eliminare una colonna dalla tabella del modello tramite la finestra di dialogo Proprietà tabella  
  
1.  In Progettazione modelli fare clic sulla tabella contenente la colonna che si desidera eliminare, quindi scegliere **Proprietà tabella** dal menu  **Tabella**.  
  
2.  In **Nomi colonne da**selezionare **Modello** (*per usare nomi delle colonna della tabella del modello, se diversi dall'origine*).  
  
3.  Nella finestra di anteprima della tabella nella finestra di dialogo **Modifica proprietà tabella** deselezionare la colonna che si desidera eliminare, quindi scegliere **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere colonne a una tabella &#40;tabulare di SSAS&#41;](add-columns-to-a-table-ssas-tabular.md)   
 [Partizioni &#40;tabulare di SSAS&#41;](partitions-ssas-tabular.md)  
  
  
---
title: "Eliminare una colonna (SSAS tabulare) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 703db83b-e554-450e-813e-23ad08c1cdad
caps.latest.revision: 5
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 5
---
# Eliminare una colonna (SSAS tabulare)
  In questo argomento viene descritto come eliminare una colonna da una tabella di modello tabulare.  
  
## Eliminare una colonna dalla tabella del modello  
  
> [!NOTE]  
>  L'eliminazione di una colonna da una tabella del modello non elimina la colonna da una definizione della query della partizione. Se la colonna che si desidera eliminare fa parte di una partizione, è necessario eliminare manualmente la colonna dalla definizione della query della partizione. Se non si elimina la colonna dalla definizione della query della partizione, durante le operazioni di elaborazione verranno eseguite query sulla colonna e restituiti dati che tuttavia non saranno popolati nella tabella del modello. Per altre informazioni, vedere [partizioni &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/partitions-ssas-tabular.md).  
  
#### Per eliminare una colonna dalla tabella del modello  
  
-   In Progettazione modelli, nella tabella contenente la colonna che si desidera eliminare, fare clic con il pulsante destro del mouse su tale colonna, quindi scegliere **Elimina**.  
  
#### Per eliminare una colonna dalla tabella del modello tramite la finestra di dialogo Proprietà tabella  
  
1.  In Progettazione modelli fare clic sulla tabella contenente la colonna che si desidera eliminare, quindi scegliere **Proprietà tabella** dal menu **Tabella**.  
  
2.  In **Nomi colonne da** selezionare **Modello** (*per usare nomi delle colonna della tabella del modello, se diversi dall'origine*).  
  
3.  Nella finestra di anteprima della tabella nella finestra di dialogo **Modifica proprietà tabella** deselezionare la colonna che si desidera eliminare, quindi scegliere **OK**.  
  
## Vedere anche  
 [Aggiungere colonne a una tabella &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/add-columns-to-a-table-ssas-tabular.md)   
 [Partizioni &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/partitions-ssas-tabular.md)  
  
  
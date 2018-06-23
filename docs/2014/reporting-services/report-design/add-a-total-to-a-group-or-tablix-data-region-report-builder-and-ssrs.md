---
title: Aggiungere un totale a un gruppo o a un'area dati Tablix (Generatore report e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf1b96c3-7f0f-4c94-ad08-5239c77ccfe4
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: d44ac2a0029f1494314645a9aa613b605b666c44
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36168243"
---
# <a name="add-a-total-to-a-group-or-tablix-data-region-report-builder-and-ssrs"></a>Aggiungere un totale a un gruppo o a un'area dati Tablix (Generatore report e SSRS)
  È possibile aggiungere totali in un'area dati Tablix per un gruppo o per l'intera area dati. Per impostazione predefinita, un totale è la somma dei dati numerici non Null presenti in un gruppo o nell'area dati dopo che sono stati applicati i filtri. Per aggiungere totali per un gruppo, fare clic su **Aggiungi totale** nel menu di scelta rapida per il gruppo nel riquadro di raggruppamento. Per aggiungere totali per una cella singola nell'area del corpo della Tablix, fare clic su **Aggiungi totale** nel menu di scelta rapida per la cella. Il comando **Aggiungi totale** è sensibile al contesto ed è abilitato solo per i campi numerici. A seconda della cella Tablix che si seleziona, è possibile aggiungere un totale per una sola cella selezionando una cella nell'area del corpo della Tablix o per l'intero gruppo selezionando una cella nell'area del gruppo di righe o del gruppo di colonne Tablix. Per ulteriori informazioni sulle aree tablix, vedere [area dati Tablix &#40;Generatore Report e SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md).  
  
 Dopo avere aggiunto un totale, è possibile impostare la funzione Sum predefinita su una funzione di aggregazione diversa dell'elenco di funzioni del report incorporate. Per altre informazioni, vedere [Riferimento a funzioni di aggregazione &#40;Generatore report e SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).[!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-total-for-an-individual-value-in-the-tablix-body-area"></a>Per aggiungere un totale per un valore singolo nell'area del corpo della Tablix  
  
-   Nell'area del corpo dell'area dati Tablix fare clic con il pulsante destro del mouse sulla cella in cui si desidera aggiungere il totale. La cella deve contenere un campo numerico. Scegliere **Aggiungi totale**, quindi fare clic su **Riga** o su **Colonna**.  
  
     Una nuova riga o una nuova colonna esterna al gruppo corrente viene aggiunta all'area dati, con un totale predefinito per il campo nella cella selezionata.  
  
     Se l'area dati Tablix è una tabella, una riga viene aggiunta automaticamente.  
  
### <a name="to-add-totals-for-a-row-group"></a>Per aggiungere totali per un gruppo di righe  
  
-   Nell'area del gruppo di righe dell'area dati Tablix fare clic con il pulsante destro del mouse su una cella nell'area del gruppo di righe di cui si desidera ottenere i totali, scegliere **Aggiungi totale**e fare clic su **Prima** o **Dopo**.  
  
     Una nuova riga esterna al gruppo corrente verrà aggiunta all'area dati, quindi verrà aggiunto un totale predefinito per ogni campo numerico della riga.  
  
### <a name="to-add-totals-for-a-column-group"></a>Per aggiungere totali per un gruppo di colonne  
  
-   Nell'area del gruppo di righe dell'area dati Tablix fare clic con il pulsante destro del mouse su una cella nell'area del gruppo di colonne di cui si desidera ottenere i totali, scegliere **Aggiungi totale**e fare clic su **Prima** o **Dopo**.  
  
     Una nuova colonna esterna al gruppo corrente verrà aggiunta all'area dati, quindi verrà aggiunto un totale predefinito per ogni campo numerico della colonna.  
  
## <a name="see-also"></a>Vedere anche  
 [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;SSRS e Generatore Report&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)   
 [Area dati Tablix &#40;Generatore report e SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md)   
 [Tabelle &#40;Generatore report e SSRS&#41;](tables-report-builder-and-ssrs.md)   
 [Matrici &#40;Generatore report e SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)   
 [Elenchi &#40;Generatore report e SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [Tabelle, matrici ed elenchi &#40;Generatore report e SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
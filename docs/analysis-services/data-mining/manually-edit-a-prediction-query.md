---
title: Modificare manualmente una Query di stima | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modifying prediction queries
- Mining Model Prediction [Analysis Services], modifying prediction queries
- manual prediction query modification [Analysis Services]
ms.assetid: 9f6a9298-49d5-4675-ad49-977a47dff5a6
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 57f892500d2ef26dc2227b4c0710c4d039dcb34e
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="manually-edit-a-prediction-query"></a>Modificare manualmente un query di stima
  Dopo avere progettato una query tramite il generatore delle query di stima, è possibile modificarla passando alla visualizzazione Testo query nella scheda **Stima modello di data mining** di Progettazione modelli di data mining. Nella parte inferiore dello schermo viene visualizzato un editor di testo per visualizzare la query creata tramite il generatore delle query.  
  
 Il passaggio alla vista Testo della query è utile per effettuare aggiunte alla query. Ad esempio, è possibile aggiungere una clausola WHERE o ORDER BY.  
  
 Utilizzare la griglia nel generatore delle query di stima per inserire i nomi di oggetti e colonne e impostare la sintassi per le singole funzioni di stima, quindi passare alla modalità di modifica manuale per modificare i valori di parametro.  
  
> [!NOTE]  
>  Se si passa nuovamente alla vista **Progettazione** dalla vista **Testo query** , qualsiasi modifica apportata in **Testo query** andrà persa.  
  
### <a name="modify-a-query"></a>Modificare una query  
  
1.  Nella scheda **Stima modello di data mining** di Progettazione modelli di data mining in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]fare clic su **SQL**.  
  
     La griglia visualizzata nella parte inferiore dello schermo verrà sostituita da un editor di testo che include la query. È possibile digitare le modifiche alla query nell'editor.  
  
2.  Per eseguire la query, scegliere **Risultato** dal menu **Modello di data mining**o fare clic sul pulsante per passare ai risultati della query.  
  
    > [!NOTE]  
    >  Se la query creata non è valida, nella finestra Risultati non verrà segnalato un errore e non verrà visualizzato alcun risultato. Fare clic sul pulsante **Progettazione** oppure scegliere **Progettazione** o **Query** dal menu **Modello di data mining** per correggere il problema ed eseguire nuovamente la query.  
  
## <a name="see-also"></a>Vedere anche  
 [Query di data mining](../../analysis-services/data-mining/data-mining-queries.md)   
 [Generatore di Query di stima &#40; Data Mining &#41;](http://msdn.microsoft.com/library/12900d49-db88-48bb-a5f4-0a9a172bc126)   
 [Lezione 6: Creazione e utilizzo di stime &#40;Esercitazione di base sul data mining&#41;](http://msdn.microsoft.com/library/b213cb58-2c40-4c89-b08b-d3c36a4afad3)  
  
  


---
title: 'Attività 9: Aggiunta di Union All Trasforma per combina record corretti e con correzione | Documenti Microsoft'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 24ba466d-a7d3-49e7-9111-b348399c9e58
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: df61e9219c179ab934a33a78f13499351047bf4b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169539"
---
# <a name="task-9-adding-union-all-transform-to-combine-correct-and-corrected-records"></a>Attività 9: Aggiunta della trasformazione Unione input multipli a Combina record corretti e con correzione
  In questa attività viene aggiunta la trasformazione Unione input multipli al flusso di dati. La trasformazione Unione input multipli consente di combinare più input in un unico output. Nello scenario attuale i record corretti e con correzione vengono combinati in un flusso.  
  
1.  Trascinare **unione input multipli** trasformare dalla **comuni** sezione del **casella degli strumenti SSIS** per il **del flusso di dati** scheda e inserirlo in **Seleziona record corretti e con correzione**.  
  
2.  Fare doppio clic su **unione input multipli** trasformare il **del flusso di dati** scheda e fare clic su **rinominare**. Tipo di **combina record corretti e**, quindi premere **invio**.  
  
     ![Combinare Reocrds corretti e con correzione](../../2014/tutorials/media/et-addinguattocombinecacrecords-01.jpg "combinare Reocrds corretti e con correzione")  
  
3.  Connettersi **Seleziona record corretti e** alla **combina record corretti e** nel **flusso di dati** scheda utilizzando il collegamento blu. Dovrebbe vedere il **selezione Input e Output** finestra di dialogo.  
  
4.  Nel **interdipendenze** finestra di dialogo **corretti** per **Output** e fare clic su **OK**.  
  
     ![Finestra di dialogo di selezione di Output di input](../../2014/tutorials/media/et-addinguattocombinecacrecords-02.jpg "Output finestra di dialogo di selezione di Input")  
  
5.  Spostare il collegamento denominato **correggere** a sinistra trascinando e rilasciando il punto alla fine del connettore a sinistra.  
  
     ![Connetti Correggi a combina corretto e con correzione](../../2014/tutorials/media/et-addinguattocombinecacrecords-03.jpg "Connetti Correggi a combina corretto e con correzione")  
  
6.  Se si seleziona **Seleziona record corretti e** trasformare, verrà visualizzato un altro collegamento blu. Trascinare blu in **combina record corretti e**.  
  
     ![Connetti con correzione a combina corretto e con correzione](../../2014/tutorials/media/et-addinguattocombinecacrecords-04.jpg "Connetti con correzione a combina corretto e con correzione")  
  
7.  Ciò **connettore** deve essere denominato **con correzione**. Poiché sono disponibili solo due condizioni **correggere** e **con correzione**, e una condizione è già stata usata, il **selezione Input e Output** finestra di dialogo non viene visualizzata questa ora. Se i collegamenti si sovrappongono, spostarne uno a sinistra e l'altro a destra trascinando il collegamento a sinistra o a destra.  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 10: Aggiunta della trasformazione Raggruppamento Fuzzy per identificare i duplicati](../../2014/tutorials/task-10-adding-fuzzy-group-transform-to-identify-duplicates.md)  
  
  
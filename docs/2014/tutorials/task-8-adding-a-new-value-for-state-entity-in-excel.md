---
title: "Attività 8: Aggiunta di un nuovo valore per l'entità State in Excel | Microsoft Docs"
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
ms.topic: conceptual
ms.assetid: a763d76b-06a3-4d51-9614-01fc9fb1c158
caps.latest.revision: 7
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4f4e79915ba28beb7cd28920faff2f79e6b339d6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37163772"
---
# <a name="task-8-adding-a-new-value-for-state-entity-in-excel"></a>Attività 8: Aggiunta di un nuovo valore per l'entità State in Excel
  In questa attività viene aggiunto un valore per l'entità State in Excel e viene pubblicata la modifica nel server MDS.  
  
1.  Aggiungere un **foglio di lavoro** in Excel facendo clic sulla nuova scheda nella parte inferiore.  
  
     ![Excel - nuova scheda del foglio di lavoro](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-01.jpg "Excel - nuova scheda del foglio di lavoro")  
  
2.  Nelle **Excel**, fare clic sui **Master Data** scheda nel menu e quindi fare clic su **Mostra Esplora** sulla barra multifunzione.  
  
3.  Nel **Esplora dati Master**, selezionare **Suppliers** per **modello**. Verranno visualizzate due entità: **Supplier** e **stato** nell'elenco delle entità.  
  
4.  Fare doppio clic su **stato** nell'elenco. Tutti i membri del **stato** deve essere visualizzato entità da MDS nel foglio di lavoro.  
  
5.  A questo punto, aggiungere una riga alla fine con i valori seguenti: **Carolina del Nord** per **Name** e **NC** per **codice**. La codifica tramite colori consente di differenziare tutti i record nuovi/aggiornati dagli altri record.  
  
     ![Excel - Aggiungi Nord Carolina agli stati](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-02.jpg "Excel - Aggiungi Nord Carolina agli Stati")  
  
6.  Fare clic su **pubblica** sulla barra multifunzione per pubblicare la modifica in MDS.  
  
     ![Excel - pulsante pubblica nella scheda dati Master](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-03.jpg "Excel - pulsante pubblica nella scheda dati Master")  
  
7.  Nel **pubblicazione e annotazione** finestra di dialogo casella, si noti che le **Usa la stessa annotazione per tutte le modifiche** sia selezionata. È possibile specificare una sola annotazione per tutte le modifiche apportate in questo punto.  
  
8.  Selezionare **rivedere le modifiche e fornisci annotazioni individualmente** opzione per specificare l'annotazione per ogni modifica (in questo caso, solo uno).  
  
     ![Excel - pubblicazione e annotazione nella finestra di dialogo](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-04.jpg "di Excel: pubblicazione e annotazione nella finestra di dialogo")  
  
9. Fare clic su **pubblica** per pubblicare i dati in MDS.  
  
10. Si noti che **codifica a colori** per la riga con **Carolina del Nord** come il **stato** è ora stessa degli altri record.  
  
11. **Facoltativo:** verificare che il nuovo membro (NC) viene aggiunto al **stato** entità utilizzando la **Esplora** in **gestione dati Master**.  
  
12. In Excel, fare doppio clic il **lo stato** foglio di lavoro nella parte inferiore, fare clic su **eliminare** per eliminare il foglio di lavoro. L'eliminazione del foglio di lavoro non comporta l'eliminazione dei dati dal server MDS.  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 9: Creazione di una gerarchia derivata mediante Gestione dati master](../../2014/tutorials/task-9-creating-a-derived-hierarchy-using-master-data-manager.md)  
  
  

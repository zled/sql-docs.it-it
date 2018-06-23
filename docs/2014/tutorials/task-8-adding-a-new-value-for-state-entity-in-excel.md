---
title: "Attività 8: Aggiunta di un nuovo valore per l'entità State in Excel | Documenti Microsoft"
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
ms.assetid: a763d76b-06a3-4d51-9614-01fc9fb1c158
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: db2eaccd4d9b344cbc1b7c25b6fec940ff9c77a9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36166966"
---
# <a name="task-8-adding-a-new-value-for-state-entity-in-excel"></a>Attività 8: Aggiunta di un nuovo valore per l'entità State in Excel
  In questa attività viene aggiunto un valore per l'entità State in Excel e viene pubblicata la modifica nel server MDS.  
  
1.  Aggiungere un **foglio di lavoro** in Excel facendo clic sulla nuova scheda nella parte inferiore.  
  
     ![Excel - nuova scheda del foglio di lavoro](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-01.jpg "Excel - nuova scheda del foglio di lavoro")  
  
2.  In **Excel**, fare clic sui **dati Master** scheda nel menu e quindi fare clic su **Mostra Esplora** sulla barra multifunzione.  
  
3.  Nel **Esplora dati Master**, selezionare **Suppliers** per **modello**. Verranno visualizzate due entità: **fornitore** e **stato** nell'elenco delle entità.  
  
4.  Fare doppio clic su **stato** nell'elenco. Tutti i membri del **stato** entità da MDS deve essere visualizzata nel foglio di lavoro.  
  
5.  A questo punto, aggiungere una riga alla fine con i seguenti valori: **North Carolina** per **nome** e **NC** per **codice**. La codifica tramite colori consente di differenziare tutti i record nuovi/aggiornati dagli altri record.  
  
     ![Excel - Aggiungi Nord Carolina agli stati](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-02.jpg "Excel - Aggiungi Nord Carolina agli Stati")  
  
6.  Fare clic su **pubblica** sulla barra multifunzione per pubblicare la modifica in MDS.  
  
     ![Excel - pulsante pubblica nella scheda dati Master](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-03.jpg "Excel - pulsante pubblica nella scheda dati Master")  
  
7.  Nel **pubblicazione e annotazione** finestra di dialogo casella, si noti che il **Usa la stessa annotazione per tutte le modifiche** sia selezionata. È possibile specificare una sola annotazione per tutte le modifiche apportate in questo punto.  
  
8.  Selezionare **esaminare le modifiche e fornisci annotazioni individualmente** opzione per specificare l'annotazione per ogni modifica (in questo caso, solo uno).  
  
     ![Excel - pubblicazione e annotazione finestra di dialogo](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-04.jpg "Excel: pubblicazione e annotare la finestra di dialogo")  
  
9. Fare clic su **pubblica** per pubblicare dati in MDS.  
  
10. Si noti che **codifica a colori** per la riga con **North Carolina** come il **stato** è stessa degli altri record.  
  
11. **Facoltativo:** verificare che il nuovo membro (NC) viene aggiunto per il **stato** entità utilizzando la **Esplora** in **gestione dati Master**.  
  
12. In Excel, fare doppio clic sui **stato** foglio di lavoro in basso e fare clic su **eliminare** per eliminare il foglio di lavoro. L'eliminazione del foglio di lavoro non comporta l'eliminazione dei dati dal server MDS.  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 9: Creazione di una gerarchia derivata mediante gestione dati Master](../../2014/tutorials/task-9-creating-a-derived-hierarchy-using-master-data-manager.md)  
  
  
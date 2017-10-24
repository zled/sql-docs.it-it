---
title: I cursori forward-Only | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cursors [ADO], forward-only
- forward-only cursors [ADO]
ms.assetid: 2b1e062f-3294-4a6f-8241-a17045c4df18
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 121e8eec0b95f66b6e034f1f77d78c7d88fd5184
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="forward-only-cursors"></a>Cursori forward-Only
Il tipo di cursore predefinito tipico, chiamato di un cursore forward-only (o non scorrevole), può passare solo tramite il set di risultati. Un cursore forward-only non supporta lo scorrimento (la possibilità di spostare in avanti e indietro nel set di risultati); supporta solo il recupero delle righe dall'inizio alla fine del set di risultati. Con alcuni cursori forward-only (ad esempio con la libreria di cursori di SQL Server), tutte le istruzioni delete, update e insert eseguite dall'utente corrente (o da altri utenti) che coinvolgono le righe nel set di risultati sono visibili come le righe vengono recuperate. Poiché non è possibile scorrere indietro il cursore, tuttavia, le modifiche apportate alle righe nel database dopo l'operazione di recupero non sono visibili tramite il cursore.  
  
 Dopo l'elaborazione di dati per la riga corrente, il cursore forward-only rilascia le risorse che sono state utilizzate per contenere i dati. I cursori forward-only sono dinamici per impostazione predefinita, vale a dire che tutte le modifiche vengono rilevate durante l'elaborazione della riga corrente. Fornisce l'apertura del cursore più veloce e consente il set di risultati per visualizzare gli aggiornamenti apportati alle tabelle sottostanti.  
  
 Mentre i cursori forward-only non supportano lo scorrimento all'indietro, l'applicazione può restituire all'inizio del set di risultati tramite chiudere e riaprire il cursore. Si tratta di un metodo efficace per lavorare con piccole quantità di dati. In alternativa, l'applicazione potrebbe leggere il set di risultati una volta, nella cache i dati in locale e quindi selezionare la cache locale dei dati.  
  
 Se l'applicazione non è necessario scorrere il set di risultati, il cursore forward-only è il modo migliore per recuperare i dati rapidamente con la quantità minima di carico. Utilizzare il **adOpenForwardOnly CursorTypeEnum** per indicare che si desidera utilizzare un cursore forward-only in ADO.  
  
## <a name="see-also"></a>Vedere anche  
 [Cursori statici](../../../ado/guide/data/static-cursors.md)   
 [Cursori keyset](../../../ado/guide/data/keyset-cursors.md)   
 [Cursori dinamici](../../../ado/guide/data/dynamic-cursors.md)


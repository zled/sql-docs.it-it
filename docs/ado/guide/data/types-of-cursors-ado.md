---
title: Tipi di cursori (ADO) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cursors [ADO], types
ms.assetid: 7cc01544-e814-403b-bbfe-a2750bf921bd
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3ec8ccca017236a8f6aa784d92e8304a98452f02
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="types-of-cursors-ado"></a>Tipi di cursori (ADO)
Come regola generale, l'applicazione deve utilizzare il cursore più semplice che fornisce l'accesso ai dati richiesti. Ogni caratteristica di cursore aggiuntive oltre le nozioni di base (forward-only, di sola lettura, statici, scorrevoli) dispone di un prezzo, nella memoria client, il carico di rete o prestazioni. In molti casi, le opzioni di cursore predefinito generano un cursore più complesso rispetto a effettivamente necessaria per l'applicazione.  
  
 La scelta del tipo di cursore dipende dalla modalità con cui l'applicazione utilizza il set di risultati e anche diverse considerazioni di progettazione, tra cui la dimensione del set di risultati, la percentuale dei dati possono essere usati, sensibilità alle modifiche dei dati e le prestazioni dell'applicazione requisiti.  
  
 In parole semplici, la scelta del cursore varia a seconda se è necessario modificare o semplicemente visualizzare i dati:  
  
-   Se è necessario solo lo scorrimento di un set di risultati, ma non modificare i dati, utilizzare un [forward-only](../../../ado/guide/data/forward-only-cursors.md) o [statico](../../../ado/guide/data/static-cursors.md) cursore.  
  
-   Se si dispone di un set di risultati di grandi dimensioni ed è necessario selezionare solo poche righe, utilizzare un [keyset](../../../ado/guide/data/keyset-cursors.md) cursore.  
  
-   Se si desidera sincronizzare un set di risultati con recente aggiunge, modifica ed Elimina tutti gli utenti simultanei, utilizzare un [dinamica](../../../ado/guide/data/dynamic-cursors.md) cursore.  
  
 Sebbene ogni tipo di cursore sembra essere distinti, tenere presente che questi tipi di cursore non sono molto varia a seconda come semplicemente il risultato della combinazione di caratteristiche e le opzioni.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Cursori forward-only](../../../ado/guide/data/forward-only-cursors.md)  
  
-   [Cursori statici](../../../ado/guide/data/static-cursors.md)  
  
-   [Cursori keyset](../../../ado/guide/data/keyset-cursors.md)  
  
-   [Cursori dinamici](../../../ado/guide/data/dynamic-cursors.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Cursori forward-Only](../../../ado/guide/data/forward-only-cursors.md)   
 [Cursori statici](../../../ado/guide/data/static-cursors.md)   
 [Cursori keyset](../../../ado/guide/data/keyset-cursors.md)   
 [Cursori dinamici](../../../ado/guide/data/dynamic-cursors.md)

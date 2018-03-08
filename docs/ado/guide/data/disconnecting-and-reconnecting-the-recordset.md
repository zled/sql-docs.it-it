---
title: Disconnessione e riconnessione Recordset | Documenti Microsoft
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
- Recordset object [ADO], disconnecting and reconnecting
ms.assetid: c5134af7-81d6-4de4-9fd1-cfe29973545e
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 66ef21ccf6826edf78847c0fc2c6d043f3960ea2
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="disconnecting-and-reconnecting-the-recordset"></a>Disconnessione e riconnessione dell'oggetto Recordset
Una delle funzionalità più potenti disponibili in ADO è la possibilità di aprire un oggetto Recordset sul lato client da un'origine dati, quindi si disconnette il Recordset dall'origine dati. Dopo il Recordset è stato disconnesso, la connessione all'origine dati è chiuso, per rilasciare le risorse del server utilizzato per gestirlo. È possibile continuare a visualizzare e modificare i dati del recordset mentre è disconnesso e successivamente ristabilire la connessione all'origine dati e inviare gli aggiornamenti in modalità batch.  
  
 Per disconnettere un Recordset, aprire il file con una posizione del cursore di adUseClient e quindi impostare la proprietà ActiveConnection su Nothing. (Gli utenti di C++ devono impostare la proprietà ActiveConnection su NULL da disconnettere.)  
  
 Disconnesso verrà utilizzato più avanti in questa sezione relativa alla persistenza Recordset per risolvere uno scenario in cui è necessario che i dati in un Recordset disponibile per un'applicazione, mentre il computer client non è connesso a una rete.  
  
## <a name="see-also"></a>Vedere anche  
 [Modalità batch](../../../ado/guide/data/batch-mode.md)

---
title: Disconnessione e riconnessione Recordset | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset object [ADO], disconnecting and reconnecting
ms.assetid: c5134af7-81d6-4de4-9fd1-cfe29973545e
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: af20ab2d205813e830301ca6fa015f4b5cda916e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="disconnecting-and-reconnecting-the-recordset"></a>Disconnessione e riconnessione dell'oggetto Recordset
Una delle funzionalità più potenti disponibili in ADO è la possibilità di aprire un oggetto Recordset sul lato client da un'origine dati, quindi si disconnette il Recordset dall'origine dati. Dopo il Recordset è stato disconnesso, la connessione all'origine dati è chiuso, per rilasciare le risorse del server utilizzato per gestirlo. È possibile continuare a visualizzare e modificare i dati del recordset mentre è disconnesso e successivamente ristabilire la connessione all'origine dati e inviare gli aggiornamenti in modalità batch.  
  
 Per disconnettere un Recordset, aprire il file con una posizione del cursore di adUseClient e quindi impostare la proprietà ActiveConnection su Nothing. (Gli utenti di C++ devono impostare la proprietà ActiveConnection su NULL da disconnettere.)  
  
 Disconnesso verrà utilizzato più avanti in questa sezione relativa alla persistenza Recordset per risolvere uno scenario in cui è necessario che i dati in un Recordset disponibile per un'applicazione, mentre il computer client non è connesso a una rete.  
  
## <a name="see-also"></a>Vedere anche  
 [Modalità batch](../../../ado/guide/data/batch-mode.md)

---
title: I cursori mista | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- mixed cursors [ODBC]
- cursors [ODBC], dynamic
- keyset-driven cursors [ODBC]
- dynamic cursors [ODBC]
- cursors [ODBC], key-set driven
- cursors [ODBC], mixed
ms.assetid: 9beb2db9-0b6d-491d-9529-d64e64e59014
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 16fd4840718c286adfe711b6b7322154f7f5f9cb
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="mixed-cursors"></a>Cursori misti
Un cursore misto è una combinazione di un cursore gestito da keyset e un cursore dinamico. Viene utilizzato quando il set di risultati è troppo grande per ragionevolmente Salva le chiavi per l'intero set di risultati. Mista i cursori vengono implementati mediante la creazione di un keyset minore l'intero set di risultati ma maggiore di set di righe.  
  
 Fino a quando l'applicazione consente di scorrere all'interno del keyset, il comportamento è basati su keyset. Quando l'applicazione scorre all'esterno di keyset, il comportamento è dinamico: il cursore recupera le righe richieste e crea un nuovo keyset. Dopo aver creato il nuovo keyset, il comportamento viene ripristinata la basati su keyset all'interno di tale keyset.  
  
 Si supponga, ad esempio, un set di risultati include 1.000 righe e utilizza un cursore misto con una dimensione del keyset pari a 100 e un set di righe pari a 10. Quando vengono recuperati il primo set di righe, il cursore viene creato un keyset costituito dalle chiavi per le prime 100 righe. Restituisce quindi le prime 10 righe, come richiesto.  
  
 Si supponga ora che un'altra applicazione elimina le righe 11 101. Se il cursore tenta di recuperare la riga 11, verificherà un foro perché ha una chiave per questa riga, ma non esiste alcuna riga. si tratta di comportamento basati su keyset. Se il cursore tenta di recuperare la riga 101, il cursore non rileverà che la riga non è disponibile perché non è una chiave per la riga. In alternativa, consente di recuperare che in precedenza era riga 102. Si tratta del comportamento del cursore dinamico.  
  
 Un cursore misto è equivalente a un cursore gestito da keyset quando la dimensione del keyset è uguale alla dimensione del set di risultati. Un cursore misto è equivalente a un cursore dinamico quando la dimensione del keyset è uguale a 1.

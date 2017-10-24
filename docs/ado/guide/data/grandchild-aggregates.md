---
title: Funzioni di aggregazione nipote | Documenti Microsoft
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
- grandchild aggregates [ADO]
- data shaping [ADO], grandchild aggregates
ms.assetid: 4162d35f-2ce1-4218-80a5-b6933348837e
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0785bede442b0f89a9a8a1efacaac03c1aedf2d3
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="grandchild-aggregates"></a>Alle aggregazioni
La colonna del capitolo creata in una clausola di un comando shape può essere assegnata un *nome alias capitolo* (in genere con la parola chiave AS). È possibile identificare ogni colonna in ogni capitolo del data shaping **Recordset** con un nome completo che identifica l'elemento figlio che contiene la colonna. Se, ad esempio, il capitolo padre Cap1 contiene un capitolo figlio Cap2, che include una colonna amount, amt, quindi il nome completo sarebbe chap1.chap2.amt. Il nome completo può quindi essere utilizzato come argomento a una delle funzioni di aggregazione (SUM, AVG, MAX, MIN, COUNT, STDEV o qualsiasi).  
  
## <a name="see-also"></a>Vedere anche  
 [Data Shaping di esempio](../../../ado/guide/data/data-shaping-example.md)


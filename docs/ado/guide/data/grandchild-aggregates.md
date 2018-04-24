---
title: Funzioni di aggregazione nipote | Documenti Microsoft
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
- grandchild aggregates [ADO]
- data shaping [ADO], grandchild aggregates
ms.assetid: 4162d35f-2ce1-4218-80a5-b6933348837e
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 589bece101c52a38d11f10a5d5f8f162aa3af8ad
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="grandchild-aggregates"></a>Alle aggregazioni
La colonna del capitolo creata in una clausola di un comando shape può essere assegnata un *nome alias capitolo* (in genere con la parola chiave AS). È possibile identificare ogni colonna in ogni capitolo del data shaping **Recordset** con un nome completo che identifica l'elemento figlio che contiene la colonna. Se, ad esempio, il capitolo padre Cap1 contiene un capitolo figlio Cap2, che include una colonna amount, amt, quindi il nome completo sarebbe chap1.chap2.amt. Il nome completo può quindi essere utilizzato come argomento a una delle funzioni di aggregazione (SUM, AVG, MAX, MIN, COUNT, STDEV o qualsiasi).  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di data shaping](../../../ado/guide/data/data-shaping-example.md)

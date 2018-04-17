---
title: Limitazioni di identificatori | Documenti Microsoft
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
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: b3466382-71cb-4f82-8318-092a8fcef3df
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e7f8863dbe5f2c8c765caad093237957b25c46c7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="identifiers-limitations"></a>Limitazioni di identificatori
Se un identificatore contiene uno spazio o un simbolo speciale, l'identificatore deve essere racchiuso tra virgolette indietro. Un nome valido è una stringa non più di 64 caratteri, di cui il primo carattere non deve essere uno spazio. I nomi validi non possono contenere caratteri di controllo o i caratteri speciali seguenti: ' &#124; # *? [ ] . ! $ .  
  
 Non utilizzare parole riservate elencate nella grammatica SQL nell'appendice C del *riferimento per programmatori ODBC* (o la forma abbreviata delle parole riservate) come identificatori (vale a dire, tabella o colonna nomi), a meno che non si racchiudono la parola indietro virgolette (').

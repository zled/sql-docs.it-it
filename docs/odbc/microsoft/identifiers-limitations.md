---
title: Limitazioni di identificatori | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: b3466382-71cb-4f82-8318-092a8fcef3df
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ec32697030d2ad4ede765879f83956692ed49914
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="identifiers-limitations"></a>Limitazioni di identificatori
Se un identificatore contiene uno spazio o un simbolo speciale, l'identificatore deve essere racchiuso tra virgolette indietro. Un nome valido è una stringa non più di 64 caratteri, di cui il primo carattere non deve essere uno spazio. I nomi validi non possono contenere caratteri di controllo o i caratteri speciali seguenti: ' &#124; # * ? [ ] . ! $ .  
  
 Non utilizzare parole riservate elencate nella grammatica SQL nell'appendice C del *riferimento per programmatori ODBC* (o la forma abbreviata delle parole riservate) come identificatori (vale a dire, tabella o colonna nomi), a meno che non si racchiudono la parola indietro virgolette (').


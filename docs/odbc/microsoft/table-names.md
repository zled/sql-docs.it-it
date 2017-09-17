---
title: Nomi di tabella | Documenti Microsoft
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
- SQL grammar [ODBC], table names
- table names [ODBC]
ms.assetid: f7a5cb0a-3be7-4f46-82f9-64ffdbceaa9b
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 480ca31108b608139b5563f0c18d1fa020e76f75
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="table-names"></a>Nomi di tabella
Quando il file dBASE, Microsoft Excel, Paradox, o testo driver viene utilizzato, i nomi di tabella che si verificano nella clausola FROM di SELECT o DELETE, dopo la clausola INTO in istruzioni INSERT e dopo l'aggiornamento, CREATE TABLE e DROP TABLE può contenere un percorso valido, nome del server primario e il nome estensione .  
  
 Utilizzo di un nome di tabella in un' posizione in un'istruzione SQL non supporta l'utilizzo di percorsi o le estensioni, ma accetterà solo il nome primario (ad esempio, EMP da C:\ABC\EMP).  
  
 È possono utilizzare i nomi di correlazione (alias). Esempio:  
  
```  
SELECT *    
FROM C:\ABC\EMP T1    
WHERE T1.COL1 = 'aaa'  
```

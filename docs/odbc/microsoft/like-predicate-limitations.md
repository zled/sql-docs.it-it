---
title: Ad esempio limitazioni Predicate | Documenti Microsoft
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
- LIKE predicate limitations [ODBC]
- ODBC SQL grammar, LIKE predicate limitations
ms.assetid: dbd39099-caf6-4c4c-9ad8-f6c63c1bd5e4
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5668f03e785c0d27133965f16af40ce69c2a2567
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="like-predicate-limitations"></a>Ad esempio limitazioni Predicate
Se i dati in una colonna sono più lungo di 255 caratteri, il confronto LIKE si baserà solo i primi 255 caratteri.  
  
 Un tipo usato in una stored procedure è supportata solo con i modelli di costanti. I driver di Database Desktop supportano SQL-92 come criteri di ricerca.  
  
 Utilizzo di una clausola di escape in un predicato LIKE non è supportato.  
  
 Non è necessario eseguire un confronto LIKE su una colonna contenente i dati di un tipo di dati numerici o float. I risultati potrebbero essere imprevedibili. Per ulteriori informazioni, vedere il *manuale del programmatore di Microsoft Jet Database Engine*.


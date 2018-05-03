---
title: Ad esempio limitazioni Predicate | Documenti Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- LIKE predicate limitations [ODBC]
- ODBC SQL grammar, LIKE predicate limitations
ms.assetid: dbd39099-caf6-4c4c-9ad8-f6c63c1bd5e4
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cff5bf10c05a85baeb9ad6f36b620785e8e8bab8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="like-predicate-limitations"></a>Ad esempio limitazioni Predicate
Se i dati in una colonna sono più lungo di 255 caratteri, il confronto LIKE si baserà solo i primi 255 caratteri.  
  
 Un tipo usato in una stored procedure è supportata solo con i modelli di costanti. I driver di Database Desktop supportano SQL-92 come criteri di ricerca.  
  
 Utilizzo di una clausola di escape in un predicato LIKE non è supportato.  
  
 Non è necessario eseguire un confronto LIKE su una colonna contenente i dati di un tipo di dati numerici o float. I risultati potrebbero essere imprevedibili. Per ulteriori informazioni, vedere il *manuale del programmatore di Microsoft Jet Database Engine*.

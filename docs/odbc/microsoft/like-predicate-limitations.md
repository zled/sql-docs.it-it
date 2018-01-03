---
title: Ad esempio limitazioni Predicate | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- LIKE predicate limitations [ODBC]
- ODBC SQL grammar, LIKE predicate limitations
ms.assetid: dbd39099-caf6-4c4c-9ad8-f6c63c1bd5e4
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3ccf71ebc5bedb1f778af8992aae71cea8320603
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="like-predicate-limitations"></a>Ad esempio limitazioni Predicate
Se i dati in una colonna sono più lungo di 255 caratteri, il confronto LIKE si baserà solo i primi 255 caratteri.  
  
 Un tipo usato in una stored procedure è supportata solo con i modelli di costanti. I driver di Database Desktop supportano SQL-92 come criteri di ricerca.  
  
 Utilizzo di una clausola di escape in un predicato LIKE non è supportato.  
  
 Non è necessario eseguire un confronto LIKE su una colonna contenente i dati di un tipo di dati numerici o float. I risultati potrebbero essere imprevedibili. Per ulteriori informazioni, vedere il *manuale del programmatore di Microsoft Jet Database Engine*.

---
title: I nomi di correlazione | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- correlation names [ODBC]
- SQL grammar [ODBC], correlation names
ms.assetid: 76c36c6f-f8e1-4ece-a77b-611dde3bdd8a
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: df00eb9990f7e20240c652c12e7a7b6bd856073f
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="correlation-names"></a>Nomi di correlazione
I nomi di correlazione sono completamente supportati, inclusi all'interno dell'elenco di tabella. Ad esempio, nella stringa seguente, E1 è il nome di correlazione per la tabella Emp denominato:  
  
```  
SELECT * FROM Emp E1   
WHERE E1.LastName = 'Smith'  
```

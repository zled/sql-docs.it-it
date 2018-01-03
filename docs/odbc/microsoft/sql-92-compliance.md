---
title: "SQL-92 conformità | Documenti Microsoft"
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
- Jet-based ODBC drivers [ODBC], SQL-92 compliance
- desktop database drivers [ODBC], SQL-92 compliance
- SQL-92 compliance [ODBC]
- ODBC desktop database drivers [ODBC], SQL-92 compliance
ms.assetid: 50c8c7df-df01-4f4d-ad62-d059cf29d73a
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ad887c4653c98a6fb4cab3df498233e6d196bd8b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sql-92-compliance"></a>Conformità SQL-92
I driver di Database ODBC Desktop e di gestione di Microsoft Jet sottostante non sono compatibili con SQL-92. Supportano molte funzionalità che sono state definite in SQL-92. Alcune funzioni supportate nel driver non sono supportati in SQL-92. Per ulteriori informazioni, vedere il *manuale del programmatore di Microsoft Jet Database Engine*. Di seguito sono le principali differenze tra i due:  
  
-   L'istruzione SQL utilizzata da driver di Database Desktop supporta espressioni più potenti rispetto a quelle specificate da SQL-92.  
  
-   Diverse regole per il predicato BETWEEN.  
  
-   L'istruzione SQL utilizzata dal driver di Database Desktop e ANSI SQL supporta diverse parole chiave.  
  
 Le funzionalità di SQL-92 seguenti non sono supportate da Microsoft Jet SQL:  
  
-   Istruzioni di sicurezza, ad esempio GRANT e blocco.  
  
-   DISTINCT con i riferimenti a funzioni di aggregazione.  
  
 Miglioramenti nel linguaggio SQL utilizzato dal driver di Database Desktop che non sono specificate da SQL-92 sono le seguenti funzionalità:  
  
-   L'istruzione di trasformazione fornendo il supporto per le query a campi incrociati.  
  
-   Altre funzioni di aggregazione (**StDev** e **VarP**).  
  
> [!NOTE]  
>  I driver di Database Desktop supportano la sintassi ANSI standard per % (percentuale) e _ (carattere di sottolineatura), non * (asterisco) e? (punto interrogativo).

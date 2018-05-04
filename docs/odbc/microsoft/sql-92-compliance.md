---
title: SQL-92 conformità | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], SQL-92 compliance
- desktop database drivers [ODBC], SQL-92 compliance
- SQL-92 compliance [ODBC]
- ODBC desktop database drivers [ODBC], SQL-92 compliance
ms.assetid: 50c8c7df-df01-4f4d-ad62-d059cf29d73a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1d6f256f16960332de497e6a861137ca42a0480f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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

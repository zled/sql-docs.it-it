---
title: Driver | Documenti Microsoft
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
- ODBC architecture [ODBC], drivers
- drivers [ODBC]
- drivers [ODBC], about drivers
ms.assetid: d6795d92-877e-44e1-b7d5-2ff2fd3989bd
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2f25be027774c83a31077953eaf51ea8f643bf5e
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="drivers"></a>Driver
*Driver* sono librerie che implementano le funzioni dell'API ODBC. Ognuno è specifico per un determinato DBMS; ad esempio, un driver per Oracle non può accedere direttamente i dati in un DBMS Informix. I driver di espongono le funzionalità del DBMS sottostante; che non sono necessari per implementare funzionalità non supportate dal sistema DBMS. Ad esempio, se il sistema DBMS sottostante non supporta gli operatori outer join, quindi non deve essere il driver. L'eccezione principale è che i driver per DBMS che non dispongono di motori di database autonomo, ad esempio Xbase, devono implementare un motore di database che supporta almeno una quantità minima di SQL.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Attività di driver](../../odbc/reference/driver-tasks.md)  
  
-   [Architettura del driver](../../odbc/reference/driver-architecture.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Driver ODBC fornito da Microsoft](../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)

